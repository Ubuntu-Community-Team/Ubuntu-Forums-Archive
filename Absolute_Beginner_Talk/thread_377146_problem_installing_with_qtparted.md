---
title: "problem installing with qtparted"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by airdelroy on 2007-03-05
I am having a problem installing 6.10 dvd on my system.  I have several partitions and I am choosing to manually setup the partition stuff.  Before it lets me edit anything it gives me the following warning:

 "Cannot unmount partition device: /dev/hda9.Please do it by hand first to commit the changes!"

Nothing on hda shows up in mount:
root@ubuntu:~# mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

The install program exits without installing after I setup the partition stuff.  It also gives me the above warning a few more times before exiting.

Anyone know how to get around this?  Maybe I should install text...

---

### Post by airdelroy on 2007-03-05
Well, I have tried it again and it looks like it is working this time.  The only thing that I can think of that I have done differently is to bring up an internet connection to post this thread.  Perhaps I should have tried running the install in a console to look for an abnormal exit/error.

---

