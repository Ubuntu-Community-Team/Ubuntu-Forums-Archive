---
title: "Problems during installation."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by amar2d4 on 2007-02-02
Initially when trying to boot from Cd after selecting language as english my screen gets frozen.

I try starting ZUbuntu in safe graphics mode.It gets frozen again in when trying to detect my SATA drive.
 I get the following material from the forum,
---------------------------------------------------------------------------------------------------------
At last, I can install Ubuntu in my PC and make it dual boot.
Thanx a lot guys, for helping me out. Very much appreciate

Let me explain what I did
1st I try put acpi=force irqpoll parameter at the end of the line like mr.wizrd told me.
But nothing happen still Ubuntu can't detect my SATA drive

Then I read thread [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230) that mr.wizrd gave me and wallaa. I figure out that it work when I put the acpi=force irqpoll parameter in between 2nd and 3rd parameter of the line. After that both of my SATA drive appear.

I'm very happy with it.
Thanx again, if not maybe I'm not one of the Ubuntu user
--------------------------------------------------------------------------------------------------------

Now i get into command line mode,but, not into X-windows mode.

When trying to look for errors.

It says X-window system version 7.0.0.

X protocol version 11, revision 0, and release 7.0


I get a box which says start when configured properly and back to commandline mode.


The machine is a GX520 ,533MZ celeron,256 MB RAM,30 Gb HDD machine contributed by my company towards my Lab work.

---

### Post by x64Jimbo on 2007-02-02
Try this:
sudo dpkg-reconfigure xserver-xorg

---

