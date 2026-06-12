---
title: "Beryl Installation Trouble"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-21
I'm trying to install Beryl on my laptop, which has Dapper, with [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX")

When I get to the AIGLX section, I start having problems:

It says that linux-dri-modules-2.6.15-27-386 IS not up, and needs to be fixed, so I try to do the work around for it ...

> There's a small glitch with xserver-xorg-air-core: it doesn't install its own modules for input and video drivers. The workaround is to point to the Xorg modules instead:

sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/
sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/


But when I type in the commands I get > ln: target `/usr/lib/xorg-air/modules/' is not a directory: No such file or directory


So... how do I fix this?

---

### Post by kbsuperstar on 2007-01-21
I'm trying to install Beryl on my laptop, which has Dapper, with [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX")

When I get to the AIGLX section, I start having problems:

It says that linux-dri-modules-2.6.15-27-386 IS not up, and needs to be fixed, so I try to do the work around for it ...

> There's a small glitch with xserver-xorg-air-core: it doesn't install its own modules for input and video drivers. The workaround is to point to the Xorg modules instead:

sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/
sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/


But when I type in the commands I get > ln: target `/usr/lib/xorg-air/modules/' is not a directory: No such file or directory


So... how do I fix this?

---

### Post by kbsuperstar on 2007-01-21
bump

---

### Post by kbsuperstar on 2007-01-21
bump

---

### Post by kbsuperstar on 2007-01-21
I'm trying to install Beryl on my laptop, which has Dapper, with [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX")

When I get to the AIGLX section, I start having problems:

It says that linux-dri-modules-2.6.15-27-386 IS not up, and needs to be fixed, so I try to do the work around for it ...

> There's a small glitch with xserver-xorg-air-core: it doesn't install its own modules for input and video drivers. The workaround is to point to the Xorg modules instead:

sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/
sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/


But when I type in the commands I get > ln: target `/usr/lib/xorg-air/modules/' is not a directory: No such file or directory


So... how do I fix this?

---

### Post by kbsuperstar on 2007-01-21
bump bump :( ](*,)

---

### Post by kbsuperstar on 2007-01-21
bbbbbbbbbbbbbbbump :D

---

### Post by kbsuperstar on 2007-01-21
bump bump

---

### Post by aysiu on 2007-01-21
There's no need to create three threads for the same problem. There's also no need to bump your thread every half hour, every ten minutes, or every one minute.

Use one thread for each problem so people aren't duplicating their efforts to help you. Bump a thread once every twenty-four hours.

Thanks.

---

### Post by Old Pink on 2007-01-21
What the hell is your problem? 

People will reply when they can/are ready, stop bumping!

---

### Post by kbsuperstar on 2007-01-21
Sorry, I'm just frustrated with this. I will be patient now.

---

### Post by harrisony on 2007-01-21
i can tell you now that dapper and beryl wont play nicely on there own
 is there any main main reason not to upgrade to edgy (also [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid) and [http://www.ubuntu.com/support/marketplace](http://www.ubuntu.com/support/marketplace)) might be needed if no one can help (try #ubuntu-xgl on irc.freenode.net as well)

---

