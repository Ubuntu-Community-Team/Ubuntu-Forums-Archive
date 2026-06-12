---
title: "Dual Boot problem"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2008-02-24
I have two HDD and I installed ubuntu on one of them. Now if I install windows on the other then would I be able to boot both in windows and linux ?. I am using ubuntu 6.06 and I installed it using the live cd.

---

### Post by kaginken on 2008-02-24
Yes.




I've had better luck installing Winblows first, then Ubuntu afterwards, as Ubuntu does a nice job of creating your Grub dual boot menu, whereas winblows doesn't due to it blowing so much...

Just my opinion, I could be wrong.  :D

God speed, John Glenn

---

### Post by Rocket2DMn on 2008-02-24
Yes, but since you are installing windows second, you will have to reinstall GRUB afterward.  Here's how: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d)

---

### Post by kaginken on 2008-02-24
Rocket2DMn - nice.  Exactly what was needed.

If you have any problems with Rocket's solution link there - can always just wipe and install winblows as it won't waste much time - Ubuntu installs in minutes...

Rock on!  :guitar:

---

### Post by dead_man_walking on 2008-02-24
Thanks for your replies. 
The tutorial there overwrites the MBR. As far as I know windows overwrites the MBR when it gets installed but I have two disks, call themHDB and HDA. I installed ubuntu on HDB. 
I want grub to be installed in HDB so that when i install windows on HDA, grub does not get affected. Can this do the job for me
```

sudo mkdir /mnt/linux 
sudo mount /dev/hda1 /mnt/linux

then change directory to your installation sbin and run grub from there

cd /mnt/linux/sbin 
sudo ./grub

```

---

### Post by Rocket2DMn on 2008-02-24
It's okay to overwrite the MBR with GRUB, if you ever ditched linux, it's easy to restore the windows bootloader.  I would suggest just following the directions on the help site I gave since we know that it works.
Windows will automatically block out GRUB when it installs, there's nothing you can do about it except restore GRUB.  It's a little trouble, but fortunately it's not difficult.

GRUB should auto-detect your windows installation and add it to the list, but if it fails to, it can be added manually.

---

