---
title: "Grub and Windows  XP"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-08
When I get to the Grub menu and select the Windows XP option, grub disapears a message appears ¨Starting windows...¨. The thing is, windows never starts, the message just sits there.

Any Ideas?

Thanks,

Rudolf

---

### Post by richardhp on 2007-01-08
what does your menu.lst file say?

should be in /boot/grub/menu.lst or somehwere similar.

---

### Post by RudolfMDLT on 2007-01-08
There is quite a lot, I think the important part is this:
> 
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Windows is installed on hda1

---

### Post by Duck2006 on 2007-01-08
You could try

#savedefault

In the windze loader part of the loader

---

### Post by Bigbluecat on 2007-01-08
Did something happen to your PC to make this suddenly happen (windows crash for example)?

If you see the message "starting windows" this suggests that you are beyond grub and into the windows boot routine.

The Microsoft site has some help on fixing boot issues using the recovery CD. From the recovery console you can use DOS to find or repair NTLDR and other boot files.

---

### Post by RudolfMDLT on 2007-01-09
Yeah - I installed Mandriva and that screwed up everything!

---

### Post by RudolfMDLT on 2007-01-10
I just checked - Grub says "starting up" for both Windows and Linux so it's not windows thats corrupt - Grub cant load it for some reason!

---

### Post by RudolfMDLT on 2007-01-11
Anybody got any ideas on what the problem is when Grub displays "Starting up" for both Windows and Kubuntu but never boots windows and neither does Grub display an error?

Please people, I cannot fix this on my own, I  really have tried!

Thank you,

Rudolf

---

### Post by confused57 on 2007-01-11
You could try reinstalling grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If this doesn't work, you could try booting with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It may help to post your partition tables, bootup with the live cd, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L"

If you're not able to boot Windows with the Super Grub Disk, then it probably is a Windows issue, rather than grub.

---

### Post by aberry5555 on 2007-01-11
I had the same problem. I presume your GRUB is installed on the boot sector at hd0,0 so all it's doing is looping itself, probably this version of GRUB either doesn't like looping or was designed not to. Basically find out which drive XP is on and, most importantly, which disk to boot from for windows, then, using the windows recovery console that's on the XP CD, rebuild the boot sector for windows and writing to the boot sector of the drive that it's on. Then, in Ubuntu rebuild the grub (I can't remember how to do this in Ubuntu, but search here or google it) making sure that the Windows option links to the Windows drive. This is, of course, only one way to do it, there are many ways, for instance with my dual boot I copied the first 500 bytes of my linux drive to a file and installed a link in the boot.ini file in windows to that file (stored on the local C:/ drive) Basically what this does is read it as the link to the GRUB folder on your PC and takes you straight to it, thus avoiding pain-in-the-arse GRUB or boot-loader re-installs; I just make sure I have that file plus my boot.ini entry saved on a floppy or USB pen.

---

### Post by RudolfMDLT on 2007-01-16
Thanks Guys - Sorry for only replying now! I'll try all of this tonight! Thank you very much!

---

