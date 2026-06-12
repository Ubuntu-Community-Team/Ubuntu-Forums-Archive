---
title: "Mount problems"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Jim Jesus on 2008-02-09
So I just installed Ubuntu 7.10 and I am having trouble mounting my ntfs partitions. When I try and manually mount them, I get this error.
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

```
Also, my other partitions don't show up on the side bar of my file browser.

---

### Post by taurus on 2008-02-09
You need to boot into windows and shut it down cleanly which means _no_ hibernation or sleep mode.  Then, you should be able to mount your ntfs again in Ubuntu.

---

### Post by kestrel1 on 2008-02-09
Have you tried booting in to Windows & safely removing the hard drives?

---

### Post by jan quark on 2008-02-09
can you post the output of these commands

but before that do what the error message tells you to do boot into windows and shutdown properly
```
mount 
```
```
sudo fdisk -l
```
```
cat /etc/fstab
```

```
df -h
```

---

### Post by kevstar31 on 2008-02-09
if it works when you run *mount -t ntfs-3g /dev/sda1 /media/sda1 -o force* then run *echo "/dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0"  >> /etc/fstab* to make it mount automatically.

---

### Post by happysmileman on 2008-02-09
> **kevstar31 said:**
> if it works when you run *mount -t ntfs-3g /dev/sda1 /media/sda1 -o force* then run *echo "/dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0"  >> /etc/fstab* to make it mount automatically.

That may corrupt the data if the drive really is in use somehow, I know it's unlikely but it's possible, so it'd be a lot safer to try fix it than it would to workaround it like this.

---

### Post by lespaul_rentals on 2008-02-09
You can force it to mount by running the following:

```
ntfs-3g -o force /dev/sda1 /media/sda1
```

Where "sda1" is the name of your device.

Note that I am not responsible for any data corruption that may occur.  I would recommend booting into Windows, and running:

```
chkdsk /f <drive letter>
```

Remember that Microsoft's crappy NTFS file system is prone to "dirty tables" so you will be doing this a lot, whether you properly remove your drives or not.

---

### Post by Jim Jesus on 2008-02-09
Thank you for all the help guys. I booted into windows and shut it down properly and then reran the mount commands and it works.

---

