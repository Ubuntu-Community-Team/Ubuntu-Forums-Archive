---
title: "MAC OSX / UBUNTU / WINDOWS 7 Boot problems"
date: 2012-06-12
forum: Apple Hardware Users
---

### Post by jamiecounsell on 2012-06-12
I recently followed the Lifehacker tutorial on how to triple boot Windows, Mac OSX and Ubuntu. After doing this, I was able to sync all partitions and get the OS's to run properly, but I am having trouble booting. Here's what's happening.
 
Macbook Pro 2010
2.66 GHz Intel Core i7
8GB 1067 DDR3
 
Partitions:
OSX LION 10.7.4 (125GB)
LION RECOVERY  (600MB)
WINDOWS 7 SP1 (125GB)
UBUNTU              (97GB)
LINUX SWAP        (1.86GB)
BOOT [linux]        (5MB)
 
 
- I am booting with rEEFit on my main partition (Mac OSX)
- If I boot the UBUNTUselection in rEEFit, it freezes on the Linux logo
- If I boot WINDOWS 7 from rEEFit, it loads the GRUB boot selector
     - From here I can still boot into Ubuntu, but not Mac OSX
- If I boot Mac OSX from rEEFit, it operates normally.
 
I want to use only a single boot loader (IE. I want to either ditch rEEFit and use GRUB, or hide GRUB and only use rEEFit). 
Basically, I only want to have to go through one selection in boot menus to get to my specified OS.
 
Any suggestions?

---

