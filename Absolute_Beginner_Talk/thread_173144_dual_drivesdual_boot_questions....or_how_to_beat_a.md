---
title: "dual drives/dual boot questions....or how to beat a dead horse"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-09
Ok, I've read about a million (ok, maybe a hundred) posts on this topic, but I hoping some of you can verify what I think I know.

First, the specs.
Dell Dimension 8200 1.8 Ghz
1.2G RAM
A01 BIOS
nVidia Something or another (5500 me thinks)

Anyway, Live CD works great. I haven't tested everything, but sound and video are perfect. Internet is fast, etc etc I (I can supply more tech info if needed). XP is on master 250G drive, slave is an 80G that so far only has the backup file from the master.  I want to put Ubuntu on the second drive (I know, I know, it's better on the primary).  I absolutely cannot accidently format the wrong drive. I could spend a week or more  backing over 40G worth of files just in case. If that's what has to happen, so be it. Of course, I would rather not.

Questions:
During install, it will ask me where to install. Different posts say different things, such as the master is hd1 and slave is hd2, or master is hd0 and slave is hd1. How do I know which of these is correct?
How will I know when and where to install GRUB (I know it has to be on the master with Windows).
If I go crazy and want to take Ubuntu off, how hard is it to fix the MBR, and how risky is this?
Should I wait 2 weeks for Dapper? What's better about Dapper?

---

### Post by PhoenixP3K on 2006-05-09
Well... I'll go from bottom up. If you remove Ubuntu you can use Windows XP Install CD to restore the MBR to make Windows boot as usual. Now I'm sure sure how important is having Ubuntu on the Master but that what I did from the start. I doesn't matter to Windows if it's moved to slave. But you should bother about hd0/hd1/hd2 thing since your drives are different sizes. You can easily tell witch is witch this way. No matter the type of install you make GRUB will go and put itself before Windows XP boot sequence. It automaticaly detects Windows XP and adds it to the boot menu. You can easily change the default booting system after you've completed Ubuntu's installation process. Now one thing is certain, I love the new visual install of Dapper, it really brings the tension down... But waiting 3 weeks for Dapper might do. But it doesn't really matter because you can upgrade when it comes out ( I think, since you can upgrade from Breezy... not sure).

---

### Post by bt224 on 2006-05-09
I haven't really heard any straight answers on how the Breezy set up will transfer with the upgrade. I'd rather not go through getting it just right, then have to do it again a few days later. But if Dapper is no great leap, I may not worry about it. I ran ME for over a year after I got my free XP install disk from Dell. The only reason I upgraded was to get a joystick to work. Newer isn't always better, sometimes it's just newer.

---

### Post by aysiu on 2006-05-09
My advice? It's a rather conservative approach, but I would say you should play with the live CD for another three weeks.

Really get to know Ubuntu well without harming your computer. Read a lot. Try out things (after all--it's a live CD... it won't harm anything unless you mount your Windows drive). Play around with the command-line. You can even "install" software (it won't be there when you reboot).

After three weeks of using the live CD, I think you'll be more than ready to install Dapper and not accidentally erase any partitions.

Some suggested reading in the meantime:
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by bt224 on 2006-05-09
Good advice. I've had it on my old laptop exclusively for a couple of weeks now. Play time is limited since it actually has to sit on the wife's desk since my $9 Linksys card hasn't arrived yet. :) I'm using the Live right now on my desktop and loving it. I did some installs and upgrades (aysiu, you were a HUGE help through most of it). Still a big n00b, but getting comfortable with the system.

---

### Post by bt224 on 2006-05-09
So this looks good to go?

---

### Post by aysiu on 2006-05-09
Dapper is a great leap, but--theoretically at least--it's supposed to keep your settings and such. The upgrade worked for me. Some others have not been as lucky. A clean install is almost always better.

---

### Post by bt224 on 2006-05-09
Thanks, aysiu. I think I'll wait.

What did you like best about Dapper over Breezy?

---

### Post by aysiu on 2006-05-09
[QUOTE=bt224]
What did you like best about Dapper over Breezy?[/QUOTE] Honestly, not a whole lot that affects me.

There are some improvements, though, mainly to the GUI (graphical user interface). For example, Xubuntu has much more polish, and it also has a cute splash screen with a mouse running inside the Ubuntu logo (the old Breezy splash screen was just a dead mouse flashing in and out). Gnome's default theme is glassy and orange instead of flat and brown.

There's now a graphical frontend to *deborphan* called *gtkorphan*. The Espresso Installer is all point-and-click instead of a text-based graphical installer.

Dapper feels faster in general--in both KDE and Gnome.

It also has some more software available: for example, KFTPGrabber wasn't in Breezy, but it's now in Dapper.

I can't list out everything, but things are generally more up-to-date. I've found AmaroK to be more stable in Dapper than in Breezy.

---

### Post by uzi09 on 2006-05-09
personally for me, i find dapper relatively stable. sure you'll come across the occasional glitch, but if you've dealt with windows, this shouldn't be too big of a deal :twisted: 


i personally LOVED the hardware support. my machine wouldn't run breezy, so it was dapper, or another distro (i don't think the latter is happnin any time soon --  go ubuntu!)

---

### Post by bt224 on 2006-05-09
yep. I'm waitin'. Thanks folks!

---

