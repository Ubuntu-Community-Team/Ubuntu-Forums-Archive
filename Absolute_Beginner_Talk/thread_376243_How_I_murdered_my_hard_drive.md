---
title: "How I murdered my hard drive:"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by cmillican on 2007-03-04
I have used Windows for my whole life, and I consider myself an advanced user. This was all fine, until I decided about a year ago how much I hate Windows. I resolved that one day I would make the switch, and today I tried it.

My goals were:

*to install Ubuntu 6.06
*to leave Windows XP on a different partition for the rest of my family and for playing games
*to not screw anything up doing the first two

All three failed.

I downloaded the Live CD from the site and burned it after mounting with DAEMON; no problems yet. I put it in, and, having messed around with the Live CD quite a bit about a month ago, I decided to just install and get it over with. I get to the partition part, and cut 3 GB off of my Windows partition and create a new one from it. It does it without any apparent error. It asks me a question about where to put the OS, and I realize I hadn't created space for swap, so I hit the back button a couple times. It has caution symbols next to the partition I edited and the new one, and I'm thinkin "Crap, I did it wrong." So I shut down the Live CD and try to boot with Windows, and it says it can't read the OS. *EXPLETIVE*

I'm writing this on the Live CD. Help.

---

### Post by steve101101 on 2007-03-04
I guess you went over your Windows XP partition. I would reinstall windows and then put ubuntu next to it. Also when you reinstall windows i would create a 512 mb swap partition and an empty partition for Ubuntu. Remeber to install windows on the windows section and then put Ubuntu on the Ubuntu section and it should work great.

---

### Post by bulldog on 2007-03-04
Hmmm,messing with your partitioner isn't a wise thing to do.
The best thing to do is download the GParted live cd and burn it to a cd-r.
Then boot from it and partition your drive at your likings.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
A warning though,3GB isn't much to install ubuntu,I should say,make it 5-10GB at least.

To try to restore your windows [can't promise it will do so]pop in the windows install disk and try to recover your existing install.
You can also try to do a new install on top of the existing windows to try to keep your data.

You can try to mount your windows partition with the live cd too,and try to save your data to another place.

---

### Post by cmillican on 2007-03-04
Yea, that's what I was thinking. The only problem is, I don't have the backup Windows discs, and I have no way to pirate one without an installed OS. I'm in a catch-22 of sorts: I can't install Windows because I don't have a copy, if I do a clean install of Ubuntu, I can download a Windows copy and keygen/crack and install it, but then I'll have to do a clean Windows install because I don't think XP lets you partition, or does it?

Either way, I'll have to wait for my dad to get home to ask him if there's anything important he didn't have backed up to our portable HD before I clean install anything  :( ...I'm sure he'll love that.

---

### Post by oilchangeguy on 2007-03-04
no matter if you do reinstall windows and set up a dual boot. or just go back and only install ubuntu, you do not have to manually create partitions for ubuntu to install on. it does a fine job by itself of creating the needed partitions. it seems to me that many people enjoy making extra work for themselves by doing un-needed manual partitioning. if your computer has to tap into swap/virtual memory to run, well then you've got a computer with problems. large swap partitions are not needed, otherwise ubuntu would automatically create large ones when it sets itself up. also don't get caught up in the command line mentality, it's not needed as much as many of the posts would have you belive. when's the last time you used a command line to get anything done in windows?

---

### Post by cmillican on 2007-03-04
So do you think it might work to try it again and let it do it automatically? Maybe I could get lucky or have God reach down and restore my hard drive back one hour.

---

### Post by oilchangeguy on 2007-03-04
make sure your computer is set to boot from the cd drive. put the ubuntu cd in, re-boot and follow the prompts, and let ubuntu do it's thing. and in about 20-30 min. you'll have a fine operating system on your computer. let it download and install all needed updates (hope you've got highspeed internet). then go to [www.getautomatix.com](www.getautomatix.com) and install this program. you'll find it will make installing software a breeze.

---

### Post by bulldog on 2007-03-04
If you re-install ubuntu,be sure you left enough space for your windows.
This should be the first partition on your disk!

Then make a swap 1GB and a / (root) partition 5-10GB at least and reinstall ubuntu.
The command line isn't a necessary tool,but it's a very powerful and useful way of getting things done.
Some people are scared of this terminal thingy,and that's alright,but learning some basic commands will show you how easy things can be.

---

### Post by cmillican on 2007-03-04
Yes, I have ~120 kB/s down, ~50 kB/s up.

Well, I think I'll just do a clean install of Ubuntu like you just said...maybe I'll download Windows and install it later, but for now, I think I'll pull a sink-or-swim on Ubuntu...probably learn quite a bit very quickly doing it this way.

---

### Post by haley1 on 2007-03-04
Try to re-load it and let it create the partitions, it should automaticaly make a swap partition and it your window partition is still on there it may recognize it and you should be able to boot into it. In any case it's probably faster to try this first than reloading Windows then ubuntu. I just loaded it on a friends laptop and it took about 20 minutes.

---

### Post by cmillican on 2007-03-04
Ok, thanks for all of y'all's help. I'll try installing it again.

---

### Post by cmillican on 2007-03-04
Ok guys. I just did a clean install, and it's working fine. I had all of MY stuff backed up, but I'm hoping my dad won't cry over having to get used to Ubuntu or over files he lost. Thanks for all of your help.

---

### Post by oilchangeguy on 2007-03-04
glad to hear it worked. now enjoy the freedom of opensource software!

---

