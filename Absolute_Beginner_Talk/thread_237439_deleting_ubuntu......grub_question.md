---
title: "deleting ubuntu......grub question??"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-08-16
i have a pc with windows and ubuntu, and grub is installed so i get a screen at start up to choose which os to boot. i recently got an old pentium 4 and have installed ubuntu on that (my other system is 64 bit and as you all know 64 bit ubuntu isnt easy for us n00bs). any way, windows is on a 120gb sata drive and ubuntu is on a 80gb sata drive on the 64 bit system. my question is if i format the 80gb linux drive from within windows, will my pc just go back to booting up normally? cause i know grub is installed on the mbr (i dont know where that is) and i dont want to screw it up. 
thanks

---

### Post by mcneely.mike on 2006-08-16
pop in the windows cd and boot to the cd (can't remember what option exactly that it is).  you want text mode and just the cd, not windows.

then type (someone help me on this??) but i think it was
  fdisk /mbr   or   fdisk \mbr    or something mbr

this will reinstall the windows master boot record and bob's your uncle \\:D/

---

### Post by anaconda on 2006-08-16
I think it is "fixmbr" and "fixboot".. fdisk /mbr works with windows boot floppies (which have fdisk installed..)

If your grub is installed to the 80GB disk, you will be OK, just make the windows drive the master drive, (which bios tries to boot first) I think this is done by switching the SATA cables so thet the drive you want to be master goes to first SATA place on the motherboard..

On the other hand, if grub is on the beginning of your windows drive (windows is on the master drive..), then you have to fix your mbr from that drive..

---

### Post by e1ektrob0y on 2006-08-16
windows is on the master drive (120 gb sata) and linux on the 80gb second drive. when i installed ubuntu it installed grub as part of the installation. does that mean it must be on the linux drive or?......... what if i just format the linux drive and leave it. will grub still load and will i still be able to boot windows from it (just not be able to boot linux) i thought it would be simpler..............damn!

---

### Post by mcneely.mike on 2006-08-16
if you install   lilo   boot manager and get it working, then you will be fine, but grub looks for the boot files on the linux partition, so i don't think it will work.

try apt-get install lilo, or use synaptic.

---

### Post by bernied on 2006-08-16
Some clarification:
If you have this setup:
- first BIOS drive 120gb with Windows
- second BIOS drive 80gb with Linux
- booting with grub
Then:
- grub stage 1 is installed to the mbr of the 120gb drive. This links to the rest of the grub files, which will be on the 80gb drive.

So if you wipe or remove the 80gb drive, you will get an error in the boot process (the infamous GRUB GRUB GRUB GRUB etc).
What you want to do is what anaconda said - run fixmbr. This is available either on your Windows CD, or you can also get it from a live-cd called FreeDOS. You should find some documentation on this utility before you run it though.

If this works, Windows will start straight away when you boot. Once you have got to this stage, you can do what you like with the 80gb drive (format, remove, etc).

---

### Post by bernied on 2006-08-16
A little more clarification:
fixmbr will replace the mbr with the one that windows uses - this simply chainloads the bootloader on the first partition of the first drive.

---

### Post by e1ektrob0y on 2006-08-16
ok fixmbr sounds like the go......so could someone talk me through the exact proccess. i set my pc to boot from my windows install cd and then when do i type fixmbr etc.....i dont remember seeing options for typing commands last time i booted from that cd........thanks

---

### Post by anaconda on 2006-08-16
You select the "rescue" option, or something like it (havent done it in a loooong time)

And finally you should get to msdos command prompt. and there you want to write "fixmbr" (and optionally "fixboot")

EDIT: the lilo option should also work....

---

### Post by e1ektrob0y on 2006-08-16
yeah i just tried it with my xp cd. i went to the rescue thing and it said insert the floppy rescue disk........so i just got scared and re-booted.

---

### Post by anaconda on 2006-08-16
No need to get scared. If you dont have the floppy rescue disk, or dont want to insert it, then you get to the command prompt, where you wanted to go anyway...

---

### Post by e1ektrob0y on 2006-08-16
i thought that would be the case but it just keeps saying insert floppy and press any key to continue with automated system recovery. i cant get any further than that cause i dont have the floppy!! every time i press enter i get the same message "insert floppy"
if i installl lilo will that over ride grub or re-write the mbr itself or??

---

### Post by seshomaru samma on 2006-08-16
YOu should be able to fix mbr with this:
[http://www.freedos.org/](http://www.freedos.org/)
the command is probably:
```
fdisk/mbr
```

---

### Post by DNSBubba on 2006-08-16
Put in your Windows XP cd and restart. When it loads, select the "Recovery Console" (Note: May be called "Repair Console" on your version) option. When it gets to the command line, type "fixmbr ". You may get a warning, select "y" to continue. Reboot when it's complete.Windows should boot normally.

---

### Post by e1ektrob0y on 2006-08-17
ok so i've created a freedos bootable floppy. apparantly i just

> Boot from this CD/floppy and select "1" for "Boot FreeDOS Setup" first and then "3 - Clean Boot" from the start menu. Start fdisk with:

     fdisk /mbr

By doing this, the boot loader GRUB will be overwritten.

what i'm wondering is, am i actually completing the installation of free dos or just using it to fix the mbr? do i just exit the installation and reboot after fixing is over?
thanks

---

### Post by Scythe!? on 2006-08-17
> **e1ektrob0y said:**
> yeah i just tried it with my xp cd. i went to the rescue thing and it said insert the floppy rescue disk........so i just got scared and re-booted.

you need the recovery console.

---

### Post by asfx on 2006-08-17
Ignore this pls

---

### Post by asfx on 2006-08-17
Found a nice howto here.. take a look:

[http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Has a section on replacing the mbr without a XP CD
(You were having a problem getting to the CMD line.)

---

### Post by catlett on 2006-08-17
You will not be able to boot into windows if you remove and/or erase the ubuntu partition.
You need a "real" windows xp installation cd, not a rescue disk that a computer maker sends with your system . I say this because when you put in a windows xp install disk, it does not ask for a flopppy disk to be installed.

I do not know anything about FreeDos but here is a graphical hgow to about the recovery console [http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html)

---

### Post by e1ektrob0y on 2006-08-17
well obviously my xp cd doesnt have the recovery console. what if i use my girlfriends xp cd. would that work or does it have to be the same cd that i installed windows with?
or, can i create a recovery floppy from somewhere to insert when i'm prompted from my cd?

---

### Post by DNSBubba on 2006-08-17
You can use your girlfriends CD.

---

### Post by e1ektrob0y on 2006-08-17
> **DNSBubba said:**
> You can use your girlfriends CD.
sweet that worked a treat!!! now i should be able to safely format the linux drive, right?

---

### Post by e1ektrob0y on 2006-08-17
if anyone's interested, i ran fixmbr from the windows cd, then deleted all partitions on the linux drive and formated it. now everything works fine and i have 1 pc with windows and 1 pc with ubuntu. it boots normally and i now have a free 80gb sata drive for backups etc. thanks to all those who helped me i appreciate the free knowledge and experience..................cheers.

---

### Post by asfx on 2006-08-17
Great..:cool:

---

