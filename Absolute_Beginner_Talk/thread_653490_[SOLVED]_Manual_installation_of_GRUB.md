---
title: "[SOLVED] Manual installation of GRUB"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-12-30
Hello,

I need to install GRUB manually after doing an Ubuntu installation with the alternate CD. At the end, when I was asked where to install GRUB, I chose to not have it installed in the first disk's MBR since I'm already using GAG as my main boot menu.
Instead, I wanted to put it on disk I've installed Ubuntu on (sdc). But since I wasn't quite sure which device to specify, I attempted to get to another prompt to look up the partitioning information. I dimly recalled that you can use F1 - F2 and ctrl or some other key to do that. In fact, in an earlier installation attempt I had already gotten to another prompt that way. 
But this time must have hit the wrong keys since all of the sudden the installation proceed without me having specified anything. 
So now I've booted from the installation CD again and am at a command prompt. I mounted my boot partition sdc1 and lo and behold, there is a GRUB directory. It seems to contain only 2 files though, "default" and "menu.lst". 
With the installation cd in the drive, how can I install GRUB now? 

Thank you.

---

### Post by clayt0njknight on 2007-12-30
an MBR is exactly as the term says- Master Boot Record.  You MUST have a bootloader in your master boot record in order to access the operating systems running on your system.  Edit your GAG Boot chooser and add an entry in there for Ubuntu, pointing to the location of the Ubuntu Partition (Disk,Part#).

---

### Post by Niniel on 2007-12-30
Uhm, thank you for your reply, but that wasn't really my question. 
Gag doesn't see Ubuntu, so I figured something must have gone wrong during the GRUB installation.
I want to re-install GRUB so that I can boot into my Ubuntu.

---

### Post by meierfra on 2007-12-30
Click on FixGrub in my signature for instructions how to reinstall Grub. If you need more help:

Boot from the Ubuntu Live CD.
Go to Places->Computer and double click the Ubuntu partition. (This mounts your Ubuntu partition.)

Post the output of 

```
sudo fdisk -l
```

and

```
cat /media/disk/boot/grub/menu.lst
```

(all "l" are lower case L, not the number one)

---

### Post by carusoswi on 2007-12-30
MEIERFRA:
Great info at the bottom of your post.  I have bookmarked this for future reference.  Things are running smoothly now, but there have been occasions in the past where I could have used quick reference to the info you have provided.

Thanks, and have a Happy New Year.

Caruso

---

### Post by meierfra on 2007-12-30
> MEIERFRA:
Great info at the bottom of your post. I

Thanks, 
Just yesterday I wanted to add a couple of more links, but  they wouldn't  let me. I can use only so many characters, and they count each single letter in the URL's.

---

### Post by Niniel on 2008-01-03
Ok, I got this resolved... not quite the way I wanted to, but at least I can boot now.
After I failed to install Grub to my 3rd hd - both from Live CD and alternative CD - I put it in the 1st drive's MBR. But then I got an Error 21. But that was fixed with a BIOS adjustment and now I get a the boot menu, and both OS boot fine. It wiped out my GAG, but I'm not sure I want to mess with it anymore. :)
Although maybe I should... could be that the initial problem was also due to the old BIOS settings.

---

