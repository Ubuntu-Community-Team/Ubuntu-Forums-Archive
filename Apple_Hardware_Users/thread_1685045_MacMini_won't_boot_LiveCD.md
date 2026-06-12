---
title: "MacMini won't boot LiveCD"
date: 2011-02-10
forum: Apple Hardware Users
---

### Post by uced on 2011-02-10
I wanna try Ubuntu but my MacMini3,1 won't boot 10.10 desktop liveCD.
CD md5 is OK.
Pressing alt on boot shows MacOS hfs+ hd and ubuntu CD. I choose the CD, the screen goes black and says something like "non bootable device, press any key". From there, no more keyboard or nothing. I must "hard" shut down the Mac.

My internal dvd drive is dead, so I am using a firewire external one. I know my Mac can boot from it with MacOS X install DVD.
Does Ubuntu only boot from internal drive ?

[edit] Why not trying 64bits ubuntu ? I downloaded the iso and burt it. Things are a little bit different: pressing alt now shows my hfs+ disk, a "Windows" CD and an "EFI boot" CD .
This forum and others being full of users that can not boot their mac any more, I did not dare choosing "Windows" nor "EFI boot" !
Are those things normal or not ?

---

### Post by uced on 2011-02-11
Let's live dangerously, I used ubuntu-10.10-desktop-amd64 liveCD !

First, I choose the "Windows" CD icon:
black screen with blinking cursor. Nothing more, had to reboot.

Second, I choose the "EFI Boot" CD icon:
Something happened ! It launched GNU Grub. I was asked to choose between Trying ubuntu, Installing ubuntu or Checking disk.
I selected the "Try" item and I got a kernel panic !

---

### Post by teh603 on 2011-02-11
That's very strange. Have you tried the i386 versions?

---

### Post by uced on 2011-02-11
> **teh603 said:**
> That's very strange. Have you tried the i386 versions?
Yes. It did not work (black screen + blinking cursor). That's why I tried amd64.

---

### Post by teh603 on 2011-02-11
> **uced said:**
> Yes. It did not work (black screen + blinking cursor). That's why I tried amd64.Did you try 10.10? I've had good luck with it. Also, have you flashed your EFI recently? Its possible, albeit unlikely, that a recent EFI flash might've made it unable to boot another OS.

---

### Post by uced on 2011-02-11
10.10 IS the one I tried.

I installed rEFIt. Its partition utility told me that I had to sync GPT and MBR. I did so.

Rebooting with rEFIt, I could choose the penguin on the CD but it doesn't go any further. It's just black screen and "Missing operating system"
Same result with i386 and amd64 CD.

---

### Post by uced on 2011-02-12
I think maybe the problem is the firewire external drive.
So, I gave up CD and used an USB stick to boot on, but it's always the same: "Missing operating system".

What's wrong with this fuc*** macmini ?

---

### Post by teh603 on 2011-02-13
Very strange. I'm single-booting so I don't need or want to use rEFIt or BootCamp and thus know very little about it. Its not a piece of software I'm comfortable messing with, anyway.

---

