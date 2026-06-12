---
title: "Dual Boot went down the drain..."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by urbanfractal on 2008-04-21
Greetings!

Perhaps this is mentioned before so please instead of hitting me with a stick, guide me to the appropriate thread, if there is one! Thanks!

I used to have Vista, then downloaded hardy herod 8.04 beta. Vista were in my IDE drive, recognized as IDE port 4 by my BIOS

I installed Ubuntu via the cd offered online on my SATA drive (recognized as IDE 0), creating all the necessary partitions. 

Then, if I can recollect correctly, I was able to dual-boot normally. But, nooooo, I wasn't satisfied with that so I thought I could mess it up :>

I went on and *tried* to install a copy of WindozeXP after formating the Vista Partition, as per usual with Windoze-boot-cd's setup.

So now, in gParted I have 2 hds, hda & hdb.
hda[IDE]: 8MB unpartitioned, 24 GB Partition 2 (XP in there) [NTFS], 161 GB Partition 3 (personal Files in there) [NTFS], 8MB unpartitioned

hdb[SATA]: 125GB Personal Files [NTFS], 3 Linux Partitions (home, file system, swap) [ext2 & 3], 8MB Unpartitioned.

Only linux main partition is flagged as boot, ALL of the rest are blank.

BUT! Although I tried and edited the menu.lst, I can boot ubuntu smoothly (as expected) but the system hangs when I try to boot  Windoze (IDE hdd). I even tried after unplugging my SATA-ubuntu drive, but to no avail; system hangs as well and hdd led on case stays always on and no 'working' sound of comes from IDE hdd.

Any Ideas as to how can I make it work?

---

### Post by bumanie on 2008-04-21
Y^ou could try easybcd bootloader from neosmart. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) It can be done with grub also by chainloading both windows look[ here]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_") for instructions

---

### Post by urbanfractal on 2008-04-21
Thanks for the quick reply, but perhaps I was not too clear about my windoze version :p

I no longer have Vista. I re-formated the whole win partition and Installed XP SP3 *instead of* Vista. My XP Boot crashes/hangs but ubuntu still works fine. Just tried with other Windoze edition and still the same result.

I wil try the GRUB Guide, I hope it works!

---

### Post by bumanie on 2008-04-21
Did you install xp before or after ubuntu?

---

### Post by urbanfractal on 2008-04-21
First Vista on their own. then Vista + Herod (working fine),  then Del vista and install XP, so now it is XP + Herod.
so I guess first ubuntu, then windoze, with comlpications :>

Reeeeally messy :>

---

### Post by bumanie on 2008-04-21
It is easier to have windows first, then grub will 'see' it when ubuntu is being installed. I am writing another reply that instructs how to fix windows mbr and reinstall grub. With xp installed second you will probably have to edit your /boot/grub/menu.lst as well. If you have nothing saved, it may be easier to reinstall windows first and ubuntu second. I can post the guide I've almost finished, but as I say, you will most probably have to edit your /boot/grub/menu.lst with drive maps, which usually works. I will finish my guide and you can decide which way to go and post back.

---

### Post by urbanfractal on 2008-04-21
thanks a million, I eagerly await thy wisdom!

---

### Post by bumanie on 2008-04-21
I'll just add the bit about the drive maps. It's on that grub guide I referred earlier anyway. Won't be long and hope that I am wise enough and that everything I have written works as it should - use at your own risk. Computers are not always friendly -as I am sure you know.

---

### Post by urbanfractal on 2008-04-21
the answer is... 42

---

### Post by bumanie on 2008-04-21
Is xp on your primary or secondary drive? ie, hda or hdb?

---

### Post by bumanie on 2008-04-21
You're right, I wasn't clear on that. I thought you needed triple booting!
In that case, as you have an xp disk, you should be able to fix the mbr through recovery console. But that will also mean that you will have to reinstall later from the ubuntu live cd.
**To fix windows**, boot with xp cd. (IF I remember correctly) you click that you want to install, but at the next screen you are given a choice of installing or going into recovery console, by typing R. In recovery console you will be asked for administrator password and then you have to choose the windows to repair, as it's the only one you should have to type 1. You then type FIXBOOT --> enter; Then type FIXMBR --> enter Answer y(yes) to any queries/ comments. Then type exit. Windows should now boot.
**Now to reinstall grub.** boot into live cd. Open terminal and type > sudo grub --> enter then type>  find /boot/grub/stage1
 You will get an output of something like (hd0,1) [substitute the numbers you obtain from the output] then type > root (hd0,1) --> enter then > setup (hd0) [Or the first number you get after (hd?)]--> enter > quit -->enter Reboot.
Ubuntu should now offer to boot xp or ubuntu.
This should work if xp is on the first disk, although I note you have mixture of ide and sata, that sometimes confuses gub. See herman's grub page for more details.

---

### Post by urbanfractal on 2008-04-21
sorry, I was away for a while.

It is on the IDE drive. Since I have a SATA the XP drive is recognized as IDE4 (sata=IDE0) and is a Master (so I guess secondary master).

GParted-wise it's in /dev/sdb5(which is sub-partition or something of /dev/sdb1) while ubuntu is on /dev/sda2, 3, 4

I hope I covered it :p

---

### Post by bumanie on 2008-04-21
Sorry I posted before you got back. Unfortunately what I have written is for if xp is on first disk, however you can still fix the xp mbr. You can try to install grub, but you may  need the grub map I mentioned earlier to get ubuntu and xp to boot properly. Up to you whether you try or wait for someone else's idea. I try these things myself and don't worry too much if I muck things up, but I don't like mucking other people's computers up - I initially thought xp was the primary drive.

---

### Post by urbanfractal on 2008-04-21
Don't worry mate! 

All this is more than I had in the beginning so I will give it a try, I won't blame you if something goes wrong. I'll blame Canada... no really it's Billl G*t*s' fault!

Anyways, one thing I wanted to ask as well is:

If I completely remove each and all OS from my drives and then start again the order I understand should be XP then Linu, right?

Does it actually matter, speedwise I mean, if I have ubuntu in the SATA (=faster-than-IDE) disk?

Thanks a million!

PS I really hope I am not keeping you awake at any strange hour, here in Greece it's only 18:00 :p

---

### Post by bumanie on 2008-04-21
Here in Australia, it's 1:15 am. It is better to have xp on the 'primary' drive. As far as which to have as the primary, I'm not sure it matters, but you're right that sata is quicker than ide. As I said, apparently mixed ide and sata drives can in themselves cause grub problems, I read that on Herman's site (grub page art hermanszone...), but can't remember the exact details as I've never 'mixed' drives so haven't had to worry. Really, if you haven't got anything valuable on the drives, I would start from scratch and install xp first, it generally is easier done that way. However, as linux/unix is modular, it is much more flexible to configure than some other monolithic OSes I can think of - but I'd choose the easier option if I were doing it. Any way the other instructions are probably worth keeping in case something goes wrong after you've installed again (xp first) - computers have tendency to muck up at times - linux much less often than some others.

---

### Post by urbanfractal on 2008-04-21
A big "Cheers" coming your way, anytime now! 

Thanks a lot for the fast help; I will try the doing-it-from-scratch method. It always worked and always will...

See u around then.

---

