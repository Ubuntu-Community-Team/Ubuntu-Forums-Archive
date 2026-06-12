---
title: "[SOLVED] Removing a partition"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-17
I have Ubuntu loaded. 
I used gparted from live CD. This is the info I got

> Partition   File System       Size     Used     Unused
------------------------------------------------------------------------
/dev/sda1    ntfs               108        63         45
/dev/sda2    ext3                78         36         42


What would be the implication if I deleted the ntfs partition. I don't need the data,

1.Will my Ubuntu boot normally after the change? (After removing the live CD from the drive?)
2. The NTFS partition is /dev/sda1, so does it mess up anything if I delete it and make the entire thing as ext3?
3. Would the /dev/sda2 gets changed to /dev/sda1 automatically or should I do it manually. Or does it really matter?

Any help on my noob question would be highly appreciated.

---

### Post by ruy_lopez on 2008-04-17
> **GoCool said:**
> 
What would be the implication if I deleted the ntfs partition. I don't need the data,

1.Will my Ubuntu boot normally after the change? (After removing the live CD from the drive?)
2. The NTFS partition is /dev/sda1, so does it mess up anything if I delete it and make the entire thing as ext3?
3. Would the /dev/sda2 gets changed to /dev/sda1 automatically or should I do it manually. Or does it really matter?

Any help on my noob question would be highly appreciated.

1) Ubuntu should boot normally afterwards, provided nothing goes wrong.

2) You have options: you can delete /dev/sda1 and then create a new ext3 partition in its place. Or you can delete /dev/sda1 and then grow /dev/sda2 into the free space (you might have to move it to the start of the free space first, just don't delete /dev/sda2).

3) The dev numbers aren't especially important. sda2 will still be sda2 after you delete /dev/sda1.

You should backup everything before using gparted in case anything goes wrong.

---

### Post by Oldsoldier2003 on 2008-04-17
> **ruy_lopez said:**
> 1) Ubuntu should boot normally afterwards, provided nothing goes wrong.

2) You have options: you can delete /dev/sda1 and then create a new ext3 partition in its place. Or you can delete /dev/sda1 and then grow /dev/sda2 into the free space (you might have to move it to the start of the free space first, just don't delete /dev/sda2).

3) The dev numbers aren't especially important. sda2 will still be sda2 after you delete /dev/sda1.

You should backup everything before using gparted in case anything goes wrong.

it is rare but Gparted sometime will mess up your data, so the advice to backup is very sound advice. just be aware that anytime you grow a partition to the left it takes a very long time.

---

### Post by quirks on 2008-04-17
Hi GoCool,

I want to say in advance, that I don't know the answer to all of your questions for sure. Therefore I won't promise anything here - I don't want to be blamed when your system does not work anymore. ;-) I had a similar scenario when I switched to Linux completely some years ago, but I used the occasion to do a fresh reinstall.

But I can give you some recommendations that have proven to be valuable in many linux installations I did.

1. I you have the possibility to make a backup of you hard disk to - say - an external hard disk, make a backup, no matter what some other guy here on the forums tells you (unless you are ok with losing all data on your entire hard disk). Making a backup of your hard disk is very easy with tools like partimage. If you need any further instructions on that, you can ask me anytime. A backup does not take too much time, and it saves a lot of time, when you need it.

2. It is a good practice to divide any linux installation into at least four partitions:
/dev/sda1 is mounted on /boot and size is 100 MB
/dev/sda2 is mounted on / and size is 6 to 8 GB
/dev/sda3 is swap and size depends on your memory
/dev/sda5 is mounted on /home and size is whatever is left
This way, your bootloader (/boot) is unaffected, when you fiddle around with other partitions, like you intend to do right now). Putting data (/home) and operating system (/) on different partitions leaves your data unaffected, when you want to reinstall the operating system. Also you can do a filesystem backup of you operating system (without the data).

3. Try to avoid moving the swap partition (resize or move on disk). The operating system usually does not recognize it anymore after that. You can re-register it, but it is a procedure that can be avoided.

4. Resizing ext3 partitions is a safe operation. It has never failed for me (the same applies to NTFS partitions, but it is said to me way more dangerous).

---

### Post by bumanie on 2008-04-17
It is best not to double post. Now you have two threads about the same thing. Very confusing for people trying to answer and help you. We are all volunteers, if you need answers so quickly, may be you should get commercial support from Canonical.

---

### Post by GoCool on 2008-04-17
> **bumanie said:**
> It is best not to double post. Now you have two threads about the same thing. Very confusing for people trying to answer and help you. We are all volunteers, if you need answers so quickly, may be you should get commercial support from Canonical.

Sorry...for the trouble caused. I'll surely keep this in mind when I post in the future.

A Big "Thank you" for all the people who helped me out.

---

