---
title: "Need help urgent!"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-11-28
I have a dual boot setup with Vista. When I click on Ubuntu 7.10 in GRUB, the screen goes black, no splash and my caps lock on the keyboard flashes

I have an Acer Aspire 5100 and I have many important documents on it!

---

### Post by jken146 on 2007-11-28
Hi there,
Don't worry!  I'll bet your problem can be fixed and besides, whatever data you've got can easily be recovered by booting into Windows or even into a live CD.

Try to boot into recovery mode.  Ubuntu should boot with loads of text output.  If you see any error messages please post them here so we can figure out what's going wrong.

---

### Post by gubemton on 2007-11-28
When I get a chance to, I will, Im on the Vista partition now but cannot see what is on the Ubunutu one, hopefully someone can help

I was reading that caps lock flashing means kernal panic ( thank you google)

---

### Post by jken146 on 2007-11-28
Yes, that's what I guessed it would be (I had a kernel panic problem recently).  Here are the threads that sorted me out: [http://ubuntuforums.org/showthread.php?t=620860](http://ubuntuforums.org/showthread.php?t=620860), [http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002)

As for accessing your ext3 partition(s) in Windows, try the  driver here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by gubemton on 2007-11-28
I used this [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Speed-up_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Speed-up_Ubuntu) and this [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen). Those were the last things I did in Ubuntu before it started doing it.

---

### Post by jken146 on 2007-11-28
OK, try the fixes in the threads I gave you, but it's probably best to go into recovery mode and take a look at the errors first.

---

### Post by gubemton on 2007-11-28
Bump

I went into recovery and this is the error I get

Kernal panic-not syncing:VFS:Unable to mount root fs on unknown-block (0,0)

BTW, I did change the order of the harddrive in BIOS from 2nd to 1st. Previously it was boot from CD(if there was one) and then hard drive.

---

### Post by gubemton on 2007-11-28
I hate to double post, but I beleive I have the same error you had. I will try it out when I can have access to my other computer.

---

### Post by skyjacker on 2007-11-28
> **jken146 said:**
> Yes, that's what I guessed it would be (I had a kernel panic problem recently).  Here are the threads that sorted me out: [http://ubuntuforums.org/showthread.php?t=620860](http://ubuntuforums.org/showthread.php?t=620860), [http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002)

As for accessing your ext3 partition(s) in Windows, try the  driver here: [http://www.fs-driver.org/](http://www.fs-driver.org/) Havve you used this driver, and if so how stable is it? Does it cause problems with windows or Ubuntu software?

---

### Post by gubemton on 2007-11-28
I think I may know the issue

vga=792

I added that to my boot aswell and it seems that you had that issue aswell jken

Lemme try and remove it and go from there, but how would I go about doing that? Load from CD and change the boot file, but how do I do that?

---

### Post by bollix47 on 2007-11-28
No need to load from the live CD.

Just press e on the Ubuntu entry in grub and remove the wrong info.

---

### Post by gubemton on 2007-11-28
I tried removing splash, quiet and vga=792 and still gives me that error.

Not even Windows has ever given me this much trouble...sigh...

---

### Post by bollix47 on 2007-11-28
Try the e in grub again and this time look at the root line.

root        (hd?,?)

What are the numbers where my question marks are?

Since you have Vista it's probably on (hd0,0) so linux might be on (hd0,1) or higher if you have another partition in between.

---

### Post by Luigi239 on 2007-11-28
Before you do anything else, now is the time to back up all of your documents by booting into the Ubuntu Live CD, accessing your Ubuntu partition, and then copying the files onto your Vista partition, or even better, an external drive or CD/DVD.

---

### Post by gubemton on 2007-11-28
Can Ubuntu write into NTFS anyway? I don't think it can. Check jken's post on his problem and help me make some sense of it...

---

### Post by cjm5229 on 2007-11-28
If you install that FS Driver  that jken mentioned you can just boot onto Windows and copy your files from Ubuntu. When you do that, If you decide to reinstall Ubuntu be sure to create a separate /home Partition, so that if you ever need to reinstall all you have to do is install to root and your files will still be there.

---

### Post by Arthur Archnix on 2007-11-28
> Not even Windows has ever given me this much trouble...sigh... 
Chances are good that because Windows doesn't let you change its splash screen or resolution by tinkering with the innards of it. As the saying goes, the great thing about Linux is that if you break it you get to keep both pieces. Or something. 

Anyway, sounds like you've done a lot of customizing, the splash screen, resolution, you mentioned something about changing HD boot order in the bios. It's going to be hard to narrow it down without more info. I see you've given the kernel panic message already. Boot a live cd, and mount the root partition if it's not already mounted on your desktop. The output of these should help:
```
cat /etc/fstab       <= This will show us how grub tries to load your hard-disks.
fdisk -l      <= This will show us what your disks and partitions look like.
```
The last is your grub menu.lst. If you just go to /boot/grub/menu.lst you'll see the one on the cd. We want the one on your HD. Look in /mnt or /media for your hd's filesystem. If you find it there just browse to /boot/grub/menu.lst, copy down what's in that file. Once you know the location (say for instance its mounted under media) you can print the output in a terminal using:
```
cat /media/sda1/boot/grub/menu.lst
```

---

### Post by twisted_steel on 2007-11-28
> **gubemton said:**
> Can Ubuntu write into NTFS anyway?

Yes, it can with the 7.10 release.  If you have the Live CD, you should be able to open up your Vista partition and copy the files over there.

---

