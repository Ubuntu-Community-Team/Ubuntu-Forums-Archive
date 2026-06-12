---
title: "[SOLVED] Fresh install or Less-fresh install?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by JillSwift on 2007-12-11
I want to take my Windows partition off now, I feel comfortable enough with Ubuntu to go "without a net".

Which would be better for me, really?

[CENTER][FONT=Century Gothic][SIZE=3]Back up ~/ and otherwise start fresh.[/SIZE][/FONT]
[SIZE=3]*[FONT=Palatino Linotype]or[/FONT]*[/SIZE]
[FONT=Century Gothic][SIZE=3]Back up everything, and do some partition shuffling.[/SIZE][/FONT]
[/CENTER]

I'm thinking fresh install, but I don't want to make more work for myself. (Nor do I want to pound on the repositories unnecessarily).

---

### Post by rockinlinux on 2007-12-11
how are you partitions now? maybe a screen shot from gparted?
when i did this i just delete my windows partitions with gparted, created a separate /home, moved my ubuntu home and root next to my mandriva and used the rest of the free space for music. I dont think you will need to do a fresh install.

---

### Post by flamelab on 2007-12-11
> **JillSwift said:**
> I want to take my Windows partition off now, I feel comfortable enough with Ubuntu to go "without a net".

Which would be better for me, really?

[CENTER][FONT=Century Gothic][SIZE=3]Back up ~/ and otherwise start fresh.[/SIZE][/FONT]
[SIZE=3]*[FONT=Palatino Linotype]or[/FONT]*[/SIZE]
[FONT=Century Gothic][SIZE=3]Back up everything, and do some partition shuffling.[/SIZE][/FONT]
[/CENTER]

I'm thinking fresh install, but I don't want to make more work for myself. (Nor do I want to pound on the repositories unnecessarily).

**Fresh install** , only fuse (I don't really like it , if you want my opinion ) the new /home with your old one .
But all the others should be new and fresh .
If you want to keep your programs (those you installed ) , one of my friends proposed me **aptoncd **.
Why don't you try it ?

---

### Post by rockinlinux on 2007-12-11
just in case you care, this is how mine looks after removing windows. windows was in the middle of the sda2 and sda1...there was no sda3.

fyi-- sda2 is mandriva and the swap for both mandriva and ubuntu. sda3 is my music and the other two and ubuntu.

---

### Post by rockinlinux on 2007-12-11
if you are happy with your ubuntu now then there is no reason to do a fresh install. if you want to start over with a  fresh ubuntu then do a fresh install.

---

### Post by JillSwift on 2007-12-11
I really shouldn't post when I'm tired.

I left out why I want to do some partition reshufflin'. First, i want to kill kill off the damn "recovery" partition (I'm always afraid I'll accidentally boot that fracker >.>; ). Second, because of some poor planning there's 2 gigs at the end of the disk that are unallocated, and I hate waste =^_^=. Lastly, I've already put /home on its own partition, and I'd rather like to merge that with the larger windows partition, and that includes changes to the swap partition (/home and swap are two logicals in one prime).

Thanks for the advice so far, all. =^_^=

---

### Post by rockinlinux on 2007-12-11
you should be able to do that still with out doing a fresh install. and as i see you are going to be great if you just reformat sda1 and sda2. you dont really need to make your /home bigger, it is big enough already. i would just make the unalocated space you get when you delete sda1 and 2 to a ext3 partition to store extra stuff. you can then make it auto-mount by editing your fstab.

---

### Post by rockinlinux on 2007-12-11
also....just curious.

why is so much space in your root used??

---

### Post by rockinlinux on 2007-12-11
oh and about the 2 gigs, just move everything to the right, i mean sda4 and sda3 to the right :P

---

### Post by JillSwift on 2007-12-11
> **rockinlinux said:**
> also....just curious.

why is so much space in your root used??Um. I don't know... Is that unusually large? I've got most every video and sound editor installed that i could find (That's what i use my machine for, mostly).> **rockinlinux said:**
> oh and about the 2 gigs, just move everything to the right, i mean sda4 and sda3 to the right :PWell, if I can move partitions without too much threat of losing data. (Perhaps I'm still stuck on winders, where this was not an option without $450 of software).> **rockinlinux said:**
> you should be able to do that still with out doing a fresh install. and as i see you are going to be great if you just reformat sda1 and sda2. you dont really need to make your /home bigger, it is big enough already. i would just make the unalocated space you get when you delete sda1 and 2 to a ext3 partition to store extra stuff. you can then make it auto-mount by editing your fstab.Yeah, that's a good idea. I'm also thinking maybe merge those first three prime partitions into a new /home, then partition that last 2 gigglebyte space at the end as swap space. (I do need a lot of space in ~/ for my video work.)

You folks am the best! =^_^=

---

### Post by rockinlinux on 2007-12-11
well that could be even esier. just make your /home 2 gigs bigger. i move partitions all the time and never lose data. do you have a gparted cd? if not get it...it works great.

as for your root, if you have a lot of programs and stuff installed i guess its normal....i would not worry about it to much because you have hella space.

if you just make a ext3 with your restore and windows partition it would be a great place for your videos. :)

before you do anything abck up your data though...who knows what could happen.

here is a step by step of what i would do.

1) boot from the gparted cd
2)delete sda1 and sda2
3)move sda4 and 3 to the right
4)format the unallocated space to ext3
5)reboot and edit your fstab so your new partion auto mounts

also im not sure what you mean here
> I'm also thinking maybe merge those first three prime partitions into a new /home
but if i were you i would just do it my way LOL :)

you will be left with a (about)116BG partiton for whatever you want and then your / and /home and swap

---

### Post by JillSwift on 2007-12-12
> **rockinlinux said:**
> also im not sure what you mean here

but if i were you i would just do it my way LOL :)

you will be left with a (about)116BG partiton for whatever you want and then your / and /home and swap

I'm planning pretty much what you said, save that I need (as in I'm *awful* about needing things organized in a *specific* way) to make the old recovery, windows and current /home partitions and make them my new /home.

Thanks tons for your help! =^_^=

---

### Post by rockinlinux on 2007-12-12
good luck and let me know how it turns out please :)

are you just going to move everything to the left and then make you /home bigger?

---

### Post by JillSwift on 2007-12-12
> **rockinlinux said:**
> good luck and let me know how it turns out please :)

are you just going to move everything to the left and then make you /home bigger?Yep, that's the plan. :biggrin:

---

### Post by rockinlinux on 2007-12-12
sweetness! :grin:

---

### Post by JillSwift on 2007-12-13
> **rockinlinux said:**
> good luck and let me know how it turns out please :)Turned out fabulous! Yay! =^_^=

---

### Post by rockinlinux on 2007-12-13
congrats! :)

---

