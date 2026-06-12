---
title: "[SOLVED] QEmu 0.9.0 CDROM boot Help"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by gmjs on 2007-04-12
Hi,

I've recently installed QEmu 0.9.0 and would like to test it by installing a copy of Windows 98 as a virtual machine.

However, I can't get QEmu to boot from the CDROM drive.  I've read several posts that have suggested adding a switch that tells QEmu which device to use as the CDROM drive, but while this has helped some people, it has not solved the problem for me.

I haven't installed KQEmu.  Perhaps this is where I'm going wrong?

I'm using the following command line, both with my login and as root with the same outcome:

**$ qemu -hda /home/graham/IMG/win98.img -m 128 -cdrom /dev/cdrom -boot d**

I am confident that /dev/cdrom is the correct device and I created the win98.img file in both the raw format and qcow format to see if this made a difference, which it did not.

QEmu returns the following error:

[B]CDROM boot failure code : 0003 
Boot from CD-Rom failed
FATAL: Could not read the boot disk[/B]

The QEMU BIOS was built on 11/01/06, revision 1.174 (20061017) if it helps!

Also, as an aside (sorry, this post's getting a bit too long) the terminal window creates the following 'non-fatal' error:

[B]Could not configure '/dev/rtc' to have a 1024 Hz timer. This is not a fatal
error, but for better emulation accuracy either use a 2.6 host Linux kernel or
type 'echo 1024 > /proc/sys/dev/rtc/max-user-freq' as root.[/B]

Can anyone suggest what this means?!  I understand that this line would update a file so that it's contents would be changed to the value '1024', but what is it for and what effect will changing this value have on the running of my system?


Many thanks,

Graham

---

### Post by Jonam on 2007-04-15
I have Qemu installed with a Win98 virtual machine running and no KQemu. Checking what you have done against what I had done, the only difference appears to be the memory allocation command. This should not cause the CDROM errors. I did get the timer error message but did not worry about it.

I will try running Qemu with CDROM emulation to see what results and post back.

Jonam

---

### Post by Jonam on 2007-04-15
Having not used Qemu for a while, I tried to boot it with CDROM support and the following happened:

```
mvr@mvr-desktop:/media/cdrom$ qemu -boot c -usb -soundhw sb16 -cdrom /dev/cdrom0 -hda /home/mvr/qemu/hd.img
qemu: could not open hard disk image '/dev/cdrom0'
```

I had a disk in the drive when I did this (Win98 Install disk).

I then ran the mount command to see how this drive appeared in the mount list and found the following:

```
mvr@mvr-desktop:/media/cdrom$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hdb1 on /media/hdb1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdd1 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
**/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=mvr)**
```

The last line shows cdrom0 appearing as /dev/hdc. I re-ran Qemu with /dev/hdc instead of /dev/cdrom0:

```
mvr@mvr-desktop:/media/cdrom$ qemu -boot c -usb -soundhw sb16 -cdrom /dev/hdc -hda /home/mvr/qemu/hd.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated
```

Qemu started up OK and could read the CDROM. Suggest you check where your CDROM is mounted and adjust Qemu command line accordingly.

Jonam

---

### Post by gmjs on 2007-04-16
Thanks so much Jonam!  It works!  I'm using /dev/hdd instead of /dev/cdrom and it is all working as it should.

Thanks,

Graham

---

### Post by Jonam on 2007-04-16
No problem. Glad I could help.

Jonam

---

