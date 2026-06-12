---
title: "Live CD won't boot"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by mulerider_too on 2008-01-28
i cannot boot from a live cd.............help!!!

---

### Post by jhetrick62 on 2008-01-28
You did not explain the problem.  Probably the xserver can't figure out your display properly.  Boot into failsafe and set xorg.conf to vesa and then start X server from there.

---

### Post by JoshuaRL on 2008-01-28
... or it may be a problem with not setting the BIOS to boot from CD.  Or the CD may be the problem, it may be corrupted or burned incorrectly.  If you could post what you did and what happened we could trace down the issue.

---

### Post by Amstell on 2008-01-28
check to make sure that your cd boots before your hd....enter your bios and switch the order

1. cd rom
2. floppy drive (old school baby)
3.  hard drive

---

### Post by crjackson on 2008-01-28
> **mulerider_too said:**
> i cannot boot from a live cd.............help!!!

Why not?  How can we help you if you don't describe the problem in a little more detail.

---

### Post by Amstell on 2008-01-29
> **crjackson said:**
> Why not?  How can we help you if you don't describe the problem in a little more detail.

Getting ready to bust 1000....nice

999 looking good.  Just thought i would weight in.

---

### Post by mulerider_too on 2008-01-29
/bin/sh: cant access tty; job control turned off

(initramfs) [98.023634] atal.00: failed to set xfermode (err_mask=0x4)

[133.443731] atal.00: failed to set xfermode (err_mask=0x4)


thats what is says

---

### Post by crjackson on 2008-01-29
Okay, that looks like a IO communication error related to your Hard Drive.  Did you install from the 7.10 LiveCD?

---

### Post by mulerider_too on 2008-01-29
> **crjackson said:**
> Okay, that looks like a IO communication error related to your Hard Drive.  Did you install from the 7.10 LiveCD?

in a class at school and not sure which version it is (however this is a different version that the teacher gave us last week which doesn't work on my machine either)

---

### Post by Amstell on 2008-01-29
> **mulerider_too said:**
> in a class at school and not sure which version it is (however this is a different version that the teacher gave us last week which doesn't work on my machine either)

yeah make sure you are using the 7.10 desktop edition live cd

---

### Post by mulerider_too on 2008-01-29
it says ubuntu 7.10 disktree when i put the disk in while running windows and it spins up

---

### Post by Amstell on 2008-01-29
> **mulerider_too said:**
> it says ubuntu 7.10 disktree when i put the disk in while running windows and it spins up

go to ubuntu.com from windows, download the 7.10 desktop image, burn it to a cd and restart your computer.

---

### Post by mulerider_too on 2008-01-29
> **Amstell said:**
> go to ubuntu.com from windows, download the 7.10 desktop image, burn it to a cd and restart your computer.

you mean download the software again then burn it to a disk?

---

### Post by crjackson on 2008-01-29
> **mulerider_too said:**
> in a class at school and not sure which version it is (however this is a different version that the teacher gave us last week which doesn't work on my machine either)

I would suggest you download the most recent version of Ubuntu Desktop Edition.  That would be version 7.10.  Start from scratch and reinstall, your current install isn't working anyway.  Then perhaps it will be easier to track down the problem(s) once we know what OS you're working with.

---

### Post by mulerider_too on 2008-01-29
ok...got the 7.10 now it just looks loke its loading, the word "ubunto" and the status bar goes away and blank screen is all thats left

---

### Post by mulerider_too on 2008-01-29
left it alone for about 25 mins....never did come up

restarted win xp and now im here

:(

---

