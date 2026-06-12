---
title: "Using the Super Grub disk? ( I'm such a newbie, I know. :/ )"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-11
OK, so I go to boot my Super Grub disk. Now, it does some stuff and then all of a sudden ( on both versions burned on CD , it wants me to enter something after 
[DR-DOS] A:\>

maybe I'm blind, and couldn't find a proper istallation guide, but can anybody tell me what it wants?? I reinstalled windows now I'm trying to get grub going again...help this person of so little linux knowledge?

---

### Post by arkangel on 2006-10-11
i think you are burning wrong the image,  the image contains information of how to boot and the rest

however with nero and others  when you specify  burn files  and  you mark the  option "make it bootable"  it will burn the files as files and it will put dr dos in oyur cd for   booting 

to burn an image  [here an official wiki]("https://help.ubuntu.com/community/BurningIsoHowto") , this works for all linx iso

---

### Post by catlett on 2006-10-11
If you are still trying to restore grub try this [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
The earlier issue, [DR-DOS] A:\> that is a dos propmt at a boot floppy. A:> is your floppy drive letter and you are now in it at a dos prompt. The next thing is to issue the commands you want to.

---

### Post by Ryupower on 2006-10-12
Thanks! I burned the iso on the cd as I would normally, but now I have a NEW issue ( :'( ). I try to boot from it, it does something, then the screen turns black and it starts booting Windows! Anyone know why it's not working?

---

### Post by dddouglas on 2006-10-12
What do you mean by "*it does something*" ? Is your bios set up to primary boot from cd ? Enter your bios set-up by pressing whatever your boot splash intructs you to. ie F8, F1, Del. Be careful it usally helps to make notes of what it is there before you change it but many bios have failsafe defaults.

---

### Post by Ryupower on 2006-10-12
> **dddouglas said:**
> What do you mean by "*it does something*" ? Is your bios set up to primary boot from cd ? Enter your bios set-up by pressing whatever your boot splash intructs you to. ie F8, F1, Del. Be careful it usally helps to make notes of what it is there before you change it but many bios have failsafe defaults.
yes, primary is CD. 
with "it does something" I mean it types something ( booting disk...etc.etc. couldn't completely read it all in that one seconed ). But after those, like, three lines are typed,windows starts booting. I didn't do anything, it just started....:/

---

### Post by dddouglas on 2006-10-13
What seems to be happening is the BIOS doesnt like the CD. It is seeing the boot sector but nothing beyond it so it moves to the next boot device. It sounds like either your cd drive is defective (doughtful but possible)  or the disk may be a bad burn. (coaster) I have had a couple of time burning an iso with Nero that the disk did not work. The first Live CD I burned went that way. If you have a Live CD you can check your drives bootablity with it and it is possible to retore your GRUB with it using catlett's instructions [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
But I prefer Super GRUB disk for it's simplicity.

---

### Post by Ryupower on 2006-10-13
thanks. :)
mayvbe it's a bad burn, I used nero too.

I tried using those instructions and, sonce I didn't pay attention to the "do not format" correctly ( found out it meant do not format ANY of them...^^; ) I formatted it and got to reinstal everything...^^;
So I got that done, off to my next thread I'm gonna make:" WHY ISN'T MY WIN 2000 BOOTING PROPERLY?? "

---

