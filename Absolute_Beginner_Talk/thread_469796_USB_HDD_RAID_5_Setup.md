---
title: "USB HDD RAID 5 Setup"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by aaron_summer on 2007-06-10
Good Day Every,

I have 3 320 USB External HDDs (all identical HDD Models) and need to setup an external RAID 5 with them to keep all my photos and videos safely archived.

I have Ubuntu Server installed and would like to know if anyone can walk me through setting up a software raid 5 setup for these USB drives? Or at least point me to a resource where this has been done before.

Thanks in advance,

---

### Post by nutz on 2007-06-14
I would like to know also.

---

### Post by aaron_summer on 2007-06-15
After some research I was able to build a simple software controlled RAID 1 array with 2 of my external 320 GB USB drives.

Tools used: gparted, gedit,  mdadm and of course some coffee ;)

First I needed to know the location of my USB drives ...

```
cat proc/diskstats
```

My two USB drives were mounted (?) to /dev/sda1 and /dev/sdb1. 

I then opened gparted and removed the partitions from both drives, and created a new partition using the full disk space and formated to EXT3 file type. (I wonder if I could have gotten away with not formatting the drives?)

Then I opened a terminal window and installed the mdadm tools for software raid ...

```
sudo apt-get install mdadm
```

After the mdadm installed I used it to build the RAID 1 ...

```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```

Then to sync the two drives together I needed to reboot the computer.

Once the computer restarted I opened a terminal to view the progress of the sync ...

```
cat /proc/mdstat
```

or

```
watch cat /proc/mdstat
```

The above will refresh the results every 2 seconds by default ;)

After about 2.5 hours the drives where synced and ready to be formated with the reiserfs.

```
sudo mkfs -t reiserfs /dev/md0
```

GREAT! We have a virtual drive that is all formated and ready to be mounted. To make things run smooth I edited the /etc/fstab file with gedit...

```
sudo gedit /etc/fstab
```

I added the following line to /etc/fstab ...

```
/dev/md0 /media/raid auto defaults 0 0
```

The above will allow me to use mount -a and have the device mount as /media/raid. Remember to make the /media/raid directory ...

```
sudo mkdir /media/raid
```

Next let's mount the raid device ...

```
sudo mount -a
```

Almost done ... next you will need to use chown to allow writing to the drive by users other than root.

Now you are done.

This worked perfectly for me and runs very well.

Please add comments if I have missed anything ... remember I am very very new to linux and this was my first attempt at creating a software raid 1 with external usb drives.

---

### Post by HalNineThousand on 2007-08-18
What happens if the drives get disconnected and somehow not connected in the same order at some later date?  Do they change device IDs and the RAID stops working?

---

