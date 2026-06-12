---
title: "Problem upgrading to Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-21
I started the upgrade to Feisty through the Update manager in 6.10.  Since it was going to take forever to download and install the files, I left the computer.  When I came back, it had been restarted, so I shut it off.  Came back the next day to boot up into feisty, and the boot up screen was on forever, without the bar moving, and then I got this message:

BusyBox v1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I'm not sure what happened, or what to do next.  Can someone please advise?  

Thanks.

---

### Post by DougieFresh4U on 2007-04-21
Some times I have gotten that and I just kept rebooting and it finally booted. That may have just getting lucky for me!!

---

### Post by ashz on 2007-04-21
Yeah its because grub is not pointing to the right location for the hd... for instructions in this thread...

[http://www.ubuntuforums.org/showthread.php?t=279884](http://www.ubuntuforums.org/showthread.php?t=279884)

cheers
ash

---

### Post by thefoolisme on 2007-04-21
OK, I used the instructions in that thread, but didn't get very far.  This is what I got:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/hda2            4463        9729    42307177+   f  W95 Ext'd (LBA)
/dev/hda5            4463        5737    10241406    b  W95 FAT32
/dev/hda6            5738        5750      104391   83  Linux
/dev/hda7            5751        7598    14844028+  83  Linux
/dev/hda8            7599        9447    14852061   83  Linux
/dev/hda9            9448        9729     2265133+  82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo  mount /dev/hda6 /mnt
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
abi-2.6.17-10-generic         initrd.img-2.6.17-11-generic.bak
abi-2.6.17-11-generic         lost+found
abi-2.6.20-15-generic         memtest86+.bin
config-2.6.17-10-generic      System.map-2.6.17-10-generic
config-2.6.17-11-generic      System.map-2.6.17-11-generic
config-2.6.20-15-generic      System.map-2.6.20-15-generic
grub                          vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic  vmlinuz-2.6.17-11-generic
initrd.img-2.6.17-11-generic  vmlinuz-2.6.20-15-generic
ubuntu@ubuntu:/mnt$ cd etc
bash: cd: etc: No such file or directory
ubuntu@ubuntu:/mnt$ 


I know hda6 is the linux boot partition.  Can anyone help with this problem?  I'm sure it's just a grub fix, but I'm not sure how to fix it.  

Thanks.

---

### Post by zvacet on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by msak007 on 2007-04-23
I just had the same exact problem and it ended up NOT being a problem with GRUB or the UUID of my HD. All the kernels (including 2.6.20-15 recovery mode in Feisty) booted except the 2.6.20-15-generic kernel. I kept getting the error you're getting, in addition to "hdX: lost interrupt" repeatedly (X is for all my hard drives), a bunch of invalid IRQ reference error messages before the boot, etc. What ended up fixing it for me is removing "noapictimer" from the end of my boot options for the kernel. I had that appended to the defaults because my Athlon XP2800+ gets so out of sync with the time that I had to have that option to keep the clock running like normal. Now my system boots, but I'll have to leave it running for a few days and see if the clock goes out of sync again.

---

### Post by thefoolisme on 2007-04-23
> **msak007 said:**
> I just had the same exact problem and it ended up NOT being a problem with GRUB or the UUID of my HD. All the kernels (including 2.6.20-15 recovery mode in Feisty) booted except the 2.6.20-15-generic kernel. I kept getting the error you're getting, in addition to "hdX: lost interrupt" repeatedly (X is for all my hard drives), a bunch of invalid IRQ reference error messages before the boot, etc. What ended up fixing it for me is removing "noapictimer" from the end of my boot options for the kernel. I had that appended to the defaults because my Athlon XP2800+ gets so out of sync with the time that I had to have that option to keep the clock running like normal. Now my system boots, but I'll have to leave it running for a few days and see if the clock goes out of sync again.

Where did you make that change about noapictimer, since you said it wasn't a GRUB error.  I'm a total noob  :-)  Is that language that would been installed automatically, because I know I've never put it in any file.  

Interesting side note, the processor in the PC I'm having this problem with is also an XP2800+.  Hmmmm.....

---

### Post by msak007 on 2007-04-23
> **thefoolisme said:**
> Where did you make that change about noapictimer, since you said it wasn't a GRUB error.  I'm a total noob  :-)  Is that language that would been installed automatically, because I know I've never put it in any file.  

Interesting side note, the processor in the PC I'm having this problem with is also an XP2800+.  Hmmmm.....
Sorry I was just throwing it out there, wasn't sure how familiar you are with everything. It was just what fixed it for me, but it may not be the case with you especially since it's not added automatically - it's something I added manually.

Basically some processors have a problem with the clock being too fast. I started noticing that after the comp was on for a couple of days, the clock could be off up to 30 mins! So anyway I found [this]("http://ubuntuforums.org/showthread.php?t=75281") thread (also [here]("http://doc.gwos.org/index.php/Double_Clock_Speed")) which talked about the problem and ways around it. What you do is append a flag to your kernel options and it fixes the clock timing, but the only one that I found worked for me as "noapictimer". I added it to my default options so that when the updater updates the grub menu after a kernel update, that option gets appended automatically (otherwise I'd have to add it manually every time). 

Anyway if you follow either of those links it goes into detail about how to edit your grub menu. You should see something like this in /boot/grub/menu.lst

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6479350f-c59c-45cc-a578-24358d88311c ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

The "noapictimer" was at the end of the "kernel" line. Once I removed it, it booted normally.

---

