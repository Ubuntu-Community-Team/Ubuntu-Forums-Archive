---
title: "USB Stick mounting problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-08
I don't know why this is happening. Everything was ok until now. 

All of sudden, my USB stick doesn't mount automatically. And I get the following error message:

mount_point cannot contain the following characters:
newline, G_DIR_SEPARATOR (usually /)

I searched for an answer and I mounted usb stick manually by using 'sudo' power in the terminal. Yes, it is mounted now. But.. 

Now i tried to create a folder in the usb stick but I don't get to have a permission to do so. I have other storages mounted in /media. Their ownership is 'root' but I can still write on each storage. but I just can't do it in the USB Stick.

I even tried to change the ownership of a folder that I'd like to create files in. But what I get is 

mark@mark-laptop:/media/TITANIUM2GB$ sudo chown mark:root My_Career
chown: changing ownership of `My_Career': Operation not permitted


Before everything was fine. Why is this thing happening?  What can I do??

---

### Post by mikeyphi on 2008-01-08
Try changing ownership of the 'Partition' on the USB instead of just the folder.

---

### Post by philinux on 2008-01-08
Try

sudo chown -R yourusername /media/TITANIUM2GB

---

### Post by vanadium on 2008-01-08
If you changed the name of the USB after right-clicking in "Places - Computer", then that might be the problem. In that dialog, you should enter a single label, not a path. Preferably, do not use spaces. The problem is that that dialog lets you enter anything, including a path such as /media/My_Disk, while only a single label (for example "My_Disk") is valid.

---

### Post by GepettoBR on 2008-01-08
If you can't change the ownership, you can create a launcher with the command ```
sudo nautilus /
```, which will open nautilus in superuser mode and allow you to do just about anything to just about any folder or file. Just be careful not to screw up your system by accident.

---

### Post by vanadium on 2008-01-08
There are as many different advises as there are answers. I recommend trying to fix the automatic mount problem first, as this will solve all other issues as well. In any case, refrain from "fixing' it by working as root all the time.

---

### Post by taekr on 2008-01-08
> **philinux said:**
> Try

sudo chown -R yourusername /media/TITANIUM2GB

I tried it. but not working. No permission to change eve if I use 'sudo'. That's weird~

---

### Post by taekr on 2008-01-08
> **GepettoBR said:**
> If you can't change the ownership, you can create a launcher with the command ```
sudo nautilus /
```, which will open nautilus in superuser mode and allow you to do just about anything to just about any folder or file. Just be careful not to screw up your system by accident.

Thanks. But I guess this is only a temporary solution. In fact, I prefer not to use this method. Anyways, thanks.

---

### Post by taekr on 2008-01-08
> **vanadium said:**
> There are as many different advises as there are answers. I recommend trying to fix the automatic mount problem first, as this will solve all other issues as well. In any case, refrain from "fixing' it by working as root all the time.

You are right. Thus, I need help. : (

---

### Post by vanadium on 2008-01-09
Then reread my first post and try my instructions if you want help from me.

---

### Post by taekr on 2008-01-09
> **vanadium said:**
> If you changed the name of the USB after right-clicking in "Places - Computer", then that might be the problem. In that dialog, you should enter a single label, not a path. Preferably, do not use spaces. The problem is that that dialog lets you enter anything, including a path such as /media/My_Disk, while only a single label (for example "My_Disk") is valid.

I don't think I fully understand your instruction. 

I'm not sure if this is what you are talking about.. ..   Before the memory stick's name was READYBOOST. Because I didn't know how to change the name, I used my friend's computer (with XP) to change the name to TITANITUM2GB(without a space)

I plugged into my computer and Ubuntu was able to automatically mount it. And I was using it...   One thing I noticed is that Ubuntu does not have USB devices mounted all the time. I mean when I connect USB Harddisk, sometime later, it is unmounted. 

The same thing happened..  I found that the memory stick was unmounted after I watched a 2 hour movie. I simply replugged it and the error occurred.

I think this is the full story. 

Any suggestions?

---

### Post by vanadium on 2008-01-11
Let us look at some output to see if this gives hints about the possible cause of the problem (I am assuming that you still have the problem posted in your first post, i.e., the USB does not automatically mount anymore). Plug in your USB, open a terminal, type following commands and post all console output here:

sudo fdisk -l
mount
blkid
ls -l /media

The first command lists all drives along with their partitions, the second lists the mounted partitions, the third lists the attributes of your drives, the fourth one lists the details of the directory where removable devices are automatically mounted.

---

### Post by Ferio on 2008-03-08
Same exact problem here, now I've to mount my USB stick manually and I'd like to get a fix for this!

---

### Post by rkd on 2008-03-08
Since you didn't say what you've tried, I have to ask: Have you tried any of the suggestions mentioned earlier in this thread?  If not, some of them might help you.  Tell us what you have tried and what difference, if any, it made.

If the earlier suggestions don't fix it for you, we need to collect some information.  Go look at post #12 (by vanadium) in this thread and follow his directions.  Note that you should do those commands after plugging in your USB drive but without trying to mount it manually.

In addition to the information vanadium shows you how to collect, I'd suggest a little more: Post the contents of /etc/fstab, and look at the system log file.  For the first, just open /etc/fstab in your favorite editor, select and copy all of it, and paste that into a post here.  To look at the system log, go to System -> Administration -> Log Viewer. When it opens, find and click on syslog in the left panel.  Then scroll down to the end of the messages and note the last message there and its timestamp.  Do this before plugging in your USB drive.  You can minimize the log viewer window at this point if you don't want it, but it doesn't hurt to leave up on the screen -- you can then see any messages as soon as they appear.

When you have plugged in the drive and collected the information as vanadium described, go look in the log viewer window and see whether any new messages have appeared in the log viewer.  If so, copy them and paste them into the post along with the other information.

---

### Post by rmtatum on 2008-03-08
I have the same problem.  The usb flash drive automounts as read only.  I cannot write files as root (using sudo).  

My fstab is as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=476c1272-2814-44b7-8317-9a3e88679835 /               ext3    errors=remount-ro 0       1
# /dev/sda3
UUID=43202d87-00d7-4d10-a273-66c6a5f23866 /home           ext3    defaults        0       2
# /dev/hda1
UUID=8ef8aeb4-9d5b-4a7b-9969-bd8c5a45da00 /media/hda1     ext3    defaults        0       2
# /dev/hda6
UUID=6b0f197d-7e00-4cc8-b901-abf918eafeae /media/hda6     ext3    defaults        0       2
# /dev/hda5
UUID=1641a1eb-669c-4bc7-84b7-0e6633b30f12 none            swap    sw              0       0
# /dev/sda2
UUID=5692b0f7-dd22-4a50-ba8b-37cef5d777ee none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#usb mount, added for virtualbox usb support
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0


I modified /etc/init.d/mountdevsubfs.sh and /etc/udev/rules.d/40-permissions.rules to make usb work with VirtualBox.

---

### Post by rmtatum on 2008-03-08
Reformatting the flash drive fixed my read only issue.

---

### Post by smoka on 2008-03-21
The quickest way I've found to fix this problem (it's happened to several of my USB sticks) was to connect it up to one of my WinXP machines and run chkdsk /f on the drive.

Plugged it back into my Ubuntu Machine (Gutsy Gibbon) and it mounted it correctly with read/write instead of just read only as it had been doing.

I'm wondering if anyone has a nice ***quick and simple*** solution for a fix without having to depend on a Windows box to fix this problem every time.

---

