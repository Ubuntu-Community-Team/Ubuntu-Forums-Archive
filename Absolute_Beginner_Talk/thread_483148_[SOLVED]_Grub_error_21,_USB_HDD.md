---
title: "[SOLVED] Grub error 21, USB HDD"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-06-24
Hi

I've searched the forums for help, but I couldn't find anything that matched this issue in particular:

I've recently installed Feisty on a [COLOR="Red"]partitioned USB HDD[/COLOR], with XP on my internal HDD.
When I start up my PC with the USB drive [COLOR="Red"]turned off[/COLOR], I get Grub error 21 - Grub can't locate my drive.
Nothing weird about that, really, since the drive is turned off, but I've got a laptop, so I don't want to be carrying my USB drive around with me all the time, and I don't want to loose XP completely. I can't just format and partition my internal HD to allow Feisty to install there, because [COLOR="Red"]XP came preinstalled on my PC[/COLOR] in one, big partition (except for Dell's recovery partitions), and I have never gotten an XP install CD.

So I guess my question is: Can I make Grub run from my internal HD (in XP?) without affecting the internal HD install of XP?
Or is there another way to simply boot XP when my USB drive is not plugged in?
All I really need is to be able to run either Feisty or XP when I've got my USB drive plugged in and just XP when I don't.

I don't know if this holds any relevance at all, but I run a Dell Inspiron 6400, and has been through a lot of fiddling with stuff I hardly understand because of my ATI x1400 card. That is all solved now, and I don't think I messed anything up since I don't experience problems besides this one.

Any help is appreciated.

Oliver

---

### Post by BobCFC on 2007-06-24
Grub is complaining because it can't find it's own config files which are in the /boot/grub directory.

One way around this is to shrink your windows partition a tiny bit and make special boot partition on the internal drive... 64mb should be enough.  Then when you install Ubuntu and choose swap partitions etc tell it to use this small partition as /boot and put the rest / on the usb drive.

You'll probably be able to reinstall grub without redoing the whole Ubuntu but others will have to help you there.


If you're having trouble shrinking windows unmount it and use gparted which is like a free partition magic.   There is also a [gparted liveCD]("http://gparted.sourceforge.net/livecd.php") which is only a 50mb iso that makes the job easy and can be used as a rescue cd

---

### Post by MVP on 2007-06-24
You should install GRUB on the USB Drive. That way you can boot Windows normally when the USB Drive is not plugged in.

---

### Post by BobCFC on 2007-06-24
That's clever.   I suppose if you tell the bios to boot usb first that should work

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> Hi

I've searched the forums for help, but I couldn't find anything that matched this issue in particular:

I've recently installed Feisty on a [COLOR="Red"]partitioned USB HDD[/COLOR], with XP on my internal HDD.
When I start up my PC with the USB drive [COLOR="Red"]turned off[/COLOR], I get Grub error 21 - Grub can't locate my drive.
Nothing weird about that, really, since the drive is turned off, but I've got a laptop, so I don't want to be carrying my USB drive around with me all the time, and I don't want to loose XP completely. I can't just format and partition my internal HD to allow Feisty to install there, because [COLOR="Red"]XP came preinstalled on my PC[/COLOR] in one, big partition (except for Dell's recovery partitions), and I have never gotten an XP install CD.

So I guess my question is: Can I make Grub run from my internal HD (in XP?) without affecting the internal HD install of XP?
Or is there another way to simply boot XP when my USB drive is not plugged in?
All I really need is to be able to run either Feisty or XP when I've got my USB drive plugged in and just XP when I don't.

I don't know if this holds any relevance at all, but I run a Dell Inspiron 6400, and has been through a lot of fiddling with stuff I hardly understand because of my ATI x1400 card. That is all solved now, and I don't think I messed anything up since I don't experience problems besides this one.

Any help is appreciated.

Oliver
What has happened is that grub's IPL was installed to your internal drive's mbr...you could download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
there are instructions for restoring your Window's IPL to the internal hard drive's mbr in the link.

You'll need to install grub to the external hard drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in the thread, but after opening a terminal, basically you would:
```
sudo grub
find /boot/grub/stage1
root (hd1,x)
setup (hd1)
quit
```

Then if your bios is capable of booting first to the external hard drive, you should get a grub boot menu...highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary, but can be made permanent if it works.

If your bios is not capable of booting first to USB, you can always use SGD to boot your external drive.

---

### Post by OliverN on 2007-06-24
Thanks for replies :p

I'll look into it and get back.

---

### Post by OliverN on 2007-06-24
I need a little more help in restoring Windows' IPL to the internal hard drive's mbr. 

There's a dead link in the instructions, and I don't fully understand.

I think I've got the rest covered.

---

### Post by BobCFC on 2007-06-24
If you have the XP cd you can use the recovery console to restore the MBR.  Boot it up to blue as if you were installing windows and at the welcome screen press R to repair.   

Once at the recovery console use the command FIXMBR to restore the master boot record.  This will remove grub and just boot the ntbootloader off the C: drive.

---

### Post by OliverN on 2007-06-24
XP came preinstalled on my PC, and I have never gotten an installation Cd :(

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> I need a little more help in restoring Windows' IPL to the internal hard drive's mbr. 

There's a dead link in the instructions, and I don't fully understand.

I think I've got the rest covered.
If you're using SGD:

>    1.  boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super GRUB Disk
   3.  Windows
   4. Fix Boot of Windows

---

### Post by OliverN on 2007-06-24
Almost there, but when I try to boot from my USB drive now it says NLTDR missing, and no grub menu.
Have I done something wrong?

---

### Post by OliverN on 2007-06-24
That's NTLDR, sorry.

Another thing: When I boot from the live cd I now have two USB HD desktop icons by default.

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> Almost there, but when I try to boot from my USB drive now it says NLTDR missing, and no grub menu.
Have I done something wrong?

Does Windows boot when your external hard drive is disconnected?

---

### Post by OliverN on 2007-06-24
yes, if I set the internal HD to be the first boot option in BIOS (or if I simply call up the boot menu during start-up and select it).

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> yes, if I set the internal HD to be the first boot option in BIOS (or if I simply call up the boot menu during start-up and select it).
That's good, so SGD was able to restore Window's IPL to the internal hard drive's mbr.

The next thing you need to do is install grub to the external hard drive's mbr, when you booted the live cd, opened a terminal(Applications---Accessories---Terminal), and entered:
```
sudo grub
find /boot/grub/stage1
```
was the output something like "root (hd1,0)", if it was then to install grub to your external drive's mbr, enter:
```
root (hd1,0)
setup (hd1)
quit
```

substitute "root (hd1,0)" for whatever the results of "find /boot/grub/stage1" showed.

Then try to boot first to your external hard drive, see my first reply for editing the Ubuntu root entry in order to get your external hard drive to boot.

Added:  Don't know if you've tried the above yet, but you might want to set your internal hard drive to boot before your external hard drive... before you try installing grub to the USB drive's mbr.  Shouldn't make a difference, but wouldn't hurt to do so.

---

### Post by OliverN on 2007-06-24
Alright, so I did everything you said, and Ubuntu booted correctly!
So... If I reboot now, are things supposed to be working, or is there more?

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> Alright, so I did everything you said, and Ubuntu booted correctly!
So... If I reboot now, are things supposed to be working, or is there more?

You'll need to make the changes permanent in your menu.lst...this is under the assumption that you're booting first to your external hard drive and was able to boot into Ubuntu by pressing "e" and changing root to (hd0,x)...open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

then change your root entries to (hd0,x), the x meaning leave this entry "as is"...also, find the line that begins with #groot, change the root to (hd0,x)

quit & save...
This should make your changes permanent to be able to boot Ubuntu by booting first to your external hard drive.

You could also add an entry to boot Windows from grub, something like this:
```
title  Windows XP
root  (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1
```
add the entry to the very end of your menu.lst.

If Windows is on the second partition, then root would be (hd1,1)...your current Window's entry should indicate this.

---

### Post by OliverN on 2007-06-24
You assume correctly, and everything is now booting just like it should. Thank you so very much for your help and patience!:p

---

### Post by confused57 on 2007-06-24
> **OliverN said:**
> You assume correctly, and everything is now booting just like it should. Thank you so very much for your help and patience!:p
Glad to help & everything is working OK.

---

