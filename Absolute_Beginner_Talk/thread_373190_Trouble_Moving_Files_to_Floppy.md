---
title: "Trouble Moving Files to Floppy"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-01
I need some good advice,

1. I am trying to move downloaded files which are on my desktop to my floppy drive. I am told that I do not have permission. See attachment. 

2. How do I make changes to get this permission?

Thanks for your assistance in resolving this matter.
kh

---

### Post by yabbadabbadont on 2007-03-01
Open a terminal window and run, "mount".  Please post the output as well as the contents of your /etc/fstab file.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> Open a terminal window and run, "mount".  Please post the output as well as the contents of your /etc/fstab file.


kittyhawk63@kittyhawk63:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/fd0 on /media/floppy type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
kittyhawk63@kittyhawk63:~$

Not sure how to get the second request done. Need advice there.

---

### Post by yabbadabbadont on 2007-03-01
Ok, in a terminal window run "id", and post the output.  To get the contents of your /etc/fstab file, just open it with gedit.  Don't worry about it being read-only, we're not going to change it.  Then just select all the text, copy, then paste into your post.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> Ok, in a terminal window run "id", and post the output.  To get the contents of your /etc/fstab file, just open it with gedit.  Don't worry about it being read-only, we're not going to change it.  Then just select all the text, copy, then paste into your post.


kittyhawk63@kittyhawk63:~$ id
uid=1000(kittyhawk63) gid=1000(kittyhawk63) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(kittyhawk63)
kittyhawk63@kittyhawk63:~$

 /etc/fstab to follow in next post.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> Ok, in a terminal window run "id", and post the output.  To get the contents of your /etc/fstab file, just open it with gedit.  Don't worry about it being read-only, we're not going to change it.  Then just select all the text, copy, then paste into your post.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by yabbadabbadont on 2007-03-01
Strange.  There is usually an entry in there for the floppy.  Oh well, it appears to be getting mounted correctly.

Try running, "df -h", in a terminal and posting that output please.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> Strange.  There is usually an entry in there for the floppy.  Oh well, it appears to be getting mounted correctly.

Try running, "df -h", in a terminal and posting that output please.

Sorry for the delay. My notifier failed to alert me that you had replied. Here you go.

kittyhawk63@kittyhawk63:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              72G  4.6G   64G   7% /
varrun                252M   76K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  132K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-28-386/volatile
/dev/fd0              1.4M  145K  1.3M  11% /media/floppy
kittyhawk63@kittyhawk63:~$

---

### Post by yabbadabbadont on 2007-03-01
What does, "ls -ld /media/floppy" show?  Can you use the "cp" (copy) command in the terminal to copy the files to the disk?

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> What does, "ls -ld /media/floppy" show?  Can you use the "cp" (copy) command in the terminal to copy the files to the disk?


kittyhawk63@kittyhawk63:~$ ls -ld /media/floppy
drwx------ 4 kittyhawk63 kittyhawk63 7168 1969-12-31 16:00 /media/floppy
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-03-01
I don't know how to use the "cd" in terminal to copy to a floppy or CD.

---

### Post by yabbadabbadont on 2007-03-01
> 1969-12-31 16:00 That doesn't look right...

Just as a test, run "sudo touch /media/floppy" in the terminal window, then try to copy a file to the disk again.  Make sure that the file is small enough to fit in the 1.3M of space that is left.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> That doesn't look right...

Just as a test, run "sudo touch /media/floppy" in the terminal window, then try to copy a file to the disk again.  Make sure that the file is small enough to fit in the 1.3M of space that is left.kittyhawk63@kittyhawk63:~$

I am on my way to trying to copy. Here is the output on the command prompt.

sudo touch /media/floppy
touch: setting times of `/media/floppy': Read-only file system
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-03-01
[quote=kittyhawk63;2229769]kittyhawk63@kittyhawk63:~$

I am on my way to trying to copy. Here is the output on the command prompt.

**Still getting "no permission".**

---

### Post by kittyhawk63 on 2007-03-01
Thought you should see this. This may be my problem. Know how to fix it?

I forgot that I kept seeing this before. Sorry that I missed telling you.

---

### Post by yabbadabbadont on 2007-03-01
Try closing Nautilus, then in the terminal run "umount /media/floppy".  If you don't get any errors from the umount command, eject the floppy and reboot your machine.  Once rebooted, go ahead and put the floppy back in and try to copy your files again, but don't use the right-click->send to floppy (I assume that is what you tried before).  Just select your files then select Copy off the Edit menu.  Then navigate to the floppy disk and take the Paste option off the Edit menu.  Hopefully that will work.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> There's the problem.  Even though mount told us that the disk is mounted 'rw' (read-write), it is really mounted read-only. All right, lets try unmounting the disk and then mounting it again manually and see if it makes a difference.  Run "umount /media/floppy".  If there are no errors then run "mount -t vfat /dev/fd0 /media/floppy".  If there are any errors or warnings, please post them.  If not, try copying the file again.
[B]
Did you see my last post on "Home Folde[/B]r"?

Here's the reply: 
kittyhawk63@kittyhawk63:~$ umount /media/floppy
umount: /media/floppy is not in the fstab (and you are not root)
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> Try closing Nautilus, then in the terminal run "umount /media/floppy".  If you don't get any errors from the umount command, eject the floppy and reboot your machine.  Once rebooted, go ahead and put the floppy back in and try to copy your files again, but don't use the right-click->send to floppy (I assume that is what you tried before).  Just select your files then select Copy off the Edit menu.  Then navigate to the floppy disk and take the Paste option off the Edit menu.  Hopefully that will work.

Here is the reply:
kittyhawk63@kittyhawk63:~$ mount -t vfat /dev/fd0 /media/floppy
mount: only root can do that
kittyhawk63@kittyhawk63:~$

---

### Post by yabbadabbadont on 2007-03-01
I was editing my post when you replied.  Just use "sudo umount /media/floppy" after you close Nautilus.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> I was editing my post when you replied.  Just use "sudo umount /media/floppy" after you close Nautilus.

Sorry, I am a noobie. What do you mean by "after you close Nautilus"?

---

### Post by yabbadabbadont on 2007-03-01
> **kittyhawk63 said:**
> Sorry, I am a noobie. What do you mean by "after you close Nautilus"?

Nautilus is the filemanager that you have been trying to use to copy the files to the floppy.  Close it, then run the "sudo umount /media/floppy" command.  Then, assuming no errors occur, eject the floppy and reboot your computer.  Once rebooted, go ahead and put the floppy back in and try to copy your files again, but don't use the right-click->send to floppy (I assume that is what you tried before). Just select your files then select Copy off the Edit menu. Then navigate to the floppy disk and take the Paste option off the Edit menu. Hopefully that will work.

---

### Post by kittyhawk63 on 2007-03-01
> **kittyhawk63 said:**
> Sorry, I am a noobie. What do you mean by "after you close Nautilus"?

I figured out what Nautilus is and it was closed. I ran the sudo command and here is the reply:

kittyhawk63@kittyhawk63:~$ sudo umount /media/floppy
Password:
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-03-01
Got you last instructions. On my way to rebooting.

---

### Post by kittyhawk63 on 2007-03-01
> **kittyhawk63 said:**
> Got you last instructions. On my way to rebooting.

Rebooted. Same issue. Should I try re-installing Nautilus? Could it get corrupted?

---

### Post by yabbadabbadont on 2007-03-01
> **kittyhawk63 said:**
> Rebooted. Same issue. Should I try re-installing Nautilus? Could it get corrupted?

I'm sorry, I'm out of ideas.  Hopefully someone else will have an idea of what is going on and be able to help you.

---

### Post by kittyhawk63 on 2007-03-01
> **yabbadabbadont said:**
> I'm sorry, I'm out of ideas.  Hopefully someone else will have an idea of what is going on and be able to help you.

Thank you for all your assistance. Even though we did not succeed in resolving my problem, I learned a lot tonight. Thanks again for your time, patience, and sharing some of your knowledge. Good night to you.
kh

---

