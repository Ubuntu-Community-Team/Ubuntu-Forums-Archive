---
title: "URGENT NTFS CONFIG MOUNTING FAIL (unclean shutdown)"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by truet on 2007-09-11
**So i have ntfs partitions i need to write on, and using ntfs config but it comes up with the following every time i try to enable write. Plz help.**

[I]Mounting /media/sda1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/FE5C75355C74E9B3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/disk/by-uuid/FE5C75355C74E9B3 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/disk/by-uuid/FE5C75355C74E9B3 /media/sda1 ntfs-3g defaults,force 0 0
[/I]

** i cant access windows, dont know how to force. Many Thanks**

---

### Post by gn2 on 2007-09-11
Why can you not access Windows?

Is there data on the NTFS drive/partition you want to keep?

---

### Post by truet on 2007-09-11
yeah need to keep the files on the ntfs drive. well one of the windows startup files is curropted, so can't start it.

---

### Post by u-slayer on 2007-09-11
run ntfsfix on your ntfs partition

for you this would be

```
sudo ntfsfix dev/disk/by-uuid/FE5C75355C74E9B3
```

make sure check to see if it's mounted first by typing $mount and if needed $umount <dev>

---

### Post by truet on 2007-09-12
**Thanks for the reply. The following message shows...**

[I]jonathan@Aishwarya:~$ sudo ntfsfix dev/disk/by-uuid/FE5C75355C74E9B3
Password:
sudo: ntfsfix: command not found[/I]

**Sorry im probably doing something really dumb or missing something out?**

---

### Post by gn2 on 2007-09-12
You need to add the ntfsprogs package.

It's in the repositories and available through Synaptic Package Manager.

---

### Post by truet on 2007-09-12
**Ok ran that and after installing and trying ntfs fix the following happens**

[I]jonathan@Aishwarya:~$ sudo ntfsfix dev/disk/by-uuid/FE5C75355C74E9B3
Password:
Failed to determine whether dev/disk/by-uuid/FE5C75355C74E9B3 is mounted : No such file or directory
Mounting volume... Error opening partition device : No such file or directory
Failed to startup volume : No such file or directory
FAILED
Attempting to correct errors... Error opening partition device : No such file or directory
FAILED
Failed to startup volume : No such file or directory
Volume is corrupt. You should run chkdsk.[/I]

---

### Post by alex_anthony on 2007-09-12
could need a / before dev/disk.... perhaps
Thats the location
so it's
```
sudo ntfsfix /dev/disk/by-uuid/FE5C75355C74E9B3
```

---

### Post by truet on 2007-09-12
New error

jonathan@Aishwarya:~$ sudo ntfsfix /dev/disk/by-uuid/FE5C75355C74E9B3
Password:
Refusing to operate on read-write mounted device /dev/disk/by-uuid/FE5C75355C74E9B3.

---

### Post by gn2 on 2007-09-12
If it was me I'd put it in a USB enclosure and plug it into a Windows PC, then "safely remove" it.

---

### Post by truet on 2007-09-13
Is there no way to do it atall without having to buy an enclosure and finding another PC?

---

### Post by rhonaldmoses on 2008-07-07
Please check the blog post below for the NTFS mounting issue:

[http://linuxevangelist.blogspot.com/2008/07/fixing-ntfs-mount-error-in-gnulinux.html](http://linuxevangelist.blogspot.com/2008/07/fixing-ntfs-mount-error-in-gnulinux.html)

Please comment whether it works or not.

Regards,
Rhonald

---

