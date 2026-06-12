---
title: "Installing firefox"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-11-10
I am using Kubuntu 6.06
I want to install firefox 2.0

when i go to adept manager it shows me

firefox 
install size 22m
candidate version 1.5.dfsg etc

and 
mozilla firefox
104k

which one is the actual firefox
and is this the version 2 the latest version??

---

### Post by taurus on 2006-11-10
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by timetunnel on 2006-11-10
> firefox
install size 22m
candidate version 1.5.dfsg etc

No, it's not 2.0, it's version 1.5. That's why its name contains the "1.5" ;)  It's the "real" package of Firefox, whereas

> mozilla firefox
104k

is a meta package. That means: it contains nothing at all, only a dependency to another package. That's the reason why it is so small. If you choose a metapackage for installation, it selects the dependent ones as well for installation. Here is a short description of some meta packages and their purpose: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

If you really want Firefox 2.0, follow the instructions in the post above.

---

