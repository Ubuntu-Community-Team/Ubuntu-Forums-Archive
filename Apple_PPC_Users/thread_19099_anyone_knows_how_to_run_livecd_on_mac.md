---
title: "anyone knows how to run livecd on mac"
date: 2005-03-10
forum: Apple PPC Users
---

### Post by xyzhao on 2005-03-10
Hi, 

I am a first timer, i downloade the live cd iso and burn it, but when i restart my comp, hold down the c key, ( i tried shift, option, control,delete) as well, it would not boot on the cd, it kept on going back to the harddisk booting,

the image is hoary-live-powerpc.iso

i am running iMac g4 1ghz
any help would be appreciated, as i want to try running linux on mac

xyzhao

---

### Post by iamgolf857 on 2005-03-10
Well, Ubuntu is pretty good about booting from CD on Apple Hardware, but if your ISO is just not working, you could try an Open Firmware Boot.  To do this you have to   know the directory on the CD where yaboot is located (make a note of it).  Then hold down Apple-Option-O-F during the reboot sequence.  When you have access to the Open Firmware screen, type:  **boot cd:,\directory\for\yaboot** This should force your Mac to boot the CD.

---

### Post by ssam on 2005-03-10
its easier than that.

a mac will boot from cd if you hold the 'C' key at boot.

if you boot with the 'alt' key held it will list all bootable partitions.

also on some machines (powerbook and ibooks i think) if you hold down 'T' the machine goes into target disk mode. it basically pretends to be a firewire hard drive, which you can then plug into another machine.

there are a few more that i cant think of offhand, should be a list on the web somewhere.

ssam

---

### Post by iamgolf857 on 2005-03-10
[QUOTE=xyzhao]
I am a first timer, i downloade the live cd iso and burn it, but when i restart my comp, hold down the c key, ( i tried shift, option, control,delete) as well, it would not boot on the cd, it kept on going back to the harddisk booting,
[/QUOTE]
Since holding down 'C' during the boot sequence isn't working, isn't it also likely that doing an 'Alt' boot won't work?  I have experienced this problem also with different ISO discs (namely Debian stable) and found the easiest way to get the CD to boot every time is to do the Open Firmware boot that I posted earlier.  Just a suggestion.

---

### Post by skipunk on 2005-03-10
are you sure you burned the iso correctly.  You have to use a program that specifically can burn iso's.  You can't just copy it onto a cd and burn

---

### Post by Leonida on 2005-03-10
[QUOTE=skipunk]are you sure you burned the iso correctly.  You have to use a program that specifically can burn iso's.  You can't just copy it onto a cd and burn[/QUOTE]
Read [How to burn ISO image](http://ubuntuppc.webplazahosting.com/index.php?FrontPage) in PPC Wiki Guide. Also check the md5 sum before burning.

---

### Post by plantwater on 2005-03-13
Thank you  :) 
[QUOTE=iamgolf857]Well, Ubuntu is pretty good about booting from CD on Apple Hardware, but if your ISO is just not working, you could try an Open Firmware Boot.  To do this you have to   know the directory on the CD where yaboot is located (make a note of it).  Then hold down Apple-Option-O-F during the reboot sequence.  When you have access to the Open Firmware screen, type:  **boot cd:,\directory\for\yaboot** This should force your Mac to boot the CD.[/QUOTE]
 brilliant; thank you... the apple+option+o+f boot and "boot cd:,\install\yaboot" worked for me; also some bugginess with the cd-rom was resolved by ejecting and re-inserting the disc a couple of times and re-typing the same command.

---

