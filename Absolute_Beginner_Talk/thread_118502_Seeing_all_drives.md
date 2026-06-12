---
title: "Seeing all drives?"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by seakiwi on 2006-01-17
I'm never sure which is the best forum to post my questions in so feel free to move this to the appropriate one.

I'm running Ubuntu and just installed the Kubuntu desktop package - guess that means I'm now running **Ku**buntu  ;-)

Anyway, under Gnome I could see my Windows drive - two partitions. They automatically appeared on the desktop during installation. I was able to see my Windows workgroup and one workgroup machine. Not sure why I couldn't see the host machine but I wasn't too worried about that yet.

Under KDE - although I can see all drives and partitions from the Disks Manager, I can't see anything under Storage Media other than my floppy drive, and I can't seem to find a way to see my Windows workgroup. 

How can I make these visible under Storage Media so that I can make a shortcut to them?  I really need to be able to see my Workgroup machines.

TIA!

---

### Post by My8os on 2006-01-17
I thing that in storage media appear only the drives that are mounted.
Try mounting your windows partitions and check again.
If you dont know how to mount them, check out [this](http://www.tuxfiles.org/linuxhelp/mounting.html) and [this](http://www.tuxfiles.org/linuxhelp/fstab.html).

---

### Post by shania98 on 2006-01-17
[QUOTE=My8os]I thing that in storage media appear only the drives that are mounted.
Try mounting your windows partitions and check again.
If you dont know how to mount them, check out [this](http://www.tuxfiles.org/linuxhelp/mounting.html) and [this](http://www.tuxfiles.org/linuxhelp/fstab.html).[/QUOTE]
hi quick question, just loaded ubuntu & need help on bios setup. I have 2 drive, floppy & 2 cdroms I believe i have ubuntu on 1st drive & still plan to setup win on 2nd drive need info on bios setup. I had cdrom as my 1st drive to load & ubuntu loads okay but when i set to drive one it gives me error # 15 wait for grub? thank for any help, a newb

---

### Post by Mustard on 2006-01-17
[QUOTE=shania98]hi quick question, just loaded ubuntu & need help on bios setup. I have 2 drive, floppy & 2 cdroms I believe i have ubuntu on 1st drive & still plan to setup win on 2nd drive need info on bios setup. I had cdrom as my 1st drive to load & ubuntu loads okay but when i set to drive one it gives me error # 15 wait for grub? thank for any help, a newb[/QUOTE]

Grub may well be setup on the second drive that you are going to install windows on. I suppose it depends on which one is setup to boot. I would mention that when you install windows, its going to destroy grub, so you are going to do some mucking around to get Ubuntu working again after installing windows.  It would be best to install windows first, then install Ubuntu second.

-edit-

It would be best to start your own thread on this question too, as its considered bad etiquette to ask new questions in someone elses thread. :)

---

### Post by cotcot on 2006-01-17
See also this [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

