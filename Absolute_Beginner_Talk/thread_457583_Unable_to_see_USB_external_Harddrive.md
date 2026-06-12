---
title: "Unable to see USB external Harddrive"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by EpsilonExordium on 2007-05-28
Hello all! I have been using Ubuntu Feisty Fawn since yesterday. Today I noticed that my USB external harddrive is not being recognized. I tried searching the forums to see if any posts could help my situation, but I came up with nothing. Fdisk -l gives the following:

doug@fresh:~$ fdisk -l

Disk /dev/sdb: 122.9 GB, 122942324224 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System


Please help!

---

### Post by taurus on 2007-05-28
Is there any filesystem on /dev/sdb?

---

### Post by EpsilonExordium on 2007-05-28
> **taurus said:**
> Is there any filesystem on /dev/sdb?

Should be either NTFS or Fat32 - the drive works fine in windows, and is filled with content. 

Is this what you wanted to know?

---

### Post by taurus on 2007-05-28
Maybe you need to connect it to a Windows and defrag and scan it.  Then, connect it back to Feisty and see if Ubuntu will see the drive now.

---

### Post by jackiecanev2 on 2007-05-28
if it is ntfs filesystem, and it most likely is, you have to enable ntfs config to be able to read/write to the drive. search for ntfs in add/remove.

---

### Post by EpsilonExordium on 2007-05-28
NTFS Config is already enabled. Also, there are no issues with fragmentation or any other disk issues. I can plug into my windows box just fine. Is there a way to manually mount the drive?

---

### Post by taurus on 2007-05-28
Can't mount it if Ubuntu doesn't see it.  You can try something like

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sdb1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by EpsilonExordium on 2007-05-28
Okay, I ran NTFS config and recieved this error message:

Mounting /media/DougExternal failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

---

### Post by taurus on 2007-05-28
You can try to use the commands in my previous post or you need to boot back into Windows and shut Windows down properly (no hibernation stuff).

---

### Post by EpsilonExordium on 2007-05-28
THis is what I get:

doug@fresh:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists

For the second two lines:

doug@fresh:~$ sudo mount -t ntfs /dev/sdb1 /media/windows -o nls=utf8,umask=0222mount: special device /dev/sdb1 does not exist
doug@fresh:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              16G  2.6G   13G  17% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  144K 1014M   1% /proc/bus/usb
udev                 1014M  144K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              40G  6.2G   33G  16% /media/DougExternal
doug@fresh:~$ 


Also, I tried to run NTFS config tool again, rebooted, and did a proper shutdown in windows. Now I have a "DougExternal" mount on my desktop. When I double click on it, it leads to my windows partition on my laptop harddrive (not the external)

---

### Post by taurus on 2007-05-28
Try to use the option _Safely Remove Hardware_ icon in the Windows taskbar notification area before disconnecting it to unmount your external harddrive when you are in XP.  Then, boot back into Ubuntu and see if you can mount it this time.

---

### Post by EpsilonExordium on 2007-05-28
> **taurus said:**
> Try to use the option _Safely Remove Hardware_ icon in the Windows taskbar notification area before disconnecting it to unmount your external harddrive when you are in XP.  Then, boot back into Ubuntu and see if you can mount it this time.

I did this the last time I booted.

I just swapped the disk in the external with another. This time, as soon I plugged it in I got a message stating, "Cannot mount Volume - - Unable to mount the volume."

Under details it gave an identical message as the one I recieved before when running the NTFS config

---

### Post by EpsilonExordium on 2007-05-28
Okay, I gave up and wiped the drive clean. What is the best way to partition this drive so it can be used in windows AND linux? It's 120gb

---

### Post by taurus on 2007-05-28
Use gparted (System -> Administration) to format it to vfat.  The only problem is that you cannot save files over 4GB on vfat filesystem.

---

### Post by EpsilonExordium on 2007-05-28
> **taurus said:**
> Use gparted (System -> Administration) to format it to vfat.  The only problem is that you cannot save files over 4GB on vfat filesystem.

thanks!

---

