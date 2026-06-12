---
title: "What to do with Second Hard Drive"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-05-12
Hi:
I have Feisty running as my default os on a 20GB drive.  I have xp on a second 20GB drive, which I am not using at all.  I have dual boot setup, and did a mapping thing something like
map 0 (0,1)
map 1 (1,0)

in order to trick xp into thinking it was master.  I followed a tutorial on this forum.  It worked anyway.

Um, so now that I am comfortable with ditching xp, I am not sure what to do with this second drive.  I have 7.5GB free on my feisty drive.  I was thinking of formatting the second drive with Gnome Partition Editor.  I eventually will want to have a 1GB or so FAT32 partition shared with another xp machine on our home network.  I may want to try Kubuntu to compare Gnome with KDE, or try another linux os, just because they are out there.  Thinking of Elive maybe.

Do I need to edit any files in Grub when I want to format my second drive? 

Am I missing something else I need to do?

Would I need to do anything special, other than point the installer of Kubuntu to the correct hard drive, which I think would be hd1?

Thanks,
Ziffnabb

---

### Post by juxtaposed on 2007-05-12
Well, I don't know about changing GRUB, but you don't need to install kubuntu to compare gnome with KDE.

You can have many different desktop environments and window managers installed. Just choose which one you want to use in the select session part of the log in screen (GDM).

I believe 'sudo apt-get install kubuntu-desktop' is how to install KDE. Then there is XFCE, IceWM, Enlightenment, FVWM, Openbox, Fluxbox, Blackbox, and many more other ones to try.

---

### Post by dwblas on 2007-05-12
> Would I need to do anything special, other than point the installer of Kubuntu to the correct hard drive, which I think would be hd1?It would actually be hdb2, as the FAT32 would probably the first partition on that drive=hdb1.  You want to unmount the drive if it is mounuted, use gparted or cfdisk to repartition and format the dirve.  Then install KUbuntu.  KUbuntu will find both Ubuntu's and update GRUB for you, so you will be able to choose between the two when you boot.  I have two Ubuntu's on my system.  One is a stable system and the other I use for testing Feisty, soon to become Gutsy.  I also use a second drive to back up critical data on a daily basis via crontab, in case one drive fails.

---

