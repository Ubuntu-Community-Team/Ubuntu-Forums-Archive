---
title: "windows 7 not opening after installing anything in ubuntu...HELP.!!"
date: 2011-07-14
forum: Any Other OS
---

### Post by abhishek39 on 2011-07-14
Used ubuntu 10.10 with xp in my old computer...and all worked fine..
bought a new PC..With pre installed windows 7. since it was an assembled one, thus no got no re-installation CD.
Downloaded ubuntu 11.4. and installed as it was in my old PC.
both worked fine until i installed flash player in ubuntu 11.4 through software center.after i installed flash player in ubuntu 11.4. windows 7 is not booting...When i switch my computer on it shows list of OS..>>ubuntu 11.4, mem. test...and windows 7(loader),
When choosing windows 7 it starts, shows its logo, then a black screen is displayed with the pointer for some time then a blue screen is displayed with many things written on it..and then the computer restarts...although it starts in safe mode..:(.
for assurance that it happened after installing flash player....
i re-installed ubuntu 11.4, and windows 7 successfully started..
again then i installed flash player and goggle chrome in ubuntu 11.4....
since then again windows 7 is not booting with same error(i mean windows logo...blue screen...black screen with pointer...again restarting) don't know what to do:(:confused:...plz help..:(

and both windows 7 and ubuntu 11.4 are 64bit.

---

### Post by ingeva on 2011-07-14
Losing boot in Windows because you installed flash in Ubuntu does not seem reasonable, but what's reasonable with windows?
My suggestion is: Drop it. You can access all its files from Linux, so what do you need it for?

---

### Post by mips on 2011-07-14
That is really weird. What you do in Ubuntu only makes changes on the ubuntu partition & not Win7 partition.

---

### Post by abhishek39 on 2011-07-14
but i don't know y everything went fine till i install flash player...and one thing more 
i have installed ubuntu with the option "install along with windows"...then a slider came to choose how much the memory to allot to windows and to ubuntu....:confused:
need help.

---

### Post by ingeva on 2011-07-14
> **abhishek39 said:**
> but i don't know y everything went fine till i install flash player...and one thing more 
i have installed ubuntu with the option "install along with windows"...then a slider came to choose how much the memory to allot to windows and to ubuntu....:confused:
need help.Well installing along with windows in the same partition makes the behaviour much more likely. I can't explain why it's happening, but I would advise you to install Ubuntu in a separate partition.
Windows 7 can reduce the partition size, so if you need to allocate more space for a new partition, use Windows to do it. I wouldn't trust Ubuntu's partition manager to do that perfectly with an NTFS partition.
You should allocate 6-10GB for Ubuntu, 2-4GB for swap, and as much as you need for user files. The system and GUI fit well within 6GB, but then you'll probably want to install a little more.
But I'll repeat what I said previously: What do you need windows for? Stupid games? (No, no smiley there).

Also be aware that the NTFS file system is VERY much slower and much more vulnerable than ext4 for Linux, so you'll be better off without it.

---

### Post by akand074 on 2011-07-14
It's not on the same partition, it's impossible to have Ubuntu on the same partition as Windows (unless you use Wubi which is not an actual install of Ubuntu). It's separate partition. Also, it's impossible that installing something in Ubuntu would effect Windows, the issue has nothing to do with Ubuntu. Also, you should make recovery disks in Windows which will bring your computer back to factory default state.

I'm considering that this may be a troll. But we'll see if that's true eventually.

---

### Post by ingeva on 2011-07-14
> **akand074 said:**
> It's not on the same partition, it's impossible to have Ubuntu on the same partition as Windows (unless you use Wubi which is not an actual install of Ubuntu). It's separate partition. Also, it's impossible that installing something in Ubuntu would effect Windows, the issue has nothing to do with Ubuntu. Also, you should make recovery disks in Windows which will bring your computer back to factory default state.

I'm considering that this may be a troll. But we'll see if that's true eventually.
OK, I must have misunderstood. Thought it might be something that I didn't know about.

I've been jumping to conclusions about cause and effect more times than I care to count.
This may be something of the sort.

I stand by everything else though!  :)

---

