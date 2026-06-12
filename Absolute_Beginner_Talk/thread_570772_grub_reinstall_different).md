---
title: "grub reinstall different:)"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-10-08
Hello guys!
Somehow I always manage to have stupid problems.
I have two internal drives in my pc.
On both of theme there is my favorite OS, the Ubuntu:)
Now.
One of them has a kernel panic error. No problem, grub works just fine, so I can boot and run the other Ubuntu. I think I might have some problem with that kernel panic drive, because in the past I lost some folders from it... So, I do NOT want to solve the kernel panic problem, I just want to format it, and use it for movies/music etc.
But, if I'm not mistaken, after the format, the grub menu won't load, because that one was installed last. Am I right, or am I wrong?

I tried this: (from the running ubuntu)
grub> setup (hd0,
 Possible partitions are:
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,5)

Error 12: Invalid device requested

I'm not sure, but I think, that the current running ubuntu is at this partition, where I tried to install the grub loader.

Any suggestions will be greatly appreciated:)
Thanx

---

### Post by skymera on 2007-10-08
ok from live cd

:grub

:root (hd0,1)   <-- change to appropraite drive/partiton

:setup(hd0)  <--- again but not the partition.

---

### Post by duruttye on 2007-10-08
> **skymera said:**
> ok from live cd

:grub

:root (hd0,1)   <-- change to appropraite drive/partiton

:setup(hd0)  <--- again but not the partition.

Unfortunately I only have an Ubuntu 7.10 cd right here with me, the other is at my friend:)
Will that live cd install a different grub? or is it problem?

Thanx for the very quick reply :guitar:

---

### Post by skymera on 2007-10-08
oo ermm i dont know.

try it :)

or get Super Grub Disk :D

---

### Post by duruttye on 2007-10-08
> **skymera said:**
> oo ermm i dont know.

try it :)

or get Super Grub Disk :D

Hey, I tried it, and it didn't break my system:))
But it didn't do anything either:)

So, any ideas why it says:

Error 12: Invalid device requested
??

And thanx again for the second quick reply ;)

---

### Post by duruttye on 2007-10-08
My internet connection is slow, maybe I can fix this without downloading a whole disk:)

---

### Post by skymera on 2007-10-08
super grub :)

its like 3mb lol

you should make your filesystem EXT3 also :wink:

---

### Post by duruttye on 2007-10-08
> **skymera said:**
> super grub :)

its like 3mb lol

you should make your filesystem EXT3 also :wink:

Damn!
I thought it's a whole cd....

And in GParted, the filesystmes ARE ext 3:)

Let me try

---

### Post by skymera on 2007-10-08
sure

what partition is your system in stalled on?

---

### Post by ajgreeny on 2007-10-08
OK, try this.
Boot into the (k)ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.  If you don't have windows at all, then put grub on hd0, the first disk.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

It is just possible that the grub menu may still point to the wrong partition but that can be dealt with later if need be; let's just get a grub menu showing first

---

### Post by duruttye on 2007-10-08
Hey, ajgreeny, I already did that, with an Ubuntu 7.10 CD, but it didn't do anything.

But it looks like I managed to reinstall the grub bootloader where I want it to be with the super grub disk.

Thanx fo the replies!!
I will mark the thread solved, when I will format the other drive and start the system again!

---

### Post by ericartman on 2007-10-08
AJGreeny, thank you , I always click on any message involving grub as along with fstab I have a real problem getting my head around these ideas. Slowly the light is coming on. You can teach an old dog new tricks. Thanks again this grub info you posted has helped solidify a few thoughts that were forming in the mist.

Cart

---

### Post by duruttye on 2007-10-08
> **ericartman said:**
> AJGreeny, thank you , I always click on any message involving grub as along with fstab I have a real problem getting my head around these ideas. Slowly the light is coming on. You can teach an old dog new tricks. Thanks again this grub info you posted has helped solidify a few thoughts that were forming in the mist.

Cart

Yeah, just like you said:))

So, I really fixed the problem:)
Thank you all!
Another thing.
I really need to check if that hard drive is ok.
Badblocks didn't show anything, it just ended...
fsck message:

kucko@kucko:~$ sudo fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 11/5020064 files, 169797/10036600 blocks
kucko@kucko:~$ 

It does it in 1 (one) second. Is it normal on a 40 GB dirve?

I just want to check and be sure, before I put anything on it!
Should I open a new thread?

thank u all!

---

