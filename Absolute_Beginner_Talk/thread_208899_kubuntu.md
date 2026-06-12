---
title: "kubuntu ??"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-07-04
i finally got rid of mswindows from ma machine. i installed ubuntu dapper on hd1 and kubuntu dapper on hd2. 1. how do i share between the two?
                                   2. internet on ubuntu was easy to set up (dsl). on kubuntu i am having problem setting the networking preferrences: mainly the dns numbers.
any help is welcomed.

---

### Post by frodon on 2006-07-04
Wow, there's no need to install both ubuntu and kubuntu !

It would be the same to install ubuntu on hd1 then add the kde desktop to your ubuntu install.

---

### Post by Elim on 2006-07-04
A bit more elaboration: As I think you're aware, you currently have two operating systems installed.  However, Ubuntu and Kubuntu are not really, in fact, two different operating systems.  What we call "Ubuntu" is the Ubuntu operating system with GNOME, and what we call "Kubuntu" is the Ubuntu operating system with KDE.

GNOME and KDE are desktop environments--kind of like complex "skins" for our operating system.  Right now, you have two of the same operating system, each with a different skin.  However, you can just as easily have only one operating system installed and have it use both skins.  (Similarly, in Windows you would only have one program and choose which skin you wanted to use on a particular day--you wouldn't have 5 versions installed, one for each skin.)

Now, from my (limited) knowledge, there doesn't seem to be any problem with having a duplicate of Ubuntu (albeit with a different skin) on your hard drive.  However, it would save a lot of space if you just use one install of Ubuntu and added on the second skin.  At the link below you'll find the directions (and they are very simple) to add KDE to your GNOME desktop.  Then you'll have more or less the same thing you do now, but in half the space!  You can select whether you'd like to use GNOME or KDE when you log in.

Installing KDE: [http://psychocats.net/ubuntu/kde.html](http://psychocats.net/ubuntu/kde.html)

---

### Post by abu-fatu on 2006-07-04
thank you. how would i remove kubuntu from hd2 and reformat it to use the free space as extra storage i can access from ubuntu in hd1?

---

### Post by cotcot on 2006-07-04
Make sure that the boot loader does not use the menu.lst from /hd2/boot/grub.  This depends on which one you installed last. Probably Kubuntu on hd2, so grub will most likely use the lenu.lst from Kubuntu hd2. 
If it is used from hd2 you need to do a grub-install from ubuntu on hd1. 
Then delete the hd2 and resize hd1. This can be done for instance with the Gparted LiveCD.

---

### Post by gingermark on 2006-07-04
If you run GNOME & KDE together you'll want [this](http://www.kde-apps.org/content/show.php?content=31031) - an extra "GNOME" entry for your K-Menu in KDE. Stops things getting cluttered.

The Debian package I linked to works great in Dapper.

---

