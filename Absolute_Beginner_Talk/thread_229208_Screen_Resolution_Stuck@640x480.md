---
title: "Screen Resolution Stuck@640x480"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-08-04
Hi, I've just upgraded from Badger to Dapper Drake. Some pages have the bottom menu out of sight - like 'forward' or 'quit' are out of reach.
If I go to System>Pref:>Screen Resolution. I get a box giving 640x480 and 60Hz. Clicking (L or R) on either of these gives no choices.
I wonder if anyone can help me on this; or point me to a wiki or FAQ on the subject, or even CLI - (I'm a nervous newby). Thanks Sarum.

---

### Post by scxtt on 2006-08-04
you most likely need to specify your monitor's Horiz/Vert refresh rates in /etc/X11/xorg.conf in order to see more resolution options ... like this:
```
Section "Monitor"
       Identifier   "Sceptre X20G"
       HorizSync    31.0 - 80.0
       VertRefresh  56.0 - 65.0
       Option      "DPMS"
EndSection
```but w/ the correct #s for your monitor ...

---

### Post by sarum on 2006-08-05
Thanks for your reply. Just as I was starting to think that I begining to know how to use the CLI; I now have to display my ignorance.
Password:
sudo: /etc/X11/xorg.conf: command not found
joe@Joes-pc:~$ cd /etc/X11/xorg.conf
bash: cd: /etc/X11/xorg.conf: Not a directory
joe@Joes-pc:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
I'm sorry to ask such a basic question, but how do I get into /etc..............
Also, I'd feel more confident if I could back-up this file before altering anything - can that be done.
Thanks for your help, Sarum.

---

### Post by pdub on 2006-08-05
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf/bak

sudo gedit /etc/X11/xorg.conf

---

### Post by confused57 on 2006-08-05
Yes, you can backup the file first:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo gedit xorg.conf
```

then you can change the refresh rates...you might also want to see if the video driver selected is appropriate for your video controller.
If not, it might be easier to change this & screen resolution options using:

```
sudo dpkg-reconfigure xserver-xorg
```

Here's an excellent tutorial for configuring xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
This tutorial was written by forum member, Herman...in fact, his entire site is a good read:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
As well as forum member aysiu's site:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by sarum on 2006-08-07
Thankyou both for your replies. I shall read the link that Confused gave before starting anything, and thanks also for the back-up advice. Cheers Sarum.

---

### Post by damianubuntu on 2006-08-07
Hi,
I've got a similar problem, I've just changed monitors in this box, from a flat LG 17" to an older standard 17" Iiyama.  Now the resolution only shows 1240x1080 with no options. 

Before I go leaping blindly into reconfiguring Xorg, given that only the monitor has changed and not the graphics card or driver, would messing with Xorg be the right thing to do?

---

### Post by steve.horsley on 2006-08-07
Yes it would. Back the file up and read the link as described by confused57. Whoever wrote that web page spent a lot of time on it. 

Then you can either use the **sudo dpkg-reconfigure xserver-xorg** command or manually edit the xorg.conf file.

---

### Post by damianubuntu on 2006-08-07
Cheers Steve, and whoever wrote the web page you referred to, its great.  All working now, though I lost my mouse in the process!  But managed to theen manually edit xorg.conf using the new mouseless conf file and editing it from the backed up one.  As a result I feel a bit more at home with xorg.conf now- so that's good.

---

### Post by steve.horsley on 2006-08-07
Excllent!

---

### Post by sarum on 2006-08-07
Thanks to you all for your help. My screen is now as I want it.
Cheers Sarum.

---

