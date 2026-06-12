---
title: "why are my .ko files so big in initrd? (custom kernel builds)"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by markjf on 2007-04-21
hi all,

recently set up on old machine to run ubuntu feisty fawn for the purpose of learning more about kernel building.

following the guildlines in here, i managed to get a default setup compiling, with nvidia restricted module (and ndiswrapper thrown in for good fun). i copied the config file from the default build and changed no options (i wanted a "clean" build).

my kernel boots fine, but the initrd file is massive compared to the default ubuntu build.

looking inside the initrd files, i notice that all the .ko files under lib/modules/2.6.xxxxx/kernel/ are much larger in my new compile. this is the only area where the initrd files differ in size.

e.g. the "drivers" subdir takes up 74mb instead of 9.5mb, "fs" subdir is 26mb instead of 2mb.
all the same files seem to be there, but are much bigger.

e.g. 3c59x.ko is 275k in my build, 61k in default build, ext2.ko is 1.3mb in mine, 78k in default.

i've run file on each pair and they both produce same "ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped"

why are my compiled versions so much bigger? and can i reduce them to get my ramdisk size down?

thanks,
mark

---

### Post by bbruing on 2007-09-16
I'm having the same issue, and I'm surprised that no one has responded to this question in so long!

My custom kernel images, though they work fine, have much larger initrd.img files. They're usually around six times the size of the official kernels. Since I have a seperate, small boot partition, this limits the number of kernels I can keep on the machine at any given time. I'm also worried that it might affect performance...

Will anyone reply to this? I'll post something in the "Packaging and compiling" forum as well.

---

### Post by markjf on 2007-09-16
i double posted this.
see here: [http://ubuntuforums.org/showthread.php?t=417138](http://ubuntuforums.org/showthread.php?t=417138)

it was an issue with debugging in kernel set on by default as i recall.

---

### Post by bbruing on 2007-09-17
**Thank you!** I wonder why I couldn't find it in the search, though I did stumble on this post...?

Anyway, I will try this out, though it sounds like it will do the trick.

---

