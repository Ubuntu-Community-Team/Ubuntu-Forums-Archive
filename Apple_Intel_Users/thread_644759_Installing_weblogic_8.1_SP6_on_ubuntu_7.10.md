---
title: "Installing weblogic 8.1 SP6 on ubuntu 7.10"
date: 2007-12-19
forum: Apple Intel Users
---

### Post by ub_newbie on 2007-12-19
All,

I am trying to install WLS 8.1 SP6 on ubuntu 7.10.
I am trying to figure out which OS I should be selecting on the bea site to get the right installer.

Any help is appreciated.

Thanks!!

---

### Post by cyberdork33 on 2007-12-19
Well, I have no idea what options are available, or even what this software is for, but I would choose the Debian option if there is one. Otherwise, there is likely a RedHat option. This will yield a rpm file, which can be converted to a deb file with an app in the repos called alien.

```
sudo aptitude install alien
```

This doesn't mean it will work though, (and in fact, one of the other linux distro versions might work instead), but good luck!

---

### Post by ekravche on 2008-04-17
I'm installing it right now on ubuntu 5.10 non server version. So far it's installing fine without any errors. Get the x86 redhat install. Do

> 
chmod +x net_platform816_linux32.bin


---

### Post by ekravche on 2008-04-17
After the install just run /bea/weblogic81/server/bin$ sudo ./startWLS.sh

make sure to **sudo**

---

