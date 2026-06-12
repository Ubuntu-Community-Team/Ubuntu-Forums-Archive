---
title: "Windows can't find my hard drive"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-10
I'm trying to install a small windows partition (i know, it burns) on my computer in order to play games.


I've got it set up so that there is free space in front of all the other partitions (it would be first if it ever installed)

i've tried having just free space in front, and having an nfts partition in front.
niether seem to work. Setup will get to the point where i can press "Install windows xp"  It will ask me if there are any additional devices that i'd like to install (it gives me a list i've tried all the ones with dell, as well as choosing nothing) and then it will tell me that it cannot find a hard drive.

I obviously DO have a hard drive, and it has a nice size ubuntu partition on it.


any help? I'm thinking i have to configure the partition so that windows can read it, but i dont know how.

---

### Post by teddybairs1 on 2007-06-10
It's tough luck, but if you're going to dual boot you need to install windows first, and then Ubuntu. Otherwise, windows will trash your Master Boot record and GRUB along with it. There's no way around it that I've read about on the forums.

I just ran into a friend of mine today with a similar problem. He's trying to reinstall windows after wiping his Ubuntu partition. For some reason, the XP install disk can't see his hard drive. The BIOS knows it's there, but the XP install disk can't see it. I have no idea why.

---

### Post by 444 on 2007-06-10
And the model of this computer is? Probably missing drivers.

BTW, Windows will nuke the MBR and make it Windows-only. There's a trick to make a backup copy and have Windows load that to get into Ubuntu again so you don't have to boot from a live-cd and fix it...

---

### Post by Tyke91 on 2007-06-10
It's a dell dimension E520 

i was aware of the grub thing, i figured i could just reinstall with the live cd as i dont have a removable hard drive.

---

### Post by Tyke91 on 2007-06-10
I've tried flagging the partition as different things, but it still wont work.

---

### Post by 444 on 2007-06-11
Partition type set right aswell? I'm still leaning towards missing drivers though... I mean at the very least it would offer to erase whatever's on there and repartition for itself...

---

