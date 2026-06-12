---
title: "Don't be scared of 64 bit!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-06-12
After playing around with feisty 32 bit for a week, I installed the 64 bit version today. It really did "work out of the box"! No problems at all. If you're not sure whether to give it a go, I found it less problematic on my PC than the 32 bit version. I'm well impressed with it! Perhaps I was lucky. I just have two questions (please be gentle with me, I'm a complete newbie). I know it sounds really silly, but how do you format a floppy disk? I can't find anything, anywhere, apart from running a command in terminal. Also, how do I remove previous kernels from the Grub menu at startup?

---

### Post by earobinson on 2007-06-12
after you have uninstalled the previous kernel with synaptic you will be able to edit your ~/boot/menu/sources.list (sudo gedit <file name>) and remove the old entries.

---

### Post by Yasumoto on 2007-06-12
This seems like the problem with flopy disks:

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/107843](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/107843)

(gfloppy isn't in feisty)

It seems that you can rebuild gnome-utils with --enable-gfloppy=yes (thanks Holger Bauer) or use the command line.

---

### Post by Wynne G Oldman on 2007-06-12
> **earobinson said:**
> after you have uninstalled the previous kernel with synaptic you will be able to edit your ~/boot/menu/sources.list (sudo gedit <file name>) and remove the old entries.I'm sorry, I don't understand. How do I do both of these things? I've only been using Linux for a week!

---

### Post by guysmiley25 on 2007-06-12
How do you go about uninstalling the previous kernel?

What package need to be removed? 

eg anything that contains the name 2.6.20-15-generic or just 2.6.20-15

aptitude search "~i" | grep 2.6.20-15-generic
```

i   linux-headers-2.6.20-15-generic - Linux kernel headers for version 2.6.20 on
i   linux-image-2.6.20-15-generic   - Linux kernel image for version 2.6.20 on x

```

aptitude search "~i" | grep 2.6.20-15
```

i   linux-headers-2.6.20-15         - Header files related to Linux kernel versi
i   linux-headers-2.6.20-15-generic - Linux kernel headers for version 2.6.20 on
i   linux-image-2.6.20-15-generic   - Linux kernel image for version 2.6.20 on x

```

Thanks

---

### Post by mikewhatever on 2007-06-12
> **Wynne G Oldman said:**
> After playing around with feisty 32 bit for a week, I installed the 64 bit version today. It really did "work out of the box"! No problems at all. If you're not sure whether to give it a go, I found it less problematic on my PC than the 32 bit version. I'm well impressed with it! Perhaps I was lucky. I just have two questions (please be gentle with me, I'm a complete newbie). I know it sounds really silly, but how do you format a floppy disk? I can't find anything, anywhere, apart from running a command in terminal. Also, how do I remove previous kernels from the Grub menu at startup?

Hm.., I would have waited at least a week to make sure everything works 'out of the box'. Your excitement is misleading and groundless. How could you have found it less problematic, if you had no chance to use it yet.

Anyway, good luck.

---

### Post by tribaal on 2007-06-12
You can safely remove "linux-image-2.6.20-15-generic", IF you are SURE it's the kernel version you don't need anymore. Normally the two other packages should be removed with it automagically (they both depend on the former).

If you're not sure about this I suggest you leave it as is (it'll waste around 30mb of your disk which I'm pretty sure you can live without for a while). In any case, you should probably backup your valuable files before messing with the kernel if you don't feel confident.
And backups are generally a good thing to have :)

Hope this helps :)

- trib'

---

### Post by Wynne G Oldman on 2007-06-14
> **mikewhatever said:**
> Hm.., I would have waited at least a week to make sure everything works 'out of the box'. Your excitement is misleading and groundless. How could you have found it less problematic, if you had no chance to use it yet.

Anyway, good luck.What I meant was that everything's working as it should do, and I found it no harder to set up than the 32 bit version, so if you're worried that it will be more difficult to install, don't be. With the 32 bit version, I had problems with the 3D driver (cube kept stopping working for no apparent reason) and I couldn't write anything to my DVDRW drive. Everything works with the 64 bit version. It feels quicker and more stable as well. I'm still impressed . I've also found something you can't do in XP. Write directly to a DVD without any add on software. As a newbie, I found both versions incredibly easy to set up, once I got some help from this excellent forum. Ubuntu is definately the most user friendly version of Linux to newbies I've tried so far. Thank's everyone:D

---

### Post by SomethingCronic on 2007-06-14
I think you've jumped the gun a bit. You're using 64bit Ubuntu but have only used it for a week.

When you come across a flash website, you might be upset to find you have to do a lot of digging to get it to work, or you may look across the ubuntuforums, find something cool like beryl, and then find you can't use it because your 64 bit. (beryl was just an example of something cool, I have no idea if it works with 64bit OS)

---

### Post by fastpakr on 2007-06-14
> **SomethingCronic said:**
> I think you've jumped the gun a bit. You're using 64bit Ubuntu but have only used it for a week.

When you come across a flash website, you might be upset to find you have to do a lot of digging to get it to work, or you may look across the ubuntuforums, find something cool like beryl, and then find you can't use it because your 64 bit. (beryl was just an example of something cool, I have no idea if it works with 64bit OS)

Glad it was just an example, because Beryl works just fine on 64 bit.  There are a FEW things that require some digging into the forums to get working, but they CAN be resolved.  People are far too hasty to condemn 64 bit when it's really not difficult for even beginners to work with, as long as they're a little patient and resourceful.

---

### Post by Wynne G Oldman on 2007-06-14
> **SomethingCronic said:**
> I think you've jumped the gun a bit. You're using 64bit Ubuntu but have only used it for a week.

When you come across a flash website, you might be upset to find you have to do a lot of digging to get it to work, or you may look across the ubuntuforums, find something cool like beryl, and then find you can't use it because your 64 bit. (beryl was just an example of something cool, I have no idea if it works with 64bit OS)You're right, I'm sure that some things won't work with 64 bit, but this applys to Windows too. There's not that much less than the 32 bit version though. If you install Automatix, it allows you to download a 32 bit version of Firefox (Swiftfox) which allows you to run Flash.

---

