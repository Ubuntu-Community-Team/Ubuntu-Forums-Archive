---
title: "xserver-xorg-core upgrade"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-04-06
Hi,
I installed the xserver-xorg-core and xserver-xorg-dev upgrades via the automatic updates tool. After doing this on reboot it keeps returning back to the login screen in some kind of loop rather than loading up gnome/beryl as usual. Any ideas what causes this and how to fix it?

Thanks,
Mark

---

### Post by NikoC on 2007-04-06
In my case I re-installed my graphic card's driver (nvidia).

edit: make sure you backup your xorg.conf file first so you can restore it again after re-installing your drivers

---

### Post by Spike-X on 2007-04-06
See my post to the 'Groundhog Day' thread for a solution to this.

---

### Post by luvinit on 2007-04-06
thanks, I did do a search before posting under "xserver-xorg-core" but came up with nothing. Sorry to get you to post everything all over again. These incidents of everything being broken on auto updates are alarmingly common. I keep a backup so I am always ok but some people must find it a nightmare.

---

### Post by luvinit on 2007-04-06
ok i tried the re install the nvidia driver method first because that is the easiest to remember and just involves typing "sudo envy". :)  It works fine. I have scribbled down the other method too for safe keeping. Thanks all.

---

