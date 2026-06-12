---
title: "error 17 dual boot"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by afgwiz on 2007-03-12
I am a complete novice with regard to Ubuntu/linux programming.

I have installation and live 5.04 disks.

I am trying to load a dual boot Ubuntu and win98se on a 386 machine on the same hard drive, there is also an empty slave drive. win98 is already loaded.

After a seemingly OK load of 5.04 the first reboot of the machine results in error 17.

I beleive this means Ubuntu is searching the wrong partition to  boot from.

i can load the live disk, but I do not know how to get started to edit the system so Ubuntu goes to the correct partition to boot.

Please can some one give me a step by step instruction, from the grub? screen so I can get to the point where I can alter the Ubuntu boot.

if I can't get started I'll have to assume Ubuntu linux is not for me.

thanks in anticipation

Andrew

---

### Post by dstew on 2007-03-12
Boot from the live cd, open a terminal window and type

fdisk -l

This will display the names and types of partitions you have on your disks. Then from the terminal window start Grub. It has an editor that will allow you to change its menu so you can boot from the correct partition.

By the way, why are you not going with 6.06 (Dapper Drake)?

---

### Post by alienexplorers on 2007-03-12
Boot from your install disk (LiveCD) and wait for it to startup.  Go to the terminal and enter:

sudo grub (ENTER)

type: find /boot/grub/stage1

output should look something like: (hd0,0)

type: root (hd0,0)

type setup (hd0)

reboot machine

---

### Post by cookieforyou on 2007-03-12
```
fdisk -l
``` won't work.
You need to type ```
sudo fdisk -l
``` where l = small 'L'.

---

### Post by afgwiz on 2007-03-12
Thank you for your replies.

I have 5.04 'cos I sent off for ubuntu ages ago, and never got got round to giving it a proper go.
do the later versions not suffer from this problem? I could wait for a new disk, although i would like to solve what should be a simple problem.

when i open the terminal from the live disk it is comes up with root@ubuntu (or similar) should I put the command in there? the root of my hard drive installation is a different name, wilson. with my windows head on i would have to change directories to edit, this is where I begin to get confused.

I don't have the PC in front of me so I can't give you an update of success

thanks again

Andrew

---

### Post by afgwiz on 2007-03-12
Hello again

how do I start grub from the terminal window?

this gives you an idea of my knowledge.

thanks for your indulgence

Andrew

---

### Post by igknighted on 2007-03-12
You're not starting grub per se, you are just editing it.  If you copy and paste alienexplorers commands from above (substituting whatever you get for (hd0,0) then you should be all set.  Using Ubuntu 6.06 or 6.10 will probably lead to much fewer troubles, so if you can get a hold of those disks that would be recommended.

---

### Post by afgwiz on 2007-03-13
I have now tried your instructions

I tried in both terminal and root terminal (which should I use?) 

sudo grub comes back with command not found

There is nothing on the hard disk other than partition one win98se, part 2 primary ext3 I assume the ubuntu system, part 3 fat32 empty and part 4 ext3 logical empty and the empty slave drive.

pleas, what should I do?

regards

Andrew

---

### Post by dstew on 2007-03-13
Boot live CD, go to the terminal, and try grub (not sudo grub). See if that works.
(The "command not found" may refer to sudo, and not grub.)

---

### Post by afgwiz on 2007-03-25
I have tried both 'sudo grub' and 'grub' in both the root terminal and the terminal windows.
Each time bash comes back with command not found,
Whiich terminal window is best to use?
What can I try now?

Andrew

---

### Post by dstew on 2007-03-25
I don't know enough about Ubuntu 5 to say for sure, but it maybe grub is not available on the command line. You might need to try a SuperGrub disk (grub on its own live CD). You can get supergrub here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Do other commands work? Did you do lspci -l?

---

