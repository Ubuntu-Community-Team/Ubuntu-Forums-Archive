---
title: "Install issues:  which CD? (was:  Oooh! Please help! Pleeeease!)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Anemic_Royalty on 2006-10-03
Okay, guys, I think I messed up! So I burnt Ubuntu to a disc and booted my computer with the disc in it, and a couple of options came up: install as text, install as OEM, and a few others. I clicked "install as text" or something like that. It like installed I guess but there were a few errors and stuff but anyways it asked me if I wanted to do like a partition, and I said yeah. So after a bunch of like installing and stuff nothing happened! I don't know how to boot it up!

Luckily I burnt Slax to a CD before I did this stupid stuff, which is what I'm on right now. I went on "system" and deleted the partition because when I tried booting my computer without the Ubuntu disc it said "Reboot using proper boot device..." or something like that, and I'm not sure what I did. But now, even though I deleted that other partition, I still can't boot Windows! Please help! Pleeeease, I'm on my knees, guys!

---

### Post by Sef on 2006-10-03
So understand your situation correctly:

You tried to dual boot, but there was a problem.  So you used Slax to undo the partition and now you can't boot into Windows. Is that correct?

---

### Post by Anemic_Royalty on 2006-10-03
> **Sef said:**
> So understand your situation correctly:

You tried to dual boot, but there was a problem.  So you used Slax to undo the partition and now you can't boot into Windows. Is that correct?


I'm pretty sure. I mean, I didn't uninstall Windows when I tried to install Ubuntu. It asked me if I wanted to create a partition on the hard disk, and I said yeah. So after that, after it supposedly installed, I tried booting it up, and all that popped up was the "install as text", etc. screen. So I tried booting it without the disk, and it says "reboot using proper boot device..." or something like that. Do you understand?

---

### Post by Sef on 2006-10-03
There is a way to reinstall Windows Boot Loader, but I can't remember it right now and can't find a post on it either.

---

### Post by Ocxic on 2006-10-03
boot with you windows cd, enter the recovery console and type "fixmbr" without the quotes, that will fix the windows partition and hopefully get you botting windows again. (if you didn't accedentaly hose your system by formating the whole drive, don't worry you prolly didn't).

anyway if that doesn't workyou'll prolly have to reinstall windows, or take the chance and switch to ubuntu, learn by doing.

i suggest you read up on partitioning a hard disk, MBR (Master Boot Record), fdisk,  and the partition table, befor attempting to (re-)install anything, itt'l give you a better idea of what your doin during the install. wikipeidia should have a good run down on the stuff.

---

### Post by Sef on 2006-10-03
If you haven't already, read this to [dual boot.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by confused57 on 2006-10-03
Here's 2 excellent websites you might want to peruse:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(see the section "Uninstall Ubuntu" for restoring the Windows mbr)

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Another site for installing in Ubuntu:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Edit: Sef beat me to the first link.

---

### Post by mysticrider92 on 2006-10-03
Which Ubuntu cd did you download, the Live cd or the Install cd? The Live cd has a very easy to use installer with almost automatic partitioning. 

I don't have a solution for Windows other than what Ocxic said. You have to be very careful when insalling Ubuntu (or any OS for that matter) on a hard driv you can't afford to lose.

---

### Post by Brunellus on 2006-10-03
thread title changed to better reflect the nature of the help request.  

In the future, please use your thread title to give a BRIEF description of the TYPE of problem you are encountering.  That way, users who know HOW to help you can know that they CAN help you.

throwing yourself to the mercy of the community may get you pity, but may not get you the technical help you need.

---

