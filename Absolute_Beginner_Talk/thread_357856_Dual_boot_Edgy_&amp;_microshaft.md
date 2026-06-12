---
title: "Dual boot Edgy &amp; microshaft"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-10
Hi I have never set up a dual boot before. On the machine I want to do this I have 2 x 40 gig hd's. One has winxp and the other is Edgy. I guess I have to set with the jumper Edgy as the 1st hd and winxp as the 2nd hd. I read that grub is what I use to select what drive I use when booting so how do I do that? I see that when Edgy is booting that the word grub comes up so I suppose that Grub is installed? I did read a few posts on the subject but none seem to involve 2 hd's so I am a little confused.

---

### Post by igknighted on 2007-02-10
All you need to do is switch the boot order in the BIOS to boot the Ubuntu disk first.  Then you need to add an entry to the file /boot/grub/menu.lst that tells it how to boot windows.  IIRC it goes like this:
```

title Windows
root (hd1,0)
makeactive
chainloader +1

```

You will need to use 'sudo' to get permission to edit this file

---

### Post by moshuptrail on 2007-02-10
No worries.  Just install edgy on the 2nd HD.  It should install grub.  Grub will let you choose if you want to boot XP or Edgy.  The 2nd hard drive is not an issue.  You shouldn't need to mess with jumpers.  I've got a similar setup with Dapper: 80G XP as first drive, 200G Dapper as 2nd.

I'm not sure exactly how the boot process works, but the MBR on your HD1 will be modified for grub.  Somehow grub will find the 2nd HD and the grub menu.

---

### Post by xpod on 2007-02-10
G,day m8:) 
If you`ve used ubuntu before now it should be pretty easy.
I have two 40g drives too and when i used to have XP on one it was as simple as installing that to the first drive then once you`ve finished messing around with that you just throw that Ubuntu cd in and when it gets to the installation stages all you do is point the installer to the "erase enitre disk" option.Usually "hdb" it`s called.

If things go well then It does it all for you pretty much

---

### Post by rapattack1 on 2007-02-10
Um I am pretty confused. I have installed the os's already. I have only been using Ubuntu 5.04 on the machine I am on now for 4 weeks so I don't know much.
Ignited: where do I put that code?
moshuptrail: really not sure what you mean. The hd's have already got the os's on them.
xpod:have installed os's. Sorry I was told to do this first.

---

### Post by moshuptrail on 2007-02-11
So you have 2 40G HD's.  HD1 has XP, and HD2 has Edgy, or U 5.04 (it really doesn't matter)

Is that correct?

So how do you boot to XP today?  How to you get to Ubuntu?

---

### Post by rapattack1 on 2007-02-12
OK I have 2 hd's(40gig each). The master is now Edgy and the slave is XP. My friend came over that was trying to do the dualboot thing but he wasn't able to get it happening. Previous to this if I wanted to access xp I had to plug it as a master and if I wanted to access Edgy I had to change the plugs/cable. Very annoying but that is what I had to do.
The machine I am on right now has 5.04 which is internet connected. The other machine with the two hd's is not. That is another issue.

---

