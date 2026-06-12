---
title: "Dual Boot - 2 hard Drives"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-02-09
Hi All:
This is my first post.  I was trying to install Ubuntu 5.04 onto a second hard drive (slave) hdb?
XP pro is already on the primary drive, hda?  Now, I was told to install Grub onto hdb, and set my bios to boot the slave drive, which I can do - at least I saw the option there and picked it.     I was told to install Grub this way because if I ever "had to run windows defrag on the primary drive I would fry the mbr and would not be able to boot linux".  Not sure if it is true or not, but...being a total noob, I tried it.

So I got 5.04 installed, but when rebooting instead of being presented with the Grub menu, I got a message saying unable to read disk format type - or something like that. (It's been awhile.  In recently searching around, I have ran across some help articles which suggest that I probably had Grub trying to read the XP disk somehow???  Other articles say to install Grub onto the XP disk, and then modify some coding in the boot.ini file??

I am totally new to Linux, but want to jump onto the bandwagon now, as I'm not buying into the Vista stuff.  No way!

So, my computer has 2 hard drives, both 20GB, which is why I want to keep the OS on different drives.

What is the easiest way to do this with Ubuntu?

Thanks for reading this rather long 1st post!

Ziffnabb

---

### Post by Lowtech on 2007-02-09
Check out the link to the thread below, it really helped me.  It ought to be stickied IMO.

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by ieee488 on 2007-02-10
ziffnabb,

If you can, you should be installing Ubuntu 6.06 instead of 5.04.

I have the CDs for 5.10 and 6.06 both of them newer than 5.04.
6.06 is an improvement from even 5.10.

---

### Post by ziffnabb on 2007-02-11
I now have 6.06 downloaded and burned.  Ok guys, let me see if I understand this correctly.  I have xp installed as master, and it will be hda.  I will install Ubuntu on an empty 20GB drive on slave, which is hdb.  I tell Ubuntu to install Grub in hdb.

Now, I open up my box and make xp slave, and Ubuntu master.

Then I edit using terminal the /boot/grub/menu.lst file by adding:

title Windows XP
map (hd0,0) (hd1,0)
map (hp1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Save and reboot.

Did I get it right?

Ziffnabb

---

### Post by ieee488 on 2007-02-11
It sounds like you are trying to do it the nontraditional way.
Others seems to report more difficulty with it.

I also have Ubuntu on a 2nd HD.
I just installed GRUB in MBR and was done with it.

---

### Post by confused57 on 2007-02-11
> **ziffnabb said:**
> I now have 6.06 downloaded and burned.  Ok guys, let me see if I understand this correctly.  I have xp installed as master, and it will be hda.  I will install Ubuntu on an empty 20GB drive on slave, which is hdb.  I tell Ubuntu to install Grub in hdb.

Now, I open up my box and make xp slave, and Ubuntu master.

Then I edit using terminal the /boot/grub/menu.lst file by adding:

title Windows XP
map (hd0,0) (hd1,0)
map (hp1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Save and reboot.

Did I get it right?

Ziffnabb

If you followed the link Lowtech gave you, during install you'd want to connect your Ubuntu drive on the master connector so that it is hda(disconnect your Windows drive, if you want to be sure), & set your Ubuntu hard drive jumper to master or cable select.  Once you get Ubuntu up & running, add the entry to grub to boot Windows...then reconnect your Windows drive as slave(again, check jumper settings)...see the Windows entry in the link.

---

