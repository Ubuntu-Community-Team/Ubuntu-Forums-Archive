---
title: "Dual Boot Issue"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by jaybirdUK on 2008-02-03
Ok, so this is my first ever post here, & I am a complete novice to Linux so please bear with me.  I installed Ubunto just yesterday after testing it on the cd & I have to say I find it quite pleasing.  

So this is my problem, I have to keep Windows as my main OS simply because I use a lot of audio editing & production software that Linux simply can't handle yet, but for general use I'd like a change from Windows.

I installed Ubunto onto a drive all of it's own, & as far as I can tell, everything is successful, it boots & loads just fine BUT..... I have too disconnect the drive with Windows on, the dual boot screen doesn't show up at all it just boots straight into Windows, yet upon disconnecting the drive I get a screen with the dual boot options?

So I guess the issue here is, how do I get this dual boot screen to come up with both drives connected?

Regards
Jay

---

### Post by rob1101 on 2008-02-03
wait im confused. 

if both drives are connected you can't see the boot screen.
if just windows dive is in you can't see boot screen.
if just ubuntu drive is in you can see boot screen.

is that right?

---

### Post by iansane on 2008-02-03
Not sure if this is part of the issue but I have two seperate drives and had to change the jumpers to make hda (windows drive) the master, and hdb (ubuntu) the slave. Just a thought from another newbie.

---

### Post by jaybirdUK on 2008-02-03
When the Windows drive is connected I get no dual boot screen, it just boots straight into Windows, if I disconnect this drive so I have just the Ubunto drive connected then I get the boot options, which is useless as the Windows is obviously not connected.

---

### Post by rob1101 on 2008-02-03
so what happens when both drives are connected? and did you try iansane's solution?

---

### Post by jaybirdUK on 2008-02-03
> **rob1101 said:**
> so what happens when both drives are connected? and did you try iansane's solution?

When both drives are connected I get no dual boot options at all, it boots straight into Windows.  I'll give Ian's suggestion a shot though :)

---

### Post by Aurora@FleetBuzz on 2008-02-03
> **iansane said:**
> Not sure if this is part of the issue but I have two seperate drives and had to change the jumpers to make hda (windows drive) the master, and hdb (ubuntu) the slave. Just a thought from another newbie.

I dual boot XP and Ubuntu on separate HD's.  I made the windows drive the slave and Ubuntu the master.  Works like a charm.  Here's some references.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

---

### Post by jaybirdUK on 2008-02-03
> **Aurora@FleetBuzz said:**
> I dual boot XP and Ubuntu on separate HD's.  I made the windows drive the slave and Ubuntu the master.  Works like a charm.  Here's some references.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

My Windows is on a Sata Drive & the Ubunto is on an IDE drive, I'm thinking this is possibly the issue, the links mention this so I have some research to do.... :confused:

---

### Post by Aurora@FleetBuzz on 2008-02-03
You've probably checked out the link to this thread by now:
[http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

I would follow the advice by Mingus on that thread:> [QUOTE]
[**Re: Dual Boot with SATA and IDE, Need Help!!**
Quote:
Originally Posted by snapmando
Install Win XP on the SATA drive and install Ubuntu 64Bit on the IDE Drive.

Can someone give me instructions on how I could do this, Please!!

Are there any issue's with this distro and SATA drives?

I would like to accomplish this on a Dual-Boot.
1. Set BIOS to boot from SATA
2. Install XP on SATA
3. Boot from Ubuntu install CD, follow directions and at partition menu, use "guided partitioning" on the IDE drive (hda) or use "manual" to control more closely how the partitions are done
4. At the boot loader menu, do *NOT* take the default. Instead instruct the installer to put grub on the Master Boot Record of the IDE drive (/dev/hda) - *NOT* on the SATA drive (sda)
5. Ubuntu will finish phase one of install and ask you to reboot. *Immediately* enter BIOS setup and change sequence to boot from IDE drive. Let Ubuntu finish installation. If you do not yet have your network connection set up, be sure to tell installer to get packages from CD only
6. In Ubuntu go to Applications/System Tools/Terminal. You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

7. save the file
8. reboot and test boot into XP[/QUOTE]

---

### Post by jaybirdUK on 2008-02-03
There's just one issue with the method just posted, i can't see the IDE in the boot menu in the Bios.  This may cause issues, hmmmmm lol

---

### Post by Aurora@FleetBuzz on 2008-02-03
Yes, in that case I would proceed with caution.  I see where others on that thread I referenced had the same issue.  I'll look around and see if I can find a fix.  Hopefully, some vastly more experienced users will chime in.  Sorry I couldn't have been more helpful.

---

### Post by jaybirdUK on 2008-02-03
> **Aurora@FleetBuzz said:**
> Yes, in that case I would proceed with caution.  I see where others on that thread I referenced had the same issue.  I'll look around and see if I can find a fix.  Hopefully, some vastly more experienced users will chime in.  Sorry I couldn't have been more helpful.

No need to apologize, I appreciate the help but these issues need resolving as it is probably one of the reasons more people aren't willing to switch over.  Windows offers simple plug n play in most cases & they expect the same for Linux.  For the time being I'm happy to manually disconnect the relative drive to use either, but I will persevere to try & resolve this :)

---

