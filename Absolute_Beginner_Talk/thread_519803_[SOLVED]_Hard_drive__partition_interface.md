---
title: "[SOLVED] Hard drive / partition interface"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-08-07
Hi! I am fresh off the boat from old country (Windows XP) and loving my experience with Ubuntu so far. A couple of things I still have to get used to, of course.

One of those is something I expected to find in Nautilus, by analogue with the Windows interface. So... my hard drive, I have it partitioned but I want to see exactly how. Will I have to run some tools from the terminal or can I view the partition as a pie chart? I also want to install another internal hard drive on this laptop, how will I access the files on there? I've noticed that file addresses don't begin with a drive letter, which I'm used to.

Thanks for any insight!

---

### Post by LaRoza on 2007-08-07
* In the Nautilus address bar, go to "/". (Like My Computer in Windows)

* Type ```
df -l
``` will show disks
* Type ```
fdisk -l
``` will show free space on disks

If you installed to the whole disk, and used the defaults, you will have two partitions, one large EXT3 partition and one small SWAP partition.

---

### Post by dinostabOMG on 2007-08-07
I went to / - I've actually been there before, but I think I'm beginning to see. So, the folders that show up there are actually local folders on this single hard drive, but other drives will show up there and act like local folders?

I popped in a data CD, and noticed that its address is /media/cdrom0. I imagine a similar thing would happen if I put in a DVD or a USB drive? What about another hard drive? I typed df -l and got 
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             21149588   2918712  17156532  15% /
varrun                  517632       104    517528   1% /var/run
varlock                 517632         0    517632   0% /var/lock
procbususb              517632        92    517540   1% /proc/bus/usb
udev                    517632        92    517540   1% /dev
devshm                  517632         0    517632   0% /dev/shm
lrm                     517632     33788    483844   7% /lib/modules/2.6.20-16-generic/volatile
/dev/scd0               619304    619304         0 100% /media/cdrom0

```

So does that mean the CD is at /dev/scd0 or at /media/cdrom0? I'm a little confused on this point. Also, I'm assuming that my main HD is at /dev/sda1. If I put in another IDE drive will it show up at /dev/sda2 or something? Or will I access it with something preceding the root?

One last thing. I ran fdisk -l and got no output at all. What does that mean?


Thanks for responding and any help anyone might offer.

---

### Post by Inxsible on 2007-08-07
> I went to / - I've actually been there before, but I think I'm beginning to see. So, the folders that show up there are actually local folders on this single hard drive, but other drives will show up there and act like local folders? You are bang on target !! :)

> So does that mean the CD is at /dev/scd0 or at /media/cdrom0? I'm a little confused on this point. the device is at /dev/scd0 but it is mounted and therefore accesible at /media/cdrom0

>  One last thing. I ran fdisk -l and got no output at all. What does that mean? instead run```
sudo fdisk -l
```

---

### Post by dinostabOMG on 2007-08-07
Thanks for your help, guys!

In case anyone else with a similar question comes upon this thread, I noticed a utility that gives you a visual representation of your folders and drives, it looks quite cool. In the terminal type ```
baobab
``` and hit enter. I added it to my menus!

---

### Post by Inxsible on 2007-08-07
Dont forget to mark your thread as solved, if all your questions have been answered.

---

