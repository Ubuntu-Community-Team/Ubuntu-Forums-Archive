---
title: "automatix install problem"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by augie on 2007-03-20
hi Guys, i'm trying to install automatix the following way:
```
echo "deb http://www.getautomatix.com/apt edgy main" | sudo tee -a /etc/apt/sources.list
```]
```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```
And after that I get:
```
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```
Don't know what is going on and why.
Any suggestions?

ps  I installed automatix some 3 days ago on the same machine and previously installed same edgy and the same method worked out just fine.

ta

augie

---

### Post by overdrank on 2007-03-20
> **augie said:**
> hi Guys, i'm trying to install automatix the following way:
```
echo "deb http://www.getautomatix.com/apt edgy main" | sudo tee -a /etc/apt/sources.list
```]
```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```
And after that I get:
```
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```
Don't know what is going on and why.
Any suggestions?

ps  I installed automatix some 3 days ago on the same machine and previously installed same edgy and the same method worked out just fine.

ta

augie

Hi I cannot update  I believe the site it down for a bit. It did work yesterday. Just wait a bit  good luck!

---

### Post by jenhsun on 2007-03-20
You sure you got that asc key correct?
I think their server is down.

---

### Post by augie on 2007-03-20
no idea what asc keys are :(

could be the server, indeed.

thanks a lot

augie

---

### Post by IndyBob on 2007-03-20
I agree, their server must be down as auto updates keeps telling me I have an update for Automatix2, but it fails to connect to get the download, so I guess we just keep trying.  It is aggravating to keep trying to get an update when it won't work, but since their site was hacked they seem to have several problems getting things back to normal, or so I have read on this and other forums including their own site.  Be patient and all will work out.

IndyBob

---

