---
title: "Installer 'crashing' at partition manager"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by djhworld on 2006-08-14
Hello there, Now to cut things short, the installer on my Ubuntu CD seems to crash at 'manually edit partition table'. The partition manager sort of loads, but when it comes to 'scanning devices' (with the progress bar moving from side to side) it totally freezes the whole machine. The keyboard doesn't respond to turning caps lock on, which I usually deem to mean the whole computer has crashed.

When I booted the CD again, I executed gparted (manually) fine so I don't think that's the problem as such.

Anyway, to give you more details, I'm attempting to install Ubuntu on my SATA hard drive. It's already pre-partitioned (in a sort of sense) ready for Ubuntu, like this: -

[< ubuntu space> | <C:/ drive for Windows XP>]

So all I want to do is basically split the Ubuntu space to give a swap partition and boot partition (if you need it?)

Anyway, I can't access the Internet on the Ubuntu liveCD as I use a wireless USB stick and would probably need to configure it later on after installation. But this installer problem seems to be letting me down.

Was just wondering, is there anyway of just firing up the terminal and typing a few commands in to do a similar thing as the GUI? I'm an ex-gentoo user and would be happy with this sort of thing. 

I'm guessing the first reply I'll get will be about the 'alternative installer' but do I really need to download another 700mb or so just because of a buggy installation program?

Thanks.

---

### Post by ComplexNumber on 2006-08-14
it did that for me....about 7 times in a row. its a known bug. if you go straight through the partitioning process without pressing the Back button to make changes, it  won't crash.

you'll have to go back into the installer on the cd, resize your current ubuntu partion, and add the boot and the swap.

---

### Post by xpod on 2006-08-14
Yep.....You just might,I had the seme trouble over and over with Ubunto on another older (but to spec)pc..

Eventually i could only get the kbunto version on it(Alternate!)

Ps...aint it supposed to be the best idea to have XP at start of disk??

OR is that just us who dont know how to remedy the probs NOT having it at start apparently cause??

---

### Post by djhworld on 2006-08-15
Hi there, thanks for the replies.

I tried and tried again but the problem kept on occuring. 

In the end I just gave up and downloaded the alternate installation CD. Worked fine and had a working system within 15 minutes or so. 

However, annoyingly, GRUB decided to install itself on my second HDD, meaning I have to boot off that to load up Ubuntu or Windows on my other HDD. 

Ah well, now just to get my network going.

---

