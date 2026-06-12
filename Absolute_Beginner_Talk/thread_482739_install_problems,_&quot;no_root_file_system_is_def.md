---
title: "install problems, &quot;no root file system is defined&quot; and grub"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Rob-e on 2007-06-24
So after loving Ubuntu i talked my friend into it,  he has an acer, with 64 bit processor and Ubuntu 64 bit, fiesty, so when installing it i get to the partition step and i dont like the top 2 options (something like resize hda4 and use free space) and the second option is to use the full disc, so i choose manual (or something like that) and get to the shown screen and dont know what to do, i tried some stuff but get a "no root file system is defined" error, were going for a dual boot with windows with about 37 gigs in each partition, and the windows partition is on fat32

[[IMG]http://i19.photobucket.com/albums/b174/dsmlover99/th_ya.png[/IMG]](http://i19.photobucket.com/albums/b174/dsmlover99/ya.png)


this is the second time installing it, the first time grub didnt install and it boots right to windows, so i dont know whats going on

---

### Post by mcduck on 2007-06-24
You need to set one ext3 partition to mount in /.

---

### Post by solarswordsman on 2007-06-24
Your swap partition needs to be bigger as well.

---

### Post by Vodkayum on 2007-06-24
the drive ur installing linux to. where the mount option is type /
like the above poster stated / is like windows folder

---

### Post by Rob-e on 2007-06-24
> **mcduck said:**
> You need to set one ext3 partition to mount in /.
yeah, thats what it says at the bottom, i dont understand what that means, mainly whats "/"

> **solarswordsman said:**
> Your swap partition needs to be bigger as well.
o, yeah

> **Vodkayum said:**
> the drive ur installing linux to. where the mount option is type /
like the above poster stated / is like windows folder
i think you tried to explain what / is but it was over my head

thanks all for the fast replys, i do appreciate it

---

### Post by dhruva023 on 2007-06-24
here is the solution,

when you reach to that screen,  click on the partition on which you want to install ubuntu.
you will see button called, edit partition.
click on it.

**See Screenshot.png**
[IMG]http://server6.theimagehosting.com/image.php?img=Screenshot.2c6.png[/IMG]

than you will see something like this.
click on mount point.

**See Screenshot 1.png**
[IMG]http://server6.theimagehosting.com/image.php?img=Screenshot-1.c1e.png[/IMG]

then set it to this.

**see Screenshot 2.png**
[IMG]http://server6.theimagehosting.com/image.php?img=Screenshot-2.f5a.png[/IMG]

after that , click on ok,

it will set that partition to root partition.

and it called "/".

---

### Post by Rob-e on 2007-06-24
sweet, thanks, i wont be able to try this until wednesday though, to ill get back to this thread


p.s. nice arrows ;)

---

### Post by dhruva023 on 2007-06-24
> **Rob-e said:**
> sweet, thanks, i wont be able to try this until wednesday though, to ill get back to this thread


p.s. nice arrows ;)

don't make a joke. :D

i was in hurry !!!!  :popcorn:

---

### Post by Rob-e on 2007-06-28
woo woo, got it workin, now that i looked at it i undershatd what i was doing

anyway, turns out that he had a virus and it was bogging down windows, AND he never ever cleaned the fan out, so it kept overheating in windows and shutting off, and it was right when i installed ubuntu, (at least i hope it wasnt from me) yep, so thats funny, i deleated it and cleaned it, good as new

thanks again

---

