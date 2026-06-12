---
title: "Moving files over from Vista"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by hobohitman on 2008-02-10
I just finished installing 7.10 on my system today and I am dual booting with Vista. Is there a way other than putting the files onto a CD's to transfer them to Ubunu?

Thanks

---

### Post by Rocket2DMn on 2008-02-10
You can use the ntfs-3g driver to read/write ntfs partitions (which is what xp/vista use).  You could potentially just leave your files on the Vista partition and access them from Ubuntu, otherwise you can move them to Ubuntu.
You can enable read/write by going to Applications->System Tools->NTFS Configuration Tool.  If you still can't figure out how to see your vista drive, post the output of these following commands and I'll help you with that
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by taurus on 2008-02-10
To access files on Vista, ntfs filesystem, you need to mount it.  So, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by hobohitman on 2008-02-10
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       26604   203154432    7  HPFS/NTFS
/dev/sda4           26605       38913    98872042+  83  Linux

That is the output of that command.

There is no Applications->System Tools->NTFS Configuration Tool location as far as I can tell =/, which sounds odd to me as well, but I looked and found nothing.

---

### Post by Rocket2DMn on 2008-02-10
To make sure you have the ntfs utilities, run
```
sudo apt-get install ntfs-3g ntfs-config ntfs-tools
```
To mount the ntfs drive, you would do something like this:
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda3 /media/windows
```
Then you could see your windows stuff at /media/windows
If you're interested, we can also setup an entry in fstab so the drive will automatically mount when you boot the computer.  Just post the output of
```
cat /etc/fstab
```

---

### Post by hobohitman on 2008-02-10
Code:

sudo apt-get install ntfs-3g ntfs-config ntfs-tools

Gave me this output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-tools

...Im guessing thats not good

Thank you for the very fast replies, but I need to get back to work. I will attempt to figure this out when I again have the time.

---

### Post by Rocket2DMn on 2008-02-10
Ah, sorry, the program is "ntfsprogs".
```
sudo apt-get install ntfs-3g ntfs-config ntfsprogs
```
Then check Applications->System Tools->NTFS Configuration Tool.
Whether you get it or not, proceed to the next steps I posted.

---

### Post by hobohitman on 2008-02-11
After rebooting suddenly the files are visible. I ran the command anyway and got the program installed. Thanks for your help!

---

