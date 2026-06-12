---
title: "hal.dll"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by xRedlinexx1 on 2007-02-10
In a previous post i was having trouble installing ubuntu. Now i have it installed but when i try loading windows from grub i get hal.dll is missing. I was reading this guide [http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing]("http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing")
and i'm having trouble with it. I followed the steps and i get a blank boot.ini. I couldnt find captive ntfs and some of the code i copied over from the guide produced weird results. Could someone provide with a step by step guide because i'm a newb.

---

### Post by risbac on 2007-02-10
Hi there

If you get a blank boot.ini, maybe you are not editing the right file. Windows is unhappy because Ubuntu is now on a partition BEFORE the Windows one. But your installation didn't touch any Windows file, so the boot.ini should not be empty.

I guess you have followed the different steps in the link provided in this chat.
Could you do it again, but after "cd /mnt/windows", just type a "ls".
It should show you the files of your Windows partition's root. If you have nothing, means your windows partition is NOT mounted properly. I think it could be your problem.

You can try to instant message me on ICQ or MSN if you prefer, that will be faster. But I'm not online often this week-end.

---

### Post by xRedlinexx1 on 2007-02-10
This is what i get in the terminal.


sudo -i
root@eric-laptop:~# cd /mnt Is
root@eric-laptop:/mnt# mkdir windows
mkdir: cannot create directory `windows': File exists
root@eric-laptop:/mnt# mount -t ntfs /dev/sda2/mnt/windows
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@eric-laptop:/mnt#

It might not be working because i dont understand how to install and use captive ntfs.

---

### Post by risbac on 2007-02-10
Ok, easy easy:

> root@eric-laptop:~# cd /mnt Is

Usually you mount things in /media... So I would go instead for a

> cd /media


> root@eric-laptop:/mnt# mkdir windows
mkdir: cannot create directory `windows': File exists


obviously, this one didn't work... 

Go for a :

> sudo mkdir windows


(sudo to have enough rights to write in this directory. Will ask you your password).

> root@eric-laptop:/mnt# mount -t ntfs /dev/sda2/mnt/windows
Usage: mount -V : print version

This one didn't work either, it gives you the manual to help you fixing it :)

A space is missing, should be:

> mount -t ntfs /dev/sda2 /media/windows

I replaced "mnt" by "media", as we are mounting the windows partition in media now.

It should help, now your boot.ini should have some content. I'm off to sleep now, I'm sure you will find plenty of help here if it still doesn't work.

Have fun!

---

### Post by risbac on 2007-02-10
> It might not be working because i dont understand how to install and use captive ntfs.

That could be another problem... Now you should be able to READ your NTFS partition, but not to write on it. But let's go step by step :)

---

### Post by xRedlinexx1 on 2007-02-10
I did everything you said and i got a boot.ini with only the line of code i need. However when i try to  save it, it says it's read only. 
Heres what i put in my terminal:

sudo -i
root@eric-laptop:~# cd /media
root@eric-laptop:/media# sudo mkdir windows
root@eric-laptop:/media# mount -t ntfs /dev/sda2 /media/windows
root@eric-laptop:/media# cd /media/windows
root@eric-laptop:/media/windows# cp boot.ini /home/eric/boot.ini
root@eric-laptop:/media/windows# cp boot.ini /home/eric/boot.ini.bak
root@eric-laptop:/media/windows# cd /home/eric
root@eric-laptop:/home/eric# gedit boot.ini
root@eric-laptop:/home/eric# cd /media/windows
root@eric-laptop:/media/windows# cp boot.ini /home/eric/boot.ini
root@eric-laptop:/media/windows# cp boot.ini /home/eric/boot.ini.bak
root@eric-laptop:/media/windows# cd /home/eric
root@eric-laptop:/home/eric# sudo gedit boot.ini
root@eric-laptop:/home/eric# 

Thanks for the fast replies

(EDIT) I now understand i need to use a program to write to ntfs partitions. However I've tried installing them and i'v had no luck.

---

### Post by xRedlinexx1 on 2007-02-10
bump

---

### Post by risbac on 2007-02-11
Ok.

After "cd /media/windows"

can you do a 

> ls -l

It should show you the list of files in your windows partition. If you don't see a "boot.ini" file there, then we have a problem.

If you see it, then the other commands should be fine. The file should contain more than one line though. Mine is looking like that:

> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP dition familiale" /noexecute=optin /fastdetect


Yours should look more or less like this.

If that's the case, now we need to see to write on the NTFS partition. That will be for next post :)

---

### Post by risbac on 2007-02-11
To write to NTFS, there is this Captive software, but you have to compile it. That's a bit complicated for a newbie, so I would prefer to do it the easy way.

Which version of Ubuntu do you have? Dapper (6.06) or Edgy (6.10)? If it's Edgy, it should be quite easy to install the software. I'm crossing my fingers!

---

### Post by xRedlinexx1 on 2007-02-11
I got a boot.ini with this in it:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


I have edgy installed and i see boot.ini in the windows folder.

---

### Post by xRedlinexx1 on 2007-02-11
bump

---

### Post by shareMenaPeace on 2007-02-11
> **xRedlinexx1 said:**
> root@eric-laptop:/home/eric# sudo gedit boot.ini
root@eric-laptop:/home/eric# 

Thanks for the fast replies

(EDIT) I now understand i need to use a program to write to ntfs partitions. However I've tried installing them and i'v had no luck.
Use 
```
gksudo gedit /path/to/file

```
And what is the prblem now you couldnt save the file?

---

### Post by risbac on 2007-02-11
Ok, so you can access to the content of your boot.ini, and fix it.

Now you need to replace it on your Windows partition. INstead of CaptiveNTFS, I think you should use NTFS-3G. 

Here is a guide:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS-3G](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS-3G)

NTFS-3G is in the repositories of Ubuntu, but that's an old version. That's probably better to install a new one. Then you have a tool to mount your partitions. 

Once that's done, normally you can write on your NTFS partition. Just try to create a new directory to see if it works. If it does, takes the boot.ini file from your desktop, and copy it at the root of your NTFS partition, to replace the existing one. Then reboot, and see if Windows feels better.

---

### Post by xRedlinexx1 on 2007-02-11
I tried this earlier. I installed it then ran it, but when i checked off the first setting and hit okay i got an error message saying i have to force mount or something.

(EDIT) it said ntfs was unclean. I have searched around and tried a method by one user. He said he put in his windows disk to get to a cmd promt and typed in chkdsk. I tried this but the cd started to setup for installation. I exited out and now my desktop in ubunto has my windows and back folders on it.

---

### Post by xRedlinexx1 on 2007-02-11
bump

---

### Post by risbac on 2007-02-12
> I tried this earlier. I installed it then ran it, but when i checked off the first setting and hit okay i got an error message saying i have to force mount or something.

Yes, that's an "usual" message when it tries to mount an NTFS partition which was not unmounted properly.

To fix this, I think there is an easy solution.
Try this:

> sudo ntfs-3g /dev/hda2 /media/windows -o force

With "/dev/hda2" being an example, it's maybe something else for your Windows partition. Change it accordingly. The "force" option will make sure we don't care about the NTFS partition being unclean.

Then it should mount your NTFS partition into /media/windows, and you can write on it. If you don't have any error message when running this command, then try then a simple:

> sudo cp /home/eric/boot.ini /media/windows/
It will try to copy the modified boot.ini to the NTFS partition.

If it works, your boot.ini is now modified on your windows partition, and Windows will understand again how to run itself.

---

### Post by xRedlinexx1 on 2007-02-12
I tried the first line of code you gave me and i get this

Mounting /media/windows failed.

fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/sda2 ()

Then it says in the ntfs confg tool:

Mounting /media/Backup failed.

Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.

Also i found out that i can boot into a mcafee system recovery tool. It can bring the computer back to various dates and fix other errors. Would recovering my system to another date possibly set the boot.ini back to it's original state?

---

### Post by risbac on 2007-02-12
I don't think that recovering the boot.ini to a previous version would work... Windows is just unhappy with the repartitioning of the disk and can't find its own files on the disk from what I understand. So the only way to boot it is to fix the boot.ini with the correct partition info.

I think I know why the command failed. You already mounted the Windows partition in /media/windows, so it doesn't want to mount it again.

So let's make sure it's not mounted anymore:

> sudo umount -a 

Means "unmount everything"

Then 

> sudo ntfs-3g /dev/sda2 /media/windows -o force

again.

This time there should not be any error message. Then you can copy the boot.ini you have fixed to the root folder of the Windows partition:

> sudo cp /home/eric/boot.ini /media/windows/

---

### Post by xRedlinexx1 on 2007-02-12
i'm getting this:

root@eric-laptop:~# sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy
root@eric-laptop:~#

then this:

root@eric-laptop:~# sudo ntfs-3g /dev/sda2 /media/windows -o force
WARNING: Deficient FUSE kernel module detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. The safe FUSE kernel
         driver is included in the official Linux kernels since version
         2.6.20-rc1, or in the FUSE 2.6.0 or later software packages,
         except the faulty FUSE version 2.6.2. For more help, please
         have a look at /usr/share/doc/ntfs-3g/README.Debian. Thanks

---

### Post by risbac on 2007-02-13
Arghhh. Can we rename this post "Linux/Windows collaboration, learn it the hard way"????

Question, the message after the umount doesn't seem that bad, can you just check that there is nothing in /media/windows? (before doing the ntfs-3g command of course)


Then about the NTFS-3G error. I have it also if I try the same installation as I gave you, but it still gives access to the Windows partition. So check if you see files in /media/windows

If it's the case, then try to do the sudo cp command. If you don't have any error message, reboot, and try to run Windows.

---

### Post by xRedlinexx1 on 2007-02-13
Okay i did what you said and it let me change the boot.ini. Now when i load into grub and go into windows home adition i get two more choices. These are winows default and windows home adition. Both come up with hal.dll missing. I think i need to unmount or something.

---

