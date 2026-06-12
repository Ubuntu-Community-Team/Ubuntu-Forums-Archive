---
title: "Been asked a hundred times before, but...."
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-05-12
Just to be finally sure, before talking my father, over the phone, through installing Ubuntu on his XP machine (attack the family first, next the whole world! he he he!!):

He has no XP setup disk, just a recovery disk and a partition (which I guess is like a ghost disk image?)
All the rest of the disk is dedicated to XP, I presume NTFS (to be confirmed!)

Ubuntu installer should offer the option to resize the NTFS partion and create space for an Ubuntu install, plsu add the Grub menu.

Am I correct so far? (I think so..)

If he needs to reload XP at any time using the recovery disk and partition image, what are the chances of it overwriting the ubuntu install and grub?

Plus if he has a virus that has affected his MBR (which is a possibility, we think) would a grub install overwrite teh MBR and delete the virus, or should we do some full hdd format first (possibly deleting the ghost partion in the process?

Don't let me cock up my father's machine on this one guys!...

---

### Post by mostwanted on 2006-05-12
Backup, backup, backup!

(whenever there's a risk, that's what you do)

---

### Post by damianubuntu on 2006-05-12
OK,but say we backup (already doen, in fact :-)) and then say it all goes wrong, will he be able to reinstall from the ghost partiton and recovery disk, without trashing the Ubuntu install?

---

### Post by mostwanted on 2006-05-12
[QUOTE=damianubuntu]OK,but say we backup (already doen, in fact :-)) and then say it all goes wrong, will he be able to reinstall from the ghost partiton and recovery disk, without trashing the Ubuntu install?[/QUOTE]

Well, you'll trash the Ubuntu bootloader, but that can be reinstalled by your Ubuntu install disc (just skip the regular install steps).

If you've already backed up your stuff, I recommend reinstalling Windows and leaving free space for Ubuntu, then installing Ubuntu. That's one way to success, but reinstalling programs in Windows might be too tedious? I don't know, you decide - it's your computer after all :)

When you're installing Ubuntu, it's a good idea to make a /home partition besides the regular swap and / (root) partitions. That way you can preserve settings and files, while the entire operating can be erased and reinstalled (you can even use a different distro!).

---

### Post by Al3xanR0 on 2006-05-12
[QUOTE=damianubuntu]OK,but say we backup (already doen, in fact :-)) and then say it all goes wrong, will he be able to reinstall from the ghost partiton and recovery disk, without trashing the Ubuntu install?[/QUOTE]

The Windows sytem restore cd does not make provisions for partition sizing; if you are dual booting and you have to restore using it, it will restore to factory defaults. Remember when that box was shiny and new? Yeah like that.

---

### Post by mostwanted on 2006-05-12
[QUOTE=Al3xanR0]The Windows sytem restore cd does not make provisions for partition sizing; if you are dual booting and you have to restore using it, it will restore to factory defaults. Remember when that box was shiny and new? Yeah like that.[/QUOTE]

Huh? Mine does. Maybe it's a manufacturer thing (I have Fujitsu-Siemens restore disc).

---

### Post by NeghVar on 2006-05-12
The problem if u have a recovery partition is that that space is useless to u unless u need to backup. If it is set uop this way then restoring XP will most likely hose yr ubuntu install.

i hate companies doing it this way, its just meant to get u to HAVE to use them for tech support in the future unless u want to buy a new cd or are luky enuf for them to giver u a cd if they can c yr license.

---

### Post by bobpur on 2006-05-12
Just a thought,but...
If he suspects a virus he should do a system restore or a full re-do of the operating system before he does any backing up of anything.If he backs up anything that has the virus in it, he'll just keep re-infecting his system (Been there, Done that).

---

