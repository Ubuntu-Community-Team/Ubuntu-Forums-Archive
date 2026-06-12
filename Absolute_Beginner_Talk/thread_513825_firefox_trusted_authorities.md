---
title: "firefox trusted authorities"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by kenbaldwin on 2007-07-30
I managed to mess up my Firefox by trying to install a Rhapsody plugin. I did a remove --purge, then reinstalled, and it's working fine now, except that I get an "unrecognized certificate authority" warning everywhere I go. 

Poking around, I see
/etc/ca-certificates.conf
/etc/ssl

Do I need I to do something to get Firefox to reload all the cert files? Thanks

Ken

---

### Post by PaulFr on 2007-07-31
I would suggest you create a new profile first```
firefox -ProfileManager

``` and then check in Edit -> Preferences -> Advanced Tab -> Encryption Tab -> View Certificates button -> Authorities tab whether there are any authorities listed there. If there are none, I would suggest you install```
sudo apt-get install ca-certificates
```.

---

