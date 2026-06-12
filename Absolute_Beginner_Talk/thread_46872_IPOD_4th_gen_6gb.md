---
title: "IPOD 4th gen 6gb"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by AlexDe on 2005-07-06
Okay first off I've tried to search many threads regarding IPOD's on these forums, google, you name it i've looked. (Or have attempted) 

My problem is when I plug it in.. it auto detects it.. I can browse the dir's but theres nothing in it (Music, Itunes.db, etc..) but indeed they are considering I can play them. Im assuming it has to do with how it's formatted? It's a Windows formatted one so I was under the impression it was FAT filesystem. Anywho any help would be appreciated, thanks.


-Cody

---

### Post by sonny on 2005-07-06
Perhaps it's something simple, have you tried the option "show hidden files"?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=AlexDe]Okay first off I've tried to search many threads regarding IPOD's on these forums, google, you name it i've looked. (Or have attempted) 

My problem is when I plug it in.. it auto detects it.. I can browse the dir's but theres nothing in it (Music, Itunes.db, etc..) but indeed they are considering I can play them. Im assuming it has to do with how it's formatted? It's a Windows formatted one so I was under the impression it was FAT filesystem. Anywho any help would be appreciated, thanks.


-Cody[/QUOTE]

What you want is gtkpod.

> sudo apt-get install gtkpod

Tell it in its preferences to mount the iPod and it workd great after a reboot.

---

### Post by AlexDe on 2005-07-06
Haha,

Yes i've tried to view hidden files, and yes GTKPOD cannot read the iTunes.db either because it cannot find it either. Any other ideas? 


-Cody

---

### Post by AlexDe on 2005-07-07
**BUMP**

Sorry I hate when people  bump their posts.. but i've tried to be patient.. if it's against rules sorry and can remove.

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=AlexDe]Haha,

Yes i've tried to view hidden files, and yes GTKPOD cannot read the iTunes.db either because it cannot find it either. Any other ideas? 


-Cody[/QUOTE]

When you plug in IPod it does mount corrrect?

---

### Post by AlexDe on 2005-07-07
It pops up in /media/IPOD but not in /mnt/*

I tried editing fstab.. but im pretty new so probably did it wrong.. (erased it by now though)

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=AlexDe]It pops up in /media/IPOD but not in /mnt/*

I tried editing fstab.. but im pretty new so probably did it wrong.. (erased it by now though)[/QUOTE]

You should leave fstab alone. THe thing to do is open gtkpod, go to "edit, edit preferences" then type in /media/IPOD where it says "mount point" then click the heck box that says "handle mounting of ipod" and "import db on startup"

then close gtkpod and restart it.

---

### Post by AlexDe on 2005-07-07
Yep, when I said i've read.. I have. Im not the type to just ask when there is plenty of documented posts and whatnot on it. The point is it cannot find the iTunes.db on the ipod itself. When I try to view it the music and all the itunes files are missing. (YES I'VE CHECKED HIDDEN) 

Sorry if that was a bit.. un clear.. bit tired and going to bed.. i'll check back in the morning. Thanks for helping!


-Cody

---

### Post by not_yet on 2005-07-07
Yep, when I said i've read.. I have. Im not the type to just ask when there is plenty of documented posts and whatnot on it. The point is it cannot find the iTunes.db on the ipod itself. When I try to view it the music and all the itunes files are missing> Yep, when I said i've read.. I have. Im not the type to just ask when there is plenty of documented posts and whatnot on it. The point is it cannot find the iTunes.db on the ipod itself. When I try to view it the music and all the itunes files are missing 

if when you disconnect your ipod, and you don't see anything under "music", its probably because the file system on the pod has gotten scrambled. :???: 

sorry  afik there is no solution to this , other than re-format the ipod

go to the apple site, and get the lateset updater for your ipod

one of the sections within the updater will reset your ipod to its original condition

**this is not the same as a reset on the ipod

you are basically starting with a clean ipod

hope that helps

---

### Post by AlexDe on 2005-07-07
Ugh, stupid mistake by me. (always end in that way huh?) No the files were fine themselves, that is why it was so frusterating... While I was reading around.. apparently when editing the fstab you need to shutdown / start instead of restart? I tried it and works fine now.

---

### Post by not_yet on 2005-07-07
just a heads up for you..............

I have been using gtkpod with an ipod mini

I had all my music erased,  I'm still not sure why?

I suspect it may have something to do with not being able to disconnect  in a way that the ipod is happy with??

I have tried to eject manually, but dosen't seem to work

still researching :)

---

### Post by AlexDe on 2005-07-08
Im not using gtkpod, using gnupod ;).. but I believe when I was checking out preferances in gtkpod there was an option to "delete songs not on harddrive" or something similiar.. maybe you had that checked?

---

