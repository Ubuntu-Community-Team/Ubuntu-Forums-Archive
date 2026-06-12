---
title: "GRUB error 17 on bootup..."
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-27
This sucks!

So I noticed right before I restarted, I could not open any files. As if they lost all their properties or something. On a restart, I got the error 17...

This is not the first time this HD has crashed, and I am thinking its bad. I bought it new not more then a year ago, but it does this every few months...

I tried fdisk -l, but nothing showed up. I have the /home on a separate partition, but its on the same HD. I really hope I can salvage it...

Stupid Seagate...

btw, on a LiveCD now.

edit: int he pic, the 9gig is the /, and the 93 the /home.

---

### Post by Pragmatist on 2007-07-28
Here is a useful reference for GRUB errors:
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html#SEC101](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html#SEC101)

For GRUB error 17:
> 
17 : Cannot mount selected partition  This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.Try using fdisk to find out what linux thinks your partition types are (if your hard drive isn't at /dev/hda, substitute its real location in the following command):
```
sudo fdisk /dev/hda
```
Now type: p   (lowercase P)
Now type: q   (lowercase Q)

Now cut-and-paste the table here so we can see it.

---

### Post by FleetAdmiral74 on 2007-07-28
```
ubuntu@ubuntu:~$ sudo fdisk /dev/hdb

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1216     9767488+  83  Linux
/dev/hdb2            1217        1338      979965   82  Linux swap / Solaris
/dev/hdb3            1339       13496    97659135    5  Extended
/dev/hdb5            1339       13496    97659103+  83  Linux

Command (m for help): q

ubuntu@ubuntu:~$ 

```

1 is the root, 2 the swap obviously and 5 (in the 3 extended partition) the /home dir

Thanks for the response.

---

### Post by Pragmatist on 2007-07-28
Ok, now let's see your grub configuration file: **/boot/grub/menu.lst**

---

### Post by FleetAdmiral74 on 2007-07-28
Hmm...I am a bit confused on how to do that. If its in /boot (in the hdb drive where Ub was installed), how do I read that? Isn't the problem I cant read it at all?

Maybe I didn't make it clear actually...I cant access any data on there, the prob is not just that it won't boot correctly.

Apologies for the confusion.

---

### Post by Pragmatist on 2007-07-28
> **FleetAdmiral74 said:**
> 
Maybe I didn't make it clear actually...I cant access any data on there, the prob is not just that it won't boot correctly.


No, you made it clear, it is my mistake.  I was on autopilot and just automatically asked to see menu.lst  I did that since, when troubleshooting boot problems, I nearly always need to see it.

The LiveCD doesn't mount it either, huh?  Can you manually mount any of the partitions?  For example, can you mount your home partition with the LiveCD.  The way you manually mount is like this:

First, find an unused mount directory in /media.  Let's say there is a directory called "hd1" inside /media.  

Next, you mount the partition by typing this:

```
sudo mount /dev/hdb5 /media/hd1
```

Then you browse the partition to see if it worked:
```
cd /media/hd1
```
```
ls -l
```

Notes:  
1.  Depending on the LiveCD you may need to type su first and then run the command next, rather than using sudo in front of the command.  Or, you may not need to use either if the LiveCD automatically makes you the root user.

2. If your not sure there is an empty directory inside /media, then type:
```
mount
```
and see if the mount point is being used.  If the directory is empty, don't worry about what it is called.  You can mount your hard drive partition on any empty directory, anywhere, but it is conventional to use /media

---

### Post by Sef on 2007-07-28
>  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1216     9767488+  83  Linux
/dev/hdb2            1217        1338      979965   82  Linux swap / Solaris
/dev/hdb3            1339       13496    97659135    5  Extended
/dev/hdb5            1339       13496    97659103+  83  Linux

Do you have 2 hard drives?

Your list indicates that you have 2 of them.

---

### Post by FleetAdmiral74 on 2007-07-29
I do. I have the hda, which at the time had one ext partition where I had a partial backup of the data. It gets more complicated from here...

I just installed Ub on the remaining free space on the first HD. It boots up correctly, but only after going through some error requiring a fcsk to be run and errors corrected. I also remember something about large blocks being found, but the proper flag not enabled. After that when I typed reboot, it started initializing all the services instead of rebooting and brings me to the login screen where I can boot up normally from the HD.

Weird, no?

edit: To pregmatist,```
ed@ed-desktop:~$ sudo mount /dev/hdb5 /media/hda1
mount: you must specify the filesystem type

```

---

### Post by Pragmatist on 2007-07-29
Try it this way:

```
sudo mount -t ext3 /dev/hdb5 /media/hda1
```

---

### Post by FleetAdmiral74 on 2007-07-29
```
ed@ed-desktop:~$ sudo mount -t ext3 /dev/hdb5 /media/hda1
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ed@ed-desktop:~$ dmesg | tail
[ 1651.300000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1651.304000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1651.304000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1771.716000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1771.716000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1773.832000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1773.832000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
**[ 1774.072000] VFS: Can't find ext3 filesystem on dev hdb5.**
[ 1789.348000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1789.348000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
ed@ed-desktop:~$ dmesg | so
bash: so: command not found

```

I think thats the problem...and I know its an ext3.

That other stuff is not important, just some bad key on my keyboard, so don't worry about it :)

---

### Post by FleetAdmiral74 on 2007-08-01
Hey guys. Still looking forward to hearing back from ya...anyone...help?

---

### Post by alienexplorers on 2007-08-01
Insert your Live-CD and boot.  Enter terminal and type sudo grub
Enter:
> find /boot/grub/stage1
You should get an output like (hdx,y)
Enter:
> root (hdx,y)
setup (hdx)
quit grub
reboot

---

