---
title: "MacBook 4.1 Fail"
date: 2010-07-23
forum: Apple Hardware Users
---

### Post by brooklynite on 2010-07-23
I just tried installing Ubuntu 10.04 as a dual boot with OS X on my MacBook version 4.1 following the instructions here: [http://fosswire.com/post/2009/03/how-to-ubuntu-810-on-white-macbook/](http://fosswire.com/post/2009/03/how-to-ubuntu-810-on-white-macbook/).  I figured it would be pretty much the same, and it was.  But when I try to boot into Ubuntu, all I get is the reFit display of Tux and then it just sits there and won't boot into Ubuntu.

The biggest difference between what I did and what was recommended for Ubuntu 8.10 is that there was no option for installing Grub in the last step under the Advanced tab.  It just asked me if I wanted to install the bootloader and that was it. I assume that's the same as Grub, but maybe that's a bad assumption.  Also, after I ended my install and decided to restart the system, the Ubuntu Live CD ejected and my screen filled up with a bunch of error messages .  I then had to do a hard restart, and now Ubuntu won't boot.

 Is there anything I can do to fix this or do I have to wipe my whole drive and reload OS X and try Ubuntu again?  Any help would be much appreciated.

---

### Post by zeroti on 2010-07-23
Is your OS X partition still booting? if so, you shouldn't need to wipe it.

Maybe try finding a newer guide and trying with the install CD once more. You'll prob. need to choose to erase the old Ubuntu partition. As a disclaimer, I don't know anything about how to set-up dual booting, so maybe there's some special extra beginning partition you need to make that I don't know about.

---

### Post by brooklynite on 2010-07-23
I just checked the partitions tool in reFIT and it says my partitions overlap.

---

### Post by brooklynite on 2010-07-23
Yep, my OS X is just fine. I'll give your suggestion a try about just wiping the old Linux and trying again.

---

### Post by v41 on 2010-07-24
I wonder whether grub got installed to the MBR rather than to the Lucid partition?  To determine whether this has happened,  see point (iv) in the following link, [http://ubuntuforums.org/showpost.php?p=7477957&postcount=16](http://ubuntuforums.org/showpost.php?p=7477957&postcount=16)

---

### Post by brooklynite on 2010-07-26
Thanks for the suggestions everyone.  In the end, it was getting too complicated. So I wiped my drive and started from scratch following these instructions: [http://ubuntuforums.org/showthread.php?t=1387861](http://ubuntuforums.org/showthread.php?t=1387861).  The only hitch I ran into was that I had to do PRAM/NVRAM and SMC resets at one point, I wish I could remember what it solved but I can't right now.  Regardless, the resets were ridiculously simple processes so it wasn't much of a hitch. 

Overall, it was actually pretty painless doing it this way, and Time Machine did its job so I didn't lose anything on the OS X side. Looking back, I think you were right v41, the grub was installed to the Master Boot Record instead of to the Ubuntu partition. 

Anyway, now I have a very nice little triple boot Macbook running Snow Leopard, Windows 7 and Lucid Lynx.  This is my first significant experience with Ubuntu, and I have to say that once I got it installed, wow! "It just works" is an understatement.  Adding drivers and doing system tweaks has never been so seamless.

Thank you again for your suggestions v41 and zeroti. 

-Brooklynite

---

