---
title: "Ubuntu 10.04 stuck at install on PB G4"
date: 2010-07-14
forum: Apple Hardware Users
---

### Post by alexljz on 2010-07-14
Hi guys, I seem to be stuck on an loading screen of sorts after booting Ubuntu 10.04 from CD (the screen which shows the Ubuntu logo and 5 red/white blinking dots below). Boot options tried were: live, live-powerpc and check-powerpc (which showed no errors in the files)

Hope this is enough information. Thanks :)
Alex

---

### Post by linuxopjemac on 2010-07-14
which Powerbook exactly? link in everymac.com pls.

---

### Post by alexljz on 2010-07-15
should be this: [http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html)

---

### Post by linuxopjemac on 2010-07-15
I have it for you on my website:
[http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx](http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx)

Just do the following (in a tty, CTRL-ALT-F1 for example):
```

wget http://mac.linux.be/files/xorg/powerbook4.txt
sudo mv powerbook4.txt /etc/X11/xorg.conf
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
or reboot

good luck.

---

### Post by npadger on 2011-05-21
I'm having the same problem. I have a M969OLL/A (PowerBook G4 Aluminum 1.5 ghz 12"). I installed 10.04 with no problems, but now I am trying to run a (PPC version of course) live disk of 10.10 so I can remove my Lynx partition to save space. I even left my mac on overnight at the screen with the word Ubuntu and the scrolling dots, but it will not boot. Any way to fix this?

---

