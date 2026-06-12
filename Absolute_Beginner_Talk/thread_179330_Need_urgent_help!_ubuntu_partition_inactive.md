---
title: "Need urgent help! ubuntu partition inactive"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by a_0000 on 2006-05-19
I used gparted to create a 15gb partition in my hdd so that I can install XP (it was urgent, for use with my PDA) but while installing XP it said it would set active the partition XP was being installed to which means that now the first partition in which ubuntu (dapper beta 2) is installed can not be booted in to as there is no boot up menu or anything!!!

My hdd is like this: 

1st partition: dapper (98GB) UNACTIVE
2nd partition: xp (15gb) ACTIVE
3rd partition: linux swap (2.5gb)

Plz plz plzzzz somebody help as I have all my files and data in my ubuntu partition. How can i boot back in to ubuntu?? is there even a way or have i lost it for good now? :confused: :confused:

---

### Post by Nano Geek on 2006-05-19
You should at least be able to access yout Ubuntu partition from windows and make a backup of your files. If you can wait, I will try to find some instruction for you.

---

### Post by macdo on 2006-05-19
So that you know what happened, not a solution.

Windows likes being first on the disc. To do that, it overwrites the MBR...
It's always recommended to install windows first, and anything else, second, for that reason.

---

### Post by Klaidas on 2006-05-19
Everything's gonna be allright ;)
Take a look here: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nano Geek on 2006-05-19
It looks like someone allready got you instructions, but here they are anyway. I got them from the How To by [vnbuddy2002]("http://www.ubuntuforums.org/member.php?u=13391").
Here they are.

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

