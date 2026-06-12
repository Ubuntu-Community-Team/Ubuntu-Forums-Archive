---
title: "Shrinking Ubuntu partition (ext3) ERROR"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Baseer on 2007-07-29
I would like to shrink my Ubuntu partition so that I can install XP. And currently Ubuntu is the only OS on my drive, and it takes up the whole drive.

So what I've done is put in the LiveCD in so I could modify my Ubuntu partition, but when I try to shrink it using GNOME Partition Editor, it gives me this error:

*Check filesystem on /dev/sda1 for errors and (if possible) fix them.*

Where do I proceed?

And I realize after installing XP, the bootloader will be messed, but I'm assuming [this guide](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) will be fine right?

Thanks in advance.

---

### Post by splintercellguy on 2007-07-29
Do fsck /dev/sda1 in the Terminal on the LiveCD. The guide should be good.

---

### Post by alienexplorers on 2007-07-29
If you manage to get SDA1 reduced in size and you get XP loaded then you will have to reload GRUB.  To do this Insert your LiveCD and boot it.  Enter terminal and type in sudo grub.
Enter :
> find  /boot/grub/stage1
You will get and output such as (hd#,#)
Enter:
> root (hd#,#)
Enter:
> setup (hd#)
leave off the partition number in the setup line.
quit grub
reboot and dual boot should run fine.

---

### Post by Baseer on 2007-07-30
Thanks for the replies.

Ok I've tried doing fsck in the terminal and this is my result:

> ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: clean, 146728/7028736 files, 1154899/14040802 blocks

But, it still shows me the same error when I try to shrink the partition.

What do I do now?:confused:

---

### Post by splintercellguy on 2007-07-30
What's the detailed error message? Can you post a screenshot?

---

### Post by Baseer on 2007-07-30
It says underneath that error:

> **e2fsck -f -y -v /dev/sda1**
[i]/dev/sda1 is mounted.
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Cannot continue, aborting.[/i]

---

### Post by Baseer on 2007-07-30
Never mind, I solved it myself. :)

Ok so if anyone gets this problem: Basically you just have to unmount sda1, AND turn off the 'linux-swap' and unmount the swap partition ('extended'). All partitions must be unmounted and then you can resize. :)

---

