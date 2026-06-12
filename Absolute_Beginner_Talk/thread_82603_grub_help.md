---
title: "grub help"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Laz0r on 2005-10-26
Here is my setup:
I have 2 sata drives raided with windows installed
I have a 3rd hard drive, it is ide and has ubuntu badger installed.

Can someone help me add a entry into grub so i can boot windows?

I've looked at:
[http://www.ubuntuguide.org/#addwindowsentrygrubmenu](http://www.ubuntuguide.org/#addwindowsentrygrubmenu)
it says "Assumed that /dev/hda1 is the location of Windows partition" and on my computer the location of the partition is /dev/sda1

also on the disk manager only the first hard drive shows up as having a partition, is this right for a raid?

Thanks for your help.

---

### Post by Breezy Badger on 2005-10-26
unless you have done a lot of customizing go back and install linux again.  If you already have partitions with windows then linux is smart and will detect them and you can load a boot file during linux install (it will give you the option).

Then when you start you have a menu to choose what OS you want.  I have done this, it works.  To make things easier install all other OS, then install linux.

hope this helps

Badger

---

### Post by aysiu on 2005-10-26
[QUOTE=Laz0r]
I've looked at:
[http://www.ubuntuguide.org/#addwindowsentrygrubmenu](http://www.ubuntuguide.org/#addwindowsentrygrubmenu)
it says "Assumed that /dev/hda1 is the location of Windows partition" and on my computer the location of the partition is /dev/sda1[/quote] So change it to be ```
title		Microsoft Windows
root		(sd0,0)
savedefault
makeactive
chainloader	+1
```

[quote=Breezy Badger]unless you have done a lot of customizing go back and install linux again. If you already have partitions with windows then linux is smart and will detect them and you can load a boot file during linux install (it will give you the option).[/quote] I disagree with this. Installing takes a lot of time, even without customization. Instead of reinstalling completely, you can just [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Emerzen on 2005-10-26
There are several ways to skin this cat and reinstalling Ubuntu is one possibility but not necessary.  Do the following:

**sudo gedit /boot/grub/menu.lst**

Add the following lines to the bottom of this file, save and close it:

[B]title		Windows
root		(hd0,0)
makeactive
chainloader	+1[/B]

Grub starts counting at 0, so /dev/sda1 is equivalent to (hd0,0) a=0, b=1 and partition 1=0, partition 2=1, etc...

In any case, reboot and try it.

---

### Post by Emerzen on 2005-10-26
sorry about the double post, aysiu and I must have been writing at the same time.

---

### Post by Breezy Badger on 2005-10-26
> There are several ways to skin this cat and reinstalling Ubuntu is one possibility but not necessary. Do the following:

sudo gedit /boot/grub/menu.lst

Add the following lines to the bottom of this file, save and close it:

title Windows
root (hd0,0)
makeactive
chainloader +1

Grub starts counting at 0, so /dev/sda1 is equivalent to (hd0,0) a=0, b=1 and partition 1=0, partition 2=1, etc...

In any case, reboot and try it.

Yes this is easier than what I told you to do, I should have just told you this.  But if all else fails now you know what I told you for next time

Badger

---

### Post by Laz0r on 2005-10-27
[QUOTE=Emerzen]There are several ways to skin this cat and reinstalling Ubuntu is one possibility but not necessary.  Do the following:

**sudo gedit /boot/grub/menu.lst**

Add the following lines to the bottom of this file, save and close it:

[B]title		Windows
root		(hd0,0)
makeactive
chainloader	+1[/B]

Grub starts counting at 0, so /dev/sda1 is equivalent to (hd0,0) a=0, b=1 and partition 1=0, partition 2=1, etc...

In any case, reboot and try it.[/QUOTE]


I've tried everyones suggestions, this one works the best though. I still get error 13 invalid or unsupported executable format. 
I looked into my bios and noticed the raid i'm trying to boot from wasn't on the boot order, when I added it grub gave me the error "ntldr is missing"

Your help is appreciated, thanks.

---

### Post by aysiu on 2005-10-27
[QUOTE=Laz0r]
I looked into my bios and noticed the raid i'm trying to boot from wasn't on the boot order, when I added it grub gave me the error "ntldr is missing"[/QUOTE] I don't know what that means, but [this](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22ntldr+is+missing%22&btnG=Google+Search) might help.

---

### Post by Emerzen on 2005-10-27
Question:  did you change any BIOS settings before installing Ubuntu?  I had to change some drive settings in my BIOS before installing Ubuntu, Windows wouldn't work w/ the new settings.  So, I reinstalled Windows w/ the new settings, then Ubuntu and it worked fine (I would get the Windows Blue Screen of Death). 

From reading the links that Aysiu posted, it looks like the Windows MBR may be a problem.  You can reinstall just the Windows MBR w/ your windows disk, but then you have to reinstall GRUB (which is pretty simple).  I don't know how to reinstall the Windows MBR but search the forums, I've seen it posted here before.  

Easiest way to reinstall GRUB:

Insert your Ubuntu install disk and reboot.  At prompt type "rescue" and hit enter.  It will ask you which partition you want to mount, mount your primary (root) partition (unless you have a separate boot partition).  Then, at the prompt type

grub-install /dev/sda


Then reboot.  You'll have to re-add the Windows boot line as we've posted above.

---

