---
title: "Installing a hard drive and a DVD drive"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-02-05
Grettings everyone, I've been doing a lot of searching, but without much luck.  I am looking for a concise step-by-step guide to installing a hard drive and a DVD drive as well, on Ubuntu Dapper.  

I've found a few things, but most of it goes over my head, and none of it specific to Ubuntu.  If anyone has time to point me in the right direction it would be much appreciated.  

Thanks for your time.

---

### Post by bward1 on 2007-02-05
I'll try and give you an over simplified howto maybe that will point you in the right direction.

As for the physical installation of the hardware, you need to obviously open up your case and find the cables that match the interface of your device.  You then need to plug in your hardware using the right cables to your motherboard.  There are howtos around that provide pictures of how to do it if you have never done it before, but as with most computer plugs, if it fits, it probably goes there.  Make sure you have the power from the power supply and the data ribbon (or cable or w/e they call it for SATA since it isn't really a ribbon like IDE was) connected to the motherboard.  Reference your motherboard manual if you aren't exactly sure where things go, but again, if it fits your prolly safe.

Now for the software side.  I've never added a new DVD drive to ubuntu before, so I can't really give you any guidance there.  For your hard drive you will need to format it first.  I recommend getting gparted ```
apt-get install gparted
```or via synaptic which will do things graphically for you.  You should then be able to run that by searching through your menus or running gparted from a terminal.  After you have formatted and partitioned the drive you will need to mount your new partition(s).  You can mount a partition, lets say sdb1 by doing: ```
sudo mount /dev/sdb1 /where_you_want_to_mount
```To make your system mount this partition automatically on every reboot you need to edit /etc/fstab and I don't have much experience with that other than knowing that it is a one change you make.

Just a quick explanation of the differences between the linux filesystem and windows.  In windows you have C:\ and D:\ and so forth and things are labeled by letters, you do not have this in linux.  When you add a drive in linux, you can add that drive to essentially act as a folder or directory in the overall filesystem.  So for example, in windows lets say I installed my operating system on C:\ and then put My Documents and the like on D:\ then that seperates the operating system from my personal files.  In linux what I would do to accomplish a similar task would be to install linux on the first hard drive (C in windows) and that has the root directory / and a good deal of the files thereafter.  Then I have that second partition formerly known as D:\ and I want to mount it to hold user files, so I mount it to /home/ and then everything /home/user/whatever is all on the equivilent of D:\.  Once you get your mind around not having a C:\ and D:\ paritions to directly talk to, this scheme actually makes a whole lot of sense.  Once you have things setup it looks and feels like one filesystem rather than a couple of partitions or drives that store data.

I hope that that at least points you in the right direction.

---

### Post by logos34 on 2007-02-06
Hope these links help you:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive)
[http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux](http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux)

Remember to:
-correctly configure the jumper on a pata drive (master, slave or cable select)
-set the jumper on sata II drive for 150 or 300 gb/s mode based on what your motherboard supports (some sata II drives require a firmware update or driver--e.g. Hitachi)
-(if slow) verify dma is enabled ([https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA))
-(if it doesn't show up at all in Ubuntu) verify device is enabled in BIOS and set disk detection to 'auto'

---

