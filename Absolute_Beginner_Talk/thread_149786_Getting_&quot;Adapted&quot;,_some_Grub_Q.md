---
title: "Getting &quot;Adapted&quot;, some Grub Q"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by petrus66 on 2006-03-24
Hi,

  Totally beginner here, but I feel in my vains that I'm beeing adapted to Linux soon ;)
I struggled for 2 days to get my graphical interface up on Ubuntu.
  The problem was on my graphic card, ATI X800 GTO, that I got in use with browsing old threads on this forum.
  Newertheless, heres my question:

1.  Default boot option (the most upper) dont load any network interface anymore.
    I have tried to load up system network GUI, but after some waiting nothing                  happens.
   I tried to Sudo some dhclient and ifconfig eth0 up..   reboot and no remains.

The solution has been to choose same kernel version from Grub that has been located more down on the load menu. Now I can acces the Network GUI again and enable the default eth0 with dhcp again.

The lower boot option seems, after what I understand this far, to use some kind of
"boot image" versus that default boot option that boots directly into root.

Am I totally dissoriented or is there any sense of this?
Grub is pointing to some kind of img:s anyway.

SubQuestion is how to make the working boot option to be the "real" and only?

The Default without network working:

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/hda4 ro rescue quiet splash
initrd		/boot/initrd.img
savedefault
boot
  
versus the one that is working: 

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda4 ro rescue quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

This has been copyed from /boot/Grub/menu.lst
That I actually changed to boot with default   4  option
(but the non-that-working option still remains into top in menu)

Yes, the problem came after I installed 2:nd independed XP install to same HD and had to use linux rescue from the installation CD to reinstall Grub.
I re-installed Grub, not into MBR, but into same partition that before

Anyway, the more I mess with Linux so far, the more interested I has become.
The time has not luckily been redused from my family, more than from gaming.
So family gets just as little time as before ;)

Thanks for ya patience,

---

### Post by dcstar on 2006-03-24
[QUOTE=petrus66]
......
The Default without network working:

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/hda4 ro rescue quiet splash
initrd		/boot/initrd.img
savedefault
boot
  
versus **the one that is working**: 

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,3)
kernel		**/boot/vmlinuz-2.6.12-10-amd64-generic** root=/dev/hda4 ro rescue quiet splash
initrd		**/boot/initrd.img-2.6.12-10-amd64-generic**
savedefault
boot

This has been copyed from /boot/Grub/menu.lst
That I actually changed to boot with default   4  option
(but the non-that-working option still remains into top in menu)

Yes, the problem came after I installed 2:nd independed XP install to same HD and had to use linux rescue from the installation CD to reinstall Grub.
I re-installed Grub, not into MBR, but into same partition that before
......[/QUOTE]
Don't panic, it seems reinstalling Grub has just caused it to put in a default entry that loads incorrect files (you seem to need all the "-2.6.12-10-amd64-generic" ones).

Just manually copy the working block of code from where it is to the top of your list, it should be fine after that.

---

