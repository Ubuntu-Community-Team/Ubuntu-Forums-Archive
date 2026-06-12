---
title: "Help removing Dual Boot Ubuntu &amp; XP"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by nickb23 on 2007-03-29
Hi all

I had my pc dual booting ubuntu 64bit and xp fine, but after initial problems I have decided to go to 32bit Ubuntu. I tried to install Ubuntu, and it kept on coming up with (I now know is a bug) "no system file" or something like that. I decided to reformat the partition in xp with partition magic and try again. Still the same error. I then tried to load xp, but it now comes up with Grub load error 15 at start up. I loaded my xp disc and did FIXBOOT, but it is still coming up with grub error 15. 

what can I do to fix this. I need to get into XP to download the alternate disc that seems to have fixed this issue.

thank

Nick B

---

### Post by houstonbofh on 2007-03-29
You need to rewrite the mbr to remove grub.  Any boot disk with a modern fdisk on it will allow an 'fdisk /mbr' to fix it.

---

### Post by Bias on 2007-03-29
> **houstonbofh said:**
> You need to rewrite the mbr to remove grub.  Any boot disk with a modern fdisk on it will allow an 'fdisk /mbr' to fix it.

fixmbr is also part of the windows xp disc (assuming you have one), boot from it and go to the repair console, this gives you a text interface. Type fixmbr and confirm you wish to do it.

---

