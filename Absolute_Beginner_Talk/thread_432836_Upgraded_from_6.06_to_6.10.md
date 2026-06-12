---
title: "Upgraded from 6.06 to 6.10"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by rrkano on 2007-05-04
I upgraded exepecting a GUI interface, but when I  rebooted, I get the command line just like before. Did I do something wrong? Or is there another package to install to give my Ubuntu Server a GUI Interface. 

Thanks

---

### Post by Outrunner on 2007-05-04
What exactly did you install and/or upgrade? I don't understand...

Anyway since this is a server install you'll need X

sudo aptitude install xserver-xorg-core

---

### Post by lazyart on 2007-05-04
Server defaults to commandline.  While some argue that commandline is the only way to run a server (saves utilization for the real work it has to do) you can log into the terminal and type:

sudo apt-get install ubuntu-desktop

And you will be all gui.

---

### Post by rrkano on 2007-05-04
Thanks for your help. That did it. I appreciate it!

---

