---
title: "Can't boot into ubuntu after installing"
date: 2008-04-17
forum: Apple Intel Users
---

### Post by Gornik on 2008-04-17
I partitioned my hard drive, I installed ubuntu, my problem is that ubuntu does not boot.  My macbook automatically loads OS X and does not give me the option to load ubuntu.  What did I do wrong?

---

### Post by salvat0r on 2008-04-17
Do you mean it's auto boot into OS X only? Perhaps, you may want to describe on what's the error message?:lolflag: I m learning also.. hehe

---

### Post by Gornik on 2008-04-17
yeah it auto boots into OS X only?  I need help

---

### Post by kimara on 2008-04-17
Hi!

Have you installed [rEFIt]("http://refit.sourceforge.net/"), it's a boot loader for mac, after installing you can choose which OS to boot.

---

### Post by plasmatonic on 2008-04-17
You don't necessarily need rEFIt. You can simply hold down the option (not command) key when you power on until you are presented with your bootable options.

---

### Post by guj4_n3b3sk4 on 2008-04-17
> **Gornik said:**
> I partitioned my hard drive, I installed ubuntu, my problem is that ubuntu does not boot.  My macbook automatically loads OS X and does not give me the option to load ubuntu.  What did I do wrong?

Hello, Gornik.

Yesterday I have established Ubuntu 7.10 for 64-bit architecture on Macbook. If you have problems still, here's the way I solved that problem:

1. Do a backup of files in case you haven't done that already.
2. Insert OS X Install DVD1 into drive, hold C while booting and boot DVD.
3. Go to Disk Utility, and divide entire disc into 2 partitions - 1. partitions should be Journal, that is going to be Mac's partitions, and the rest should be free space.
4. Click partition, reboot, and boot that same DVD1 again.
5. Follow OS X instalation guide and install OS X on partition mentioned for that OS.
6. Go online and download rEFIt 0,10 - although coleague from above says you don't need it, it's pretty useful thing.
7. Install rEFIt, get Ubuntu Install CD in drive, reboot, hold C, and boot Ubuntu.
8. I suppose you know how to install Ubuntu, here's only thing I've done with partitions: I made 1024MB space for swap, and rest ext3 mounted as '/' (all made out of that free space I made with Disk Utility). *I've found if there's more than one partition made for Linux needs on Macbook, it'll cause some problems, but with swap and / partitions everything works just fine.
9. Reboot, and that's the end.

When you reboot, rEFIt window will pop up and ask you which OS you want to boot. Select the one you want and enjoy.

I did this because I didn't want to delete OS X, because it's a good Unix OS and I want to explore it. Of course, if you want only Ubuntu on Macbook, make all free size partition, and rest of tutorial is the same.

Hope I've helped.

Send us a post to see have you managed to install Ubuntu on Macbook.

---

