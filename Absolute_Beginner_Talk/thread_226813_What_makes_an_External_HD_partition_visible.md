---
title: "What makes an External HD partition visible?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-31
Hi Folks
I have two external HDs. One is a Seagate 250GB with 4 ntfs partitions, all the same size. One primary partitions and the other three are logical in one extended partition.
The other USB HD is a Philps 160 GB and is partitioned into one primary and two logical partitions, all of about 50GB in size. One of the logical partitions is formatted to ext2 while the other two are ntfs.

So, what's the big deal?
Well, when I boot up, only TWO (out of a total of seven) of these external partitions show up on my desktop.
Obviously, one is the logical ext2 partition on the 160GB drive. But, the other is an ntfs partition from the 250GB drive and seems to be one of the logical partitions. (I say "seems to be" as I can't be totally sure as all 4 partitions on the drive have about the same size).

Now, the primary partition on the 250GB drive is flagged as bootable and I'm just wondering is this the one that shows up on the desktop.

Another point of confusion is that when I run "df -h" or "sudo fdisk -l" the ext2 partition is referred to as /dev/sda6
However, in fstab, it is known as /dev/sdb6
The partition from the 250GB USB HD that shows up on the desktop undergoes a similar "name change" being/dev/sdb7 in the first two listings and /dev/sda7 in fstab.

Curiouser and curiouser.
Any ideas?

Thanks
Paul

---

### Post by catlett on 2006-07-31
There shouldn't be an issue. They should be detected.
One question. Did you have the externals connected and on when you installed? If you did that may be the problem.(actually it shouldn't be a problem but it has showed up a couple of times)
You do not need an /etc/fstab entry for external drives. There is an application called pmount that mounts removable drives.
Try this for the heck of it. Open up your /etc/fstab with ```
sudo gedit /etc/fstab
``` Comment out the entries for the external hard drives(meaning put a # in front of the line for external drives) You can always uncomment (remove the # ) afterwards to get it back.
Anyways uncomment the drives and start up without the externals powered on. After you boot into Ubuntu, power on the hard drives. Icons for the drives should show up on your desktop.
I would try this first. It is pretty easy and I think it will work. What it does is take /etc/fstab and mount at boot out of the picture and lets pmount do the mounting of the drives.

---

### Post by PaulFXH on 2006-08-01
Hi catlett
I did what you suggested and it worked EXACTLY as you had predicted.
And, yes, I did have both of the USB HDs connected and powered up when I installed Ubuntu 6.06
That's great that I now have access to all of my external partitions.

Interestingly, the on-off switch on the Philips 160 GB (this one has one logical ext2 partition and two ntfs partitions) does NOT work at all from Linux (but DOES from WinXP). So, I have to use the Eject command to turn this off.
OTOH, the Seagate 250GB ( 4 ntfs partitions) does NOT react at all to the Eject command but the switch works.
Apparently, if there are any "Linux" partitions on the drive, control of the power on-off passes from the switch to the Eject command.

Many thanks for your advice
Paul

---

### Post by catlett on 2006-08-01
> **PaulFXH said:**
> Hi catlett
I did what you suggested and it worked EXACTLY as you had predicted.
And, yes, I did have both of the USB HDs connected and powered up when I installed Ubuntu 6.06
That's great that I now have access to all of my external partitions.

Interestingly, the on-off switch on the Philips 160 GB (this one has one logical ext2 partition and two ntfs partitions) does NOT work at all from Linux (but DOES from WinXP). So, I have to use the Eject command to turn this off.
OTOH, the Seagate 250GB ( 4 ntfs partitions) does NOT react at all to the Eject command but the switch works.
Apparently, if there are any "Linux" partitions on the drive, control of the power on-off passes from the switch to the Eject command.

Many thanks for your advice
PaulGlad it worked. That is interesting about the ntfs issue. I do not have an ntfs partition. I was expecting one but I was surprised when I hooked up my 160gb Seagate external for the first time and it came up fat32. I never messed with it afterwards. My other external is a homemade one from when I upgraded and threw the old one into an external case and it was already the linux slave drive so I didn't mess with it either.

Just for your knowledge. It is still risky to try and read/write to an ntfs from linux. Read is fine, you can copy anything or play anything from the ntfs. The issue is the linux capability is from reverse engineering. Noone has gotten a look at the source code because microsoft owns it.
My point is, I keep window's ntfs read only in linux. I use the ext2 driver for windows to access linux from windows [http://www.fs-driver.org/](http://www.fs-driver.org/) The driver allows you to access your linux partitions from windows with read/write capabilities.
The one drawback is saving something to windows from linux requires an extra step.
 If you have something you want on the ntfs partition, just save it on your linux partition and when you boot into windows, move it onto your ntfs. It adds a step but you are not taking any risks.
As for when you are in windows, you will have full read/write access to all your partitions.

---

