---
title: "Ubuntu 7.1 on Parallels 2.x (build 3188)"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by bcamp1973 on 2007-10-18
Has anyone had any luck installing Ubuntu 7.1 on Parallels build 3188?  I can't seem to get it to work :( on my Mac Mini

---

### Post by midtoad on 2007-10-20
I'm on Parallels 3.0 Build 5144 and I can't get it to install either.  Ubuntu keeps requesting a video resolution that OS X doesn't support, even after I ask it to install in VGA mode.

---

### Post by bcamp1973 on 2007-10-20
I finally got it to install...and booted once...but it won't boot anymore...just a blank screen...

The secret for me was to NOT use VGA but to select a resolution. I believe i selected 1280x...something.  About to give up...

BTW, i got it installed on 3.0...but as I said, it quit working...

---

### Post by DeathAxe on 2007-10-20
It doesn't work in Parallels 3 5160 for me as well. There's a discussion thread on the Parallels forums [http://forum.parallels.com/showthread.php?t=17069](http://forum.parallels.com/showthread.php?t=17069)

Works with VMWare Fusion though

---

### Post by dtrots on 2007-10-20
I couldn't get it to work either, same issues. But what I did do was clone my virtual machine and then I upgraded it through Ubuntu's software update engine located in the system/admin section. Took about an hour and a half. It is upgraded but will not enable enhanced dektop features presumably becasue of the video card driver. I still messing with that. I allowed Parallels to give it all 64m of video card but still doesn't work. I'm trying different drivers right now. Still feels like Parrallels will need a patch though.

---

### Post by Crusty on 2007-10-21
I got Ubuntu installed on Parallels 5160 by choosing the alternate text installer. Everything is running great except for screen resolutions. Only one works, and I have to go fullscreen with Parallels in order to see all of Ubuntu.

---

### Post by Ken T on 2007-10-24
Hi All,

When I upgraded to Feisty on my macbook (Parallels 2.5, build 3188), I found a thread somewhere on this forum or via google which worked. It entailed creating a new VM and calling it a Solaris OS rather than specifying the correct type of Linux kernel, going thru the install then changing the details in Parallels back to reflect a Linux kernel. It worked, with a few minor but irritating side-effects (like loading progress bars not displaying correctly, etc).

Now I don't know, but maybe that workaround would also apply to Gutsy as well?

K.

---

