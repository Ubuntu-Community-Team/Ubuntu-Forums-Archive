---
title: "How to eliminate booting error messages"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by open2linux on 2007-07-06
I have been using Ubuntu for just a few days, and I must say that I can`t complain.
So far evrything seems to work quite well.
Just a little trouble at booting.
It lasts about 1minute 30 secs (is that normal?) and while starting comes 
this message:
[B]
There are differences between the boot sector and its backup. 
Differeneces: (offset original/backup)[/B]

Then comes a long list of numbers, and then

**Not automatically fixing this ** 
fsck 1.40

Anybody knows what is it suposselly to be fixed?
And how to fix it?

Thanks

---

### Post by Cypher on 2007-07-06
Login using the Recovery mode option in GRUB. At the command prompt do the following
```

fdisk -l
mount

```
The first command will list the partitions on your HD and the second will list what is currently mounted. For all partitions that aren't mounted, do
```

e2fsck -y <partition name>

```
Where <partition name> is something like /dev/hda1, /dev/sda1 or whatever you got from the output of "fdisk -l" above..

---

### Post by open2linux on 2007-07-06
Thanks for responding.

I have a dual boot system with WinXP  /dev/sda1 and 
Ubuntu Feisty /dev/sda2

After doing
mount
I saw that both sda1 and sda2 are in the list.
But /dev/sda3 is not in the list, and that is the swap partition.

When I typed 
e2fsck -y /dev/sda3
this message came:

WARNING!! Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
Do you really want to continue?

This message got me a bit nervous, so I selected no and rebooted.
What should I do?

PD. By the way, even before solving this I learned from you about the signature, so I registered in the counters ;)

---

### Post by open2linux on 2007-07-08
Well, I finally found the solution myself:

sudo umount /dev/sda1

and then

sudo fsck.vfat -ar /dev/sda1

This fixed the error message. Thanks to uncle google.

:guitar:

---

