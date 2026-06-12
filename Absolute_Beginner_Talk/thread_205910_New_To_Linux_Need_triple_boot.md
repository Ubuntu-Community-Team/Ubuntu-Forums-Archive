---
title: "New To Linux Need triple boot"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by DanWan on 2006-06-29
I am an old time MacUser. No understanding of Windows at all. My work forces me to use some XP ready made apps and I got a Vaio VGN T27 Laptop. The windows apps will only run native so I need an XP partition, however I want to use Unbuntu as my major sytem in this machine, and also to add a small partiotion for the MacOSX-86 (patched X 10.4.1) which runs not perfectly but well enough for me.

My questions:

1 - How to plan the different partitions? 
2 - I will use Windows only for two apps and store the data in an external Firewire or USB drive so I need little space (10 GB out of 100)
3 - for MacOSX-86 ab out 15 GB out of my 100 total should do
4 - Linux for most of the work.
5 - Is there a simple to choose how to start similar to Mac OS press the alt key during start-up?
6 - I will partition the XP in FAT32 and Mac as HFS+ but doing some basic tests I can't see anything but the Unbutu disks partition what can I do?

I am a new user I would truly appreceite anyone giving the simplest possible suggestions as I do not know much about programming at all.

Example I learned about GRUB could copy from the live CD
However I have no idea on how to do this .... 

Thanks really

:confused:

---

### Post by mark_g on 2006-06-29
You can Use the liveCD and start GParted. You can partition your hard drive just the way you want to with it.
Then install XP to the 10GB partition. Next MacOS and finally Ubuntu, which should normally detect that XP and OSX are installed, so Grub will show a menu to choose from everytime you start your PC.

You said:
"I can't see anything but the Unbuntu disks partition what can I do?"

Where can't you see the Ubuntu disk partitions, from the LiveCD?

---

