---
title: "No Swap?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-02-18
With my computer, for some reason, kernel upgrades "break" the system.  It's a simple matter of having the wrong partition assigned as root (easily fixed by changing a 5 to a 4 in my Grub menu.lst).  But today as I was browsing my specs in Sysinfo, I found that a swap isn't detected.  Could the kernel upgrades be pointing my install to a different place when it looks for swap?  And how can I have my computer "find" it again?

---

### Post by dje on 2008-02-18
Please post the outputs of:
```
cat /etc/fstab
```
Prints mount points and other info that computer mounts at boot
```
blkid
```
Prints UUID of all partitions

---

### Post by Niklas Schröder on 2008-02-18
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=532fc691-b3be-4356-8e8f-ea8ecb6b7198 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0309" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="E6AC5550AC551BFD" 
/dev/sda3: UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="9a757e4d-cf4d-459e-a219-dc4125703a58" 

```

---

### Post by dje on 2008-02-18
OK the UUID of the swap partition is different to the one the computer attempts to mount at boot, so  you need to change it:
```
sudo gedit /etc/fstab
```
Copy and paste this into the UUID space for the swap partition in the fstab file (second line up from bottom):
```
9a757e4d-cf4d-459e-a219-dc4125703a58
```
After that save and close the file
Then do:
```
sudo swapon /dev/sda6
```

Hope that is clear, if not please post on any issues you have

dje

---

### Post by Niklas Schröder on 2008-02-18
Done.  Now I get...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
9a757e4d-cf4d-459e-a219-dc4125703a58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0309" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="E6AC5550AC551BFD" 
/dev/sda3: UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="9a757e4d-cf4d-459e-a219-dc4125703a58" 

```

---

### Post by smartboyathome on 2008-02-18
Restart Ubuntu and it should work.

---

### Post by dje on 2008-02-18
No you made an error, you put
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
9a757e4d-cf4d-459e-a219-dc4125703a58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

But it should be:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=9a757e4d-cf4d-459e-a219-dc4125703a58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

You need to put the UUID= at the start of the second line from the bottom

---

### Post by Niklas Schröder on 2008-02-18
Ok.  I just pasted in what you said and restarted.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=9a757e4d-cf4d-459e-a219-dc4125703a58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```

```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0309" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="E6AC5550AC551BFD" 
/dev/sda3: UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="ceb5fb0c-efaa-41d9-b82f-e1b32fee3b54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="9a757e4d-cf4d-459e-a219-dc4125703a58" 

```

---

### Post by dje on 2008-02-18
Yep you're good to go just do:
```
sudo swapon /dev/sda6
```
or reboot

dje

---

