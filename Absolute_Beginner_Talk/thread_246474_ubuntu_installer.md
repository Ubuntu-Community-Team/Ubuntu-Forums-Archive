---
title: "ubuntu installer"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by hughlle on 2006-08-29
ok, go easy, never used ubuntu before and only ever dabbed into kubuntu once.

i booted up the latest iso and it was a live cd with the installer shortcut on desktop.

i went through it all just fine until i got to the harddrive partition page. here is my problem. i set it (well it set it and i just nodded and smiled) to resize a 60gb partition so that i would keep all of my windows stuff intact (can't afford to lose it) and to create a new partition in the newly created space. this all seemed well and such but once i clicked next i got the round sandtimer thing and its been like that for a couple of hours.

is the machine just resizing and such or has it broken (it has not progressed t another page like on kubuntu and i can still move the slider and chose different partition options but its stuck on the timer and i can't go forwards or backwards)

help!!!!

thanks, hugh

---

### Post by taurus on 2006-08-29
Perhaps you need to use the gparted from the LiveCD to resize your harddrive first before you run the installer!!!  And before you resize your harddrive, better run defrag from XP a few times...

---

### Post by justin whitaker on 2006-08-29
The installer is, um, buggy. I use the alternate CD because it gives you the original text installer, plus OEM and server options. Much more flexible, and not as buggy.

There is an option in the text installer to resize the partition. Since I'm an ex-slackware user, text installs do not scare me, but YMMV. 

Gparted is your friend if you want to use the live CD. 

Taurus is absolutely correct: if you want to keep XP, then defrag the heck out of it first, so that you don't accidently lose something.

---

### Post by whizbaby on 2006-08-29
If you knocked your ntfs partition-table (like I did for a friend's, following quite the same procedure as you) try to rescue it with 'testdisk',
that's what saved the data (and of course my teeth). I believe it should be in the latest knoppix release, otherwise copy it to floppy, cd, usbstick and start it from ubuntu live cd.
Then do what the others say, DEFRAGMENT and then resize and THEN install.(yes,for some the installer is buggy to a point not funny anymore)
good luck!

---

### Post by hughlle on 2006-08-29
ok, booted xp back up and used partition magic to creat a 12gb unpartitioned space, went into the gnome partition editor and created a 1gb swap drive and a 10gb ext3 drive (was default so i thought i'd leave it) and then during the installation i selected manually edit partition table as it wanted to format my entire drive and selected to reformat the ext3 and the swap and to leave the other 2 partitions, after that i got them mounted, with ext3 as "/" and the swap as "/swap" (i think) and then to mount the nfts ones as /hda/media or something.

hopefully this will work and it hasn't shouted at me yet so fingers crossed, i really hope i dont lose that windows partition.

will this allow me to dual boot or will i have to edit my GRUB loader (please say its simple ](*,) )

---

### Post by justin whitaker on 2006-08-29
> **hughlle said:**
> will this allow me to dual boot or will i have to edit my GRUB loader (please say its simple ](*,) )

Grub will find all other OSes on the system, and add them, first asking if this is correct.

---

### Post by hughlle on 2006-08-29
well it didsn't ask me anyhting but i'm now on my ubuntu shuttle with dual boot working just dandy so i'm very happy and impressed that i didn't kill anything (i have a very very bad karma :D)

---

### Post by justin whitaker on 2006-08-29
> **hughlle said:**
> well it didsn't ask me anyhting but i'm now on my ubuntu shuttle with dual boot working just dandy so i'm very happy and impressed that i didn't kill anything (i have a very very bad karma :D)

Like I said, I'm used to the text install, so it usually asks.

Congrats on, ummm, not messing anything up!:mrgreen:

---

### Post by bcollignon on 2006-09-10
I have given up on dual booting operating systems.  I tried it years ago with multiple versions of Windows in separate primary partitions and, sometimes months down the road, bugs reveal themselves eventually.  I was even running Fedora, Windows, OS/2 and DOS 6.22 together successfully for a while.  However, I firmly believe the best, most trouble-free, way to run any system is with one OS in command.  Get drive trays if you wish and slip them in and out.  Use CS which makes selecting master and slave, on most modern drives, very easy and truly portable.  I just installed Ubuntu 6.06 this way on a fresh drive and, so far, it's a beautiful system.  It seems inherently more stable than Windows; much like a Mac in some regards.  I'm sure bugs will crop up because -- and this is the never-ending truth of computing -- computers NEVER work the way they're supposed to all of the time.  I guess it must be fun, though or else I'd find another hobby.

---

