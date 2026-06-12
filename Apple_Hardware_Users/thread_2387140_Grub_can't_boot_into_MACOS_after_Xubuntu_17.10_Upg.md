---
title: "Grub can't boot into MACOS after Xubuntu 17.10 Upgrade"
date: 2018-03-15
forum: Apple Hardware Users
---

### Post by erixoltan on 2018-03-15
I have a Macbook and have used a dual boot with Xubuntu and Mac OS X for a couple years. This week I upgraded my Xubuntu dual boot to 17.10 and it works better. However when I try to reboot into Mac OS X Grub gives me an error message that only flashes on the screen for a split second. It then makes a reboot noise and comes back into Grub.  

I will try to get a better look at the error message. Can anyone else point me to other things to look at in GRUB?

<Edited to change version number from 16.10 to 17.10 which was a typo.>

---

### Post by erixoltan on 2018-03-15
When I select "Mac OS X" in the GRUB menu, I get two messages.

The first says "**System boot order not found. Initializing defaults.**" 

Then this goes away and a second message appears.

**Reset System**

Then it reboots and returns to the GRUB menu.

If anyone can point me in the right direction, where to look in resolving this issue, I'd be very grateful. The system worked fine until I upgraded Xubuntu to 16.10 a few days ago.

---

### Post by wildmanne39 on 2018-03-15
*Thread moved to **Apple Hardware Users, a more appropriate forum**.*

16.10 is no longer supported you will not even receive security updates, I recommend installing 17.10 or 16.04, then April 26th 18.04 comes out and it has long term support like 16.04 does.

---

### Post by erixoltan on 2018-03-15
I'm sorry that was a typo. I installed 17.10, not 16.10 -- I still haven't gotten used to 2018 apparently. 

I saw on another thread the following command. I am putting it in with my results. 

```
$ efibootmgr
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000,0080
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Mac OS X
Boot0082* 
BootFFFF* 
```

---

### Post by erixoltan on 2018-03-23
I was able to resolve this. I am leaving the steps I used in case anyone else has a similar problem.  

In the above listing, efibootmgr has two Mac OS X entries. The old one 0080 and the new one 0081. It seems that the upgrade process added a new one without removing the old one. Since they both have the same exact name, it is not possible to select the new one.  This is just an inference on my part.  

I wanted to find out what would happen if I booted the 0081 entry. So I tried the following command. 
```
$ sudo efibootmgr -n 81
$ sudo reboot now
```
This tells the system to try booting 0081 the next time I reboot, for one time only. I then rebooted and the system was able to get into Mac OS X.

I then had to delete the 0080 entry which was preventing the system from getting to the 0081 entry.
```
$ sudo efibootmgr -b 80 -B
$ sudo efibootmgr -o 81,0
```
The option -b 80 selects the 0080 boot entry, and the -B option causes that entry to be deleted.
The option -o 81,0 sets the boot order going forward. My old boot order was specifying the 0080 entry which I have now removed. So I wanted to specify the new entry in the revised boot order.

Now with these changes my system boots file.  I will mark this as solved.

---

