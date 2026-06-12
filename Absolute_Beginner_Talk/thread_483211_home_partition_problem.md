---
title: "/home partition problem"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-06-24
Ok, when I installed Ubuntu, I was foolish enough to not make a separate home partition, which I am now regretting, because I want to move from 32-bit to 64-bit Ubuntu.

So after some searching, I found [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").
After making the partition and starting the process of the loads of commands that I need to use, I got stuck on this one:
```

find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/

```
The error I get says:
```

cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

```

I've never used 'cpio' before so I have no idea what the problem is, or how to fix it.

---

### Post by BobCFC on 2007-06-24
I followed that tutorial a few months ago it does work well but there is a problem with the fonts on that page... The two long dashes infront of null and sparse should actually be double --

eg

```
find . -depth -print0 | cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome
```


The extra bit preserve-modification-time does exactly what it says on the tin.. keeps you old files with the same dates.


PS I have also recently gone 64bit... You will want to use the [script on this page]("http://ubuntuforums.org/showthread.php?t=425672") to get Flash Plugin working in 64bit Firefox so that you can watch YouTube/Google video.. It works like a charm not difficult.

---

### Post by Hobo Joe on 2007-06-24
> **BobCFC said:**
> I followed that tutorial a few months ago it does work well but there is a problem with the fonts on that page... The two long dashes infront of null and sparse should actually be double --

eg

```
find . -depth -print0 | cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome
```


The extra bit preserve-modification-time does exactly what it says on the tin.. keeps you old files with the same dates.


PS I have also recently gone 64bit... You will want to use the [script on this page]("http://ubuntuforums.org/showthread.php?t=425672") to get Flash Plugin working in 64bit Firefox so that you can watch YouTube/Google video.. It works like a charm not difficult.

Ahhh, that fixed it, thanks a lot!

Thanks for the link to, thats the only thing I'm a little intimidated by for 64-bit, hopefully it won't be to hard though. :)

---

### Post by Hobo Joe on 2007-06-24
Wait, the command ran, but I got a HUGE amount of errors. In fact, I think every single line is an error.

For example, they look like this:
```

cpio: ./joseph/.kde/share/apps/amarok/submit.xml: Permission denied

```
They all look like that, with some variation, such as 'Operation not permitted', or 'No such file or directory'.

Any ideas as to what would be causing that?

I tried running it with sudo, but it still did the same thing.

---

### Post by Happy_Man on 2007-06-24
I actually transferred my /home over with [http://psychocats.net/ubuntu/seperatehome](http://psychocats.net/ubuntu/seperatehome). Worked like a charm... try that and see what it does.

---

### Post by Hobo Joe on 2007-06-24
> **Happy_Man said:**
> I actually transferred my /home over with [http://psychocats.net/ubuntu/seperatehome](http://psychocats.net/ubuntu/seperatehome). Worked like a charm... try that and see what it does.

On that guide, I see a whole lot of references to partition numbers, which I know I'm going to have to change in the commands, but how do I know which is which?
For example, one of the commands says:
```

sudo mount -t ext3 /dev/hda1 /old

```
Ubuntu is installed on sda2 for me, and the new partition is sda4, but I'm not sure if this command is for the partition that Linux is installed one, or if it's for the one that I just made for my home folder.
(sorry if that isn't very clear. :()

---

### Post by Happy_Man on 2007-06-24
Run the command ```
sudo fdisk -l
``` and post it here. I'll try and customize the commands for you.

---

### Post by Hobo Joe on 2007-06-24
> **Happy_Man said:**
> Run the command ```
sudo fdisk -l
``` and post it here. I'll try and customize the commands for you.

I can do it myself, becuase I know that would take a little work, I just need a little verification as to which is which.

In the guide, I see 'hda1', and 'hda7' I ASSUME that hda1 is the partition that the OS is installed on, and that hda7 is the one made for the home partition.

But if you insist, here is the output. :)
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12685   101892231    7  HPFS/NTFS
/dev/sda2           12686       26218   108703822+  83  Linux
/dev/sda3           38210       38913     5654880    5  Extended
/dev/sda4           26219       38209    96317707+  83  Linux
/dev/sda5           38210       38913     5654848+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
Don't feel obligated to do it all for me if you don't want, I kind of want to learn how to do this stuff anyway. ;)

---

### Post by BobCFC on 2007-06-24
hdXX is for old IDE drives sdaX is for new SATA

---

### Post by Hobo Joe on 2007-06-24
> **BobCFC said:**
> You need to be root for permissions error.

 type su and enter root password before typing commands or prefix each command with sudo which takes your ordinary user password

I tried that, but I still got the permission's error.
> 
I tried running it with sudo, but it still did the same thing.


EDIT:

I'm and idiot, on that page, he tells me:

> Now, in my example, my original partition that I shrunk was /dev/hda5, and it created a new partition called /dev/hda7, and my /home folder lives on /dev/hda1. It's very important that you substitute in your own appropriate partition names for the ones I'm using--you most likely will have only two partitions you're dealing with--the one you shrunk and the newly created one.

I guess that's what I get for not reading carefully!
Thanks for your help guys, I'll post back with the results. :)

EDIT:
I also figured out why I had messed up with the permissions on that one command, when I said I had tried to run it as root, I had just put sudo at the beginning of the command, but I was supposed to put sudo before cpio, rather that just at the beginning of the line.
Man I'm learning a lot!

---

### Post by Happy_Man on 2007-06-24
Good for you, buddy. I'll just tell you a couple things, and move on.

*guessing here, but it's an educated guess* sda2 is the partition Linux is currently on, sda4 is where you want /home.

---

### Post by Hobo Joe on 2007-06-24
> **Happy_Man said:**
> Good for you, buddy. I'll just tell you a couple things, and move on.

*guessing here, but it's an educated guess* sda2 is the partition Linux is currently on, sda4 is where you want /home.

CRAP!

I'm in big trouble. REALLY big trouble. I'm one the part where I'm supposed to edit the fstab file, but I accidentally closed the terminal, but now it won't open, and everthing looks weird, and the music that I had playing the background stopped and I can't open the terminal. 

PLEASE HELP!!!

---

### Post by Happy_Man on 2007-06-24
You are running from a LiveCD, right?

---

### Post by Hobo Joe on 2007-06-24
.....Ummmm, I am now....

I'm trying his recovery method that's at the end of the guide.
```

sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

```

---

