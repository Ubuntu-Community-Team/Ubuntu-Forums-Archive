---
title: "White macbook"
date: 2009-11-24
forum: Apple Hardware Users
---

### Post by n8ek on 2009-11-24
I have installed Ubuntu 9.10 on my 13" white macbook quite a few times in the last 24 hours and i get the same problem every time.

The install goes well i install grub on the same partition as Ubuntu, reboot see the grub menu, as it boots Ubuntu i just get left with a black screen and nothing else.

When i install i have to choose acpi off i have rEFIT installed but on start up it skips that and goes straight to the grub menu.

What have i done wrong if anything or what has gone wrong?

Thanks in advance

---

### Post by linuxopjemac on 2009-11-24
what version of macbook ? I own a MacBook Late 2006, code 2,1. Check out yours.

---

### Post by n8ek on 2009-11-24
Its the early 2009 white 13" macbook 5.2

Thanks

---

### Post by linuxopjemac on 2009-11-24
[http://ubuntuforums.org/showthread.php?t=1335409](http://ubuntuforums.org/showthread.php?t=1335409)

---

### Post by n8ek on 2009-11-24
Thanks, i just looked at that restarted the mac and was unable to figure out where to type acpi=off and the stuff in your reply?

When i installed i had to choose acpi off before it would start.

Thanks

---

### Post by linuxopjemac on 2009-11-24
> To modify the boot options within the grub menu, highlight the operating system you want to edit and press 'e'.
There you will be presented with lines starting with 'root', 'kernel', 'initrd', 'quiet' and 'savedefault'.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by linuxopjemac on 2009-11-24
also interesting for you:
[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

### Post by n8ek on 2009-11-24
Thanks for those links, will try with a 64bit version and follow this [http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758) to the letter.

Hopefully all goes well

Thanks

---

### Post by n8ek on 2009-11-24
I followed the guide to the letter and it still refuses to boot i see grub press e add acpi=off at the end of line of my kernel version ctrl + x to boot Ubuntu and then nothing

?

Thanks

---

### Post by linds2009 on 2009-11-25
Sorry, did not encounter such a situation

---

### Post by jacobs444 on 2009-11-25
why are you installing grub to the same partition as ubuntu instead of the MBR?

---

### Post by n8ek on 2009-11-25
[http://ubuntuforums.org/showthread.php?t=1327758i](http://ubuntuforums.org/showthread.php?t=1327758i) followed that guide and installed 9.10 and 9.04 16g for ubuntu and 4g for swap using ext3 i put GRUB in the UBUNTU partition and now on both versions of Ubuntu all i get is a black screen with GRUB in the top right of the screen and that's as far as it goes, should i install GRUB elsewhere?

Thanks

---

### Post by n8ek on 2009-11-25
Here is the output from rEFIT partition inspector


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    190988327  Mac OS X HFS+
 3      191252480    234440703  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    190988327  af  Mac OS X HFS+
 3 *    191252480    234440703  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 191252480:
 Boot Code: Unknown, but bootable
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active


Maybe looking at that some one can help.

Thanks

---

### Post by linuxopjemac on 2009-11-25
did you sync the partition table from rEFIT and put the boot flag on the linux partition with gparted from the liveCD?

---

### Post by n8ek on 2009-11-25
I went straight for the install, (skipped testing the live cd), after every install i ran gptsync.efi at the efi boot and all i get is a black screen with grub in the top right.

put the boot flag on the linux partition with gparted from the liveCD, didnt know i had to do that will try another install and do that (lost count how many i have done now?)

Thanks

---

### Post by Dans564 on 2009-11-25
Just installed karmic on my macbook about a week ago using boot camp. What i did was made a partition using bootcamp app while i was on my mac partition, then booted from the live cd.  select "try ubuntu without any change to my computer" then system--->administration-->disk utility.  in disk utility delete the bootcamp partition so that it is empty space on your hd.  Then when installing just select install on free space and your done.  hope this helps

PS.. make sure u delete the bootcamp partition not ur mac install.  refit will work as well.  

pss. i don't know what ur talking about with installing grub i didnt have to do that

---

### Post by n8ek on 2009-11-25
sda3 is the linux partition, i install grub there and on my last install a few minutes ago i got the same black screen, no grub menu.

I might try your way Dan564, not tried that way yet.

Thanks

---

### Post by n8ek on 2009-11-25
Dan564, that way worked. I now get to see the grub menu.

Another problem that has plagued me, when i install i have to choose acpi=off then when i boot Ubuntu at grub i press e on the very last line the one i think is /boot/vmlinuz-kernel no---- i add acpi=off to try and get it to boot yet again still no GUI?

Thanks

---

### Post by lepukowsky on 2009-11-25
n8ek I followed the guide that has been posted a few times that it looks like you have already tried:
[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

because I have a 5,2 macbook too. If I understand you correctly when you are hitting ctl+x your system is hanging and not making it into ubuntu. If this is obvious I am sorry, but the same thing was happening to me for a bit because I was adding the "acpi=off" text to the very end of that file, when really it should be end at the second to last line, which you can get to by going down the last line and hitting the left arrow. 

Again, sorry if this is obvious or you have already been doing it right, but considering i'm a total linux newb and that tutorial got me going in no time i thought it might just be a stupid error like that ( i rebooted 4 times before typing it on the right line ;) )

---

### Post by n8ek on 2009-11-25
YEEEEEEEES Ive finally done it, i am typing this in Ubuntu,(not got everything working yet) thanks to you all, lepukowsky the advice on acpi=off obviously worked very very grateful for that, now to find the guide that advises how to stop inputting acpi=off at every boot.

A big thank you to you all, 

Thanks.

---

### Post by Dans564 on 2009-11-25
glad my way helped :p

---

