---
title: "Copying Data Before a Re-Install"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-08-20
ive been having problems GRUB starting up ubuntu so ive decided that im going to re-install ubuntu and hopefully that will take care of the GRUB problem as well.

naturally there are documents, pictures, and information on my computer that i want to save before i re-install and everything gets erased. i was just wondering how i can go about getting that data if i cant even start ubuntu.

ive booted up using a live cd but all the files are off limits to me because i dont have the permissions for the drive whenever i mount it. is there a way that i can become root on the live cd and copy all these files i need?

detailed instructions would be appreciated, ive been using linux for a while but im definitely still a newbie.

---

### Post by Hobo Joe on 2007-08-20
When you are in the liveCD, press ALT + F2, and it will give you a run prompt, type 'gksudo natuilus', that will give you a browser with root permissions.

---

### Post by Jimmyfj on 2007-08-20
I don't know is gksu nautilus can do the trick for you. And as far as I remember i once wrote root as password on the live for sudo su in a terminal

---

### Post by Shazaam on 2007-08-20
Have you tried reinstalling or updating grub? A reinstall of Ubuntu seems pretty extreme. Also you could try the SuperGrubDisk.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Hranj on 2007-08-20
thats the thing, ive been trying to use Super Grub Disk but its not working for me. i know exactly what i did wrong and so does that website but when it comes to actually doing it on my computer it doesnt work.

i edited my menu.lst file and now its all messed up.

[Fixing  It With SGD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#mistake_when_I_edited_my_menu.lst")

I follow the steps listed and i get to boot gnu/linux directly, i choose that and then go to something like boot directly again, i choose the connection, ide, and then i choose the partition but the problem is i dont know how to choose that partition. because on the screen it says press enter or right arrow key to boot selected partition. so how else am i supposed to boot it?

---

