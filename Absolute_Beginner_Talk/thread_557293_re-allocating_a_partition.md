---
title: "re-allocating a partition"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by brodiewells on 2007-09-22
Hi,
I am new to ubuntu and linux.  I have never asked help on anything because I can usually find stuff myself.  There is a lot of good stuff on here.  Thanks for all you do.
I installed ubuntu on my old computer and it has quickly become my primary computer.  Now I need more space, so I deleted my windows partition but I cannot re-allocate that partition or increase the size of the linux partition.  It is very important that I do not have to reinstall as I do not a CD drive.

This is what my harddrive loks like in Gparted and QTparted has the same problem

[IMG]http://www.upperweather.com/images/Screenshot.png[/IMG]

Thank you so much

---

### Post by HokeyFry on 2007-09-22
you wont be able to resize or re-allocate that partition (well you can, but it will take HOURS upon HOURS, from my experience) and you will need a live cd to do that, so i would suggest formatting that as ext3, then to make things simple, make a directory in your home directory

```
cd /home/`whoami`
mkdir otherPartition
```

type in
```
sudo mount /dev/sda# /home/`whoami`/otherPartition
```
where # is whatever number is assigned to that partition

that should mount it. then type into a terminal
```
sudo gedit /etc/fstab
```

and at the bottom of the file, add
```
/dev/sda# /home/yourUserName/otherPartition auto 0 0
```
where yourUserName is your user name, and the # is the same as above

this last part is not necessary, but when you reboot it should automount the partition so you can read/write to it


if you cannot write to the directory, post, because i cannot remember the option for that but i will find out

---

### Post by Jeroen Vernooij on 2007-09-22
Hi, 
right-click on your ext3 8GB partition in the list.
You will find out that the option to resize is greyed out (unclickable).

That's because your partition is mounted.
If you unmount it, you can resize it, to also use the unallocated space.
However, this cannot be done, because you are logged in.

So you need to run Gparted from a live-cd (feisty cd is possible)
But you say you don't have a cd-drive, so this is not possible.

You can install the live-cd on a usb-stick, then boot off the usbstick and resize your partition, or borrow / buy a cd-drive?

---

### Post by brodiewells on 2007-09-22
yeah i kinda figured i was just going to have to reinstall, and do it right from the begining this time.  Thanks a lot for the help!  Before I go looking at how to do it off a usb stick do you know where i can find some good directions for it? Like don I have to change the bios?

Thanks again.

---

### Post by Jeroen Vernooij on 2007-09-22
A nice howto is in the ubuntu wiki: [https://wiki.ubuntu.com/LiveUsbStick](https://wiki.ubuntu.com/LiveUsbStick)
or [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Maybe this is useful: [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

You should make sure your computer can boot from USB disks, check the bios.

---

### Post by brodiewells on 2007-09-22
I don think that partition has a number assigned to it anymore it used to 1 but now nothing seems to be in sda1  I wish I had asked for help earlier because that would have been an excelent work around

Thanks!

---

### Post by meierfra on 2007-09-22
You might also try to use the gparted live usb:

> [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by brodiewells on 2007-09-22
I did what hokeyfry suggested and he was right i cannot write to it.  any suggestions?

---

### Post by psusi on 2007-09-22
Boot from the livecd and resize it.

---

### Post by brodiewells on 2007-09-23
i don have a cd drive.  if i could just write to it now i would be really happy

---

### Post by psusi on 2007-09-23
How did you install in the first place then?

---

