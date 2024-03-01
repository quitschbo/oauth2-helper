
This is an adapted version of [\[1\]](https://github.com/billauer/oauth2-helper) to use with office356. For more information about this script, see [\[2\]](http://billauer.co.il/blog/2022/10/git-send-email-with-oauth2-gmail/).

\[1\] [https://github.com/billauer/oauth2-helper](https://github.com/billauer/oauth2-helper) \
\[2\] [http://billauer.co.il/blog/2022/10/git-send-email-with-oauth2-gmail/](http://billauer.co.il/blog/2022/10/git-send-email-with-oauth2-gmail/)


## Quick install in debian/Ubuntu

### Install msmtp and oauth2-helper

```
sudo apt-get install msmtp
wget https://github.com/quitschbo/oauth2-helper/raw/main/oauth2-helper.pl -O ~/bin/oauth2-helper.pl
chmod u+x ~/bin/oauth2-helper.pl
```
### Configure msmtp 
Edit `~/.msmtprc`

```
account default
host outlook.office365.com
port 587
tls on
tls_starttls on
auth xoauth2
user <your email>
passwordeval ~/bin/oauth2-helper.pl
from <your email>
```

Copy access oauth2_reftoken

1. In Thunderbird go to: \
 `Preferences > Privacy & Security > Passwords`
2. Click on `Saved Passwords...`
3. Look for provider `oauth://login.microsoftonline.com (...)`
4. Right-click on provider and choose `Copy Password`
5. Past text in `~/.oauth2_reftoken`
6. `chmod 600 ~/.oauth2_reftoken`

### Configure git
Edit `~/.gitconfig` 
```
[sendemail]
	smtpserver = /usr/bin/msmtp
```
	
