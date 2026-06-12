---
title: "First timer"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by idarastar on 2007-07-14
So what do I need to do to get either OS working? I'm currently stuck in the middle of Ubuntu and WinXP, kinda...Help please.

My mom just bought this used laptop with Ubuntu installed on it. This is the first time ever seeing it. I understood how to navigate alright. Because she wasn't able to have normal yahoo messenger because she wants the webcam, she asked me to load up her windows xp to the laptop even after i explained Gaiam would be fine-no webcam.
Following the directions on microsoft.com, I found fdisk to delete /dev/hfa (i think). I followed the steps from microsoft's website and of course, I messed it all up.
The CD-ROM will not automatcally boot up (even after changing the boot in BIOS). I just get the GRUB 1.5 Loading, then GRUB Error 22.
After all this confusion, my mom said she can used yahoo without a webcam.

---

### Post by kevinlyfellow on 2007-07-15
Thats tough, personally, since you don't seem beyond install operating systems, I suggest just installing windows and then installing linux again.  You can try to restore grub
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by HereInOz on 2007-07-15
Be aware that XP will often refuse to install on an already formatted EXT3 partition.  You will possibly have to use GParted (available on sourceforge) to repartition the HDD, or at least fire up an old Windows 98 startup disk, and fdisk the HDD setting up new partitions, then run fdisk /mbr which should remove the old grub bootloader. 

Then install XP, then install Ubuntu.

---

### Post by idarastar on 2007-07-15
Thanks for the replies.
I'm currently using my desktop and need suggestion to get such file over to this troublesome laptop since the only windows i have is xp on a cd-rom which will not load at all. 
This desktop doesn't have burning capabilites.

---

### Post by candtalan on 2007-07-15
> **idarastar said:**
> Thanks for the replies.
I'm currently using my desktop and need suggestion to get such file over to this troublesome laptop since the only windows i have is xp on a cd-rom which will not load at all. 
This desktop doesn't have burning capabilites.

If possible, you need to be able to boot from the cd drive in the laptop. If the windows cd does not boot, perhaps try a live cd of ubuntu or another linux distribution of recent version.
If you find that nothing boots, even though you have changed settings in the bios, then it is rather strange, and may be a problem. There may be ways to install without a cd drive booting but thy are unusual I suspect.

---

### Post by idarastar on 2007-07-15
And to confirm I'm configuring the BIOS right....I would only change the #1 boot to cd/dvd drive?
Would I need to change the IDE Adapter 0 Master or 1 Master on the Main screen also to CD/DVD drive, or leave it with Auto-detects device so it will automatically get to the hard disk drive?
In other words, I'm not entirely sure abou the IDE Adapter part..

---

### Post by candtalan on 2007-07-16
> **idarastar said:**
> And to confirm I'm configuring the BIOS right....I would only change the #1 boot to cd/dvd drive?
Would I need to change the IDE Adapter 0 Master or 1 Master on the Main screen also to CD/DVD drive, or leave it with Auto-detects device so it will automatically get to the hard disk drive?
In other words, I'm not entirely sure abou the IDE Adapter part..

I believe you only need to change the #1 boot item to be cd/dvd drive yes. I do not think any other changes are needed at all. I have only ever changed stuff to get the #1 boot to be cd drive.

---

