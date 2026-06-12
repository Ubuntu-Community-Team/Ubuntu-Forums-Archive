---
title: "Boot and login problems"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by amosharper on 2007-05-29
Hi,

I have two separate PCs, both dual-booting WinXP and Ubuntu. Both have different problems with booting and login respectively.

The first, when booting, runs a FSCK on both partitions of the disk every time. The values in FSTAB are set to 1 (except the swap partition, which is 0). This isn;t really problematic, but it does mean I have to wait a minute longer, and it does mean that when I'm showing off my flashy new OS, the graphical loading bar is consistently broken by a scary command-line interface. How do I make FSCK run every thirtieth time the drive is mounted instead?

The second boots fine, but when it reaches the graphical logon screen, only one of two users is shown until I move the mouse. If I try to log in to either, it goes to a beige/brown screen with a loading cursor and nothing further happens. However, if I press CTRL-BACKSPACE at any point, it refreshes with both users shown and login works as it should. Any ideas why this might happen, or how to resolve it?

Thanks hugely in advance;

- Amos

---

### Post by init1 on 2007-05-29
Doesn't one use tune2fs to change the fsck? I have never tried it, but it may work
Your second problem is an X one, possibly because of gdm, or of the X scripts. Maybe you could try xdm or kdm.

---

### Post by amosharper on 2007-05-30
> **init1 said:**
> Doesn't one use tune2fs to change the fsck? I have never tried it, but it may work
Your second problem is an X one, possibly because of gdm, or of the X scripts. Maybe you could try xdm or kdm.

Thanks for your reply.

How do I 'try xdm or kdm'? The problem only sometimes happens, and I suspect might be because of fsck running every startup (which I'll go about fixing when I have a chance, using tune2fs as you say).

Thanks again,

- Amos

---

