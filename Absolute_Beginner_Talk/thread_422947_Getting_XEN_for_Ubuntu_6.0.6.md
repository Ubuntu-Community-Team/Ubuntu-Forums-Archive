---
title: "Getting XEN for Ubuntu 6.0.6"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-25
Hello:

I would like to install XEN on Ubuntu 6.0.6. I heard that this is a program that will allow you to run Windows while still in Ubuntu, which would perfect for me.  If I can get XEN to work then maybe I can get rid of dual boot, but still keep Windows (sorry there are programs on Windows I really want to keep and haven't been able to get to work right using WINE).  I see XEN  is included with Ubuntu 6.10. Is there a way to install it in 6.0.6? Should I upgrade to 6.10? I hope that all made sense. Thanks.

---

### Post by oilchangeguy on 2007-04-25
go to [www.xensource.com/download](www.xensource.com/download)
this is not a free program. what's wrong with the dual boot setup? using a virtual machine you only get a limited amount of ram and hard drive space allocated for it. and this can cause your os to not perform as it would normally.

---

### Post by orwellus on 2007-04-25
Thanks for the reply. I just thought it might be easier to run everything from the same o/s instead of switching back and forth. I'm still new to the whole Ubuntu experience (since Friday). The switch has had it's ups and downs, on one hand I really like some of the programs in ubuntu, on the other hand programs that I like and use on Windows (such as Word and my excellent paint program Project Dogwaffle) don't work very well on Ubuntu, and the alternative such as Open Office Writer and Gimp leave something to be desired (especially GIMP). I like that there are packages already complied for you in Ubuntu, but trying to figure some of the commands to make them work has been a hassel. Thanks for all the help though, I think you posted on the question I had about upgrading to 7.0.4 (which I have decided against after reading some of the comments). So dual boot would be better. What about if I spent some $ and got crossover office would that be better?

---

### Post by oilchangeguy on 2007-04-25
crossoveroffice will allow you to run some software designed for windows. but it won't run the os. the best thing you can do is setup a dual boot on two hard drives. that way if one crashes you'll still be able to use the computer. i use a 30gb drive for ubuntu, and a 10gb drive for xp pro. i rarely boot into windows, mainly just to keep the anti-virus and anti-spyware programs updated, and also to make sure windows itself is updated aswell.

---

### Post by orwellus on 2007-04-25
Oh so it's kinda like WINE then. Hum, not sure about that then. Word didn't work very well when I tried it in WINE.

---

### Post by orwellus on 2007-04-25
Dual boot might be best then. I have 18GB on the computer, and that is pretty evenly split between the two O/S.  Ubuntu is partitioned for about 10GB and Windows about 8. Thought I might give Ubuntu a little more, if I use it more. Another concern I had with dual boot is running out of space for the on the either O/S. Ubuntu seems to take more up more room than windows. That's why I was trying to get some of the Windows programs to work on Ubuntu and just have one o/s. I don't know seems kinda a hassel though, and I still do use Windows quite often. But I have Windows 98, and that is slowly being fazed out. And there is no way I'm spending $200 on an upgrade to XP or Vista.

---

### Post by oilchangeguy on 2007-04-25
18gb is a tight squeeze with two os's on it. check with some local computer stores to see if they have any used hard drives for sale. stay around 40gb and you should be able to get one cheap. then use the second drive to load ubuntu on. mine are set as ubuntu on master, and xp on slave. format the 18gb and do a clean install of windows.

---

### Post by orwellus on 2007-04-25
That's a pretty good idea. If they are around $50 or $100 that might be an option. Thank you.

---

### Post by oilchangeguy on 2007-04-25
if you do go that route, reinstall the operating systems on each hard drive by doing one at a time. set the jumpers to master, install ubuntu on a drive, leave the jumpers as master. unplug the drive. install the second drive, set the jumpers as master, install windows. then set the jumpers on the windows drive to slave. reattach all cables to the first drive, and reboot. grub should then give you the option to boot into either os.

---

