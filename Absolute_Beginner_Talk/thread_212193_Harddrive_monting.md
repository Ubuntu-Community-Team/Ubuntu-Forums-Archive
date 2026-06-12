---
title: "Harddrive monting"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by yard on 2006-07-09
Third day on Ubuntu here.  Still trying to mount my second harddrive.  I have tried several things and am now confused as to what I've really done.  It shows up now under Places> Computer, but when I double click on it I get this:

error: device /dev/hdb1 is not removable

error: could not execute pmount


please help

---

### Post by taurus on 2006-07-09
I assume it's a NTFS format and it's /dev/hdb1.  Open a terminal, Applications -> Accessories -> Terminal, and type
```

sudo mkdir /windows
sudo mount -t ntfs /dev/hdb1 /window
df -h <-- you should see your second harddrive mounted on /windows...

```

---

### Post by yard on 2006-07-09
meant to mention it is vfat

---

### Post by taurus on 2006-07-09
```

sudo mkdir /windows
sudo mount -t vfat /dev/hdb1 /windows
df -h <-- you should see your second harddrive mounted on /windows...

```

---

### Post by yard on 2006-07-09
Thank you, that worked.  However, Places-> Computer still has it listed as "149.0 GB Volume" and nothing happens when I try to open it.  I do now have the option to unmount rather than mount when right clicking on it. 

Also when I try to write to the directory /windows I'm told I don't have permission.

---

### Post by yard on 2006-07-09
okay, I unmounted and remounted the drive using:

sudo mount /dev/hdb1 /second_harddrive -t vfat -o umask=000

This worked great, gave me proper access and everything, but I have to do it every time I restart the computer.  How do I make this permanent?

---

### Post by taurus on 2006-07-09
> **yard said:**
> okay, I unmounted and remounted the drive using:

sudo mount /dev/hdb1 /second_harddrive -t vfat -o umask=000

This worked great, gave me proper access and everything, but I have to do it every time I restart the computer.  How do I make this permanent?
Open a terminal and add the following line to it (at the end)...
```

/dev/hdb1     /second_harddrive     vfat     defaults,umask=00000  0     0

```
Now, mount it with
```

sudo mount -a

```
From now one, /dev/hdb1 will be mounted to /second_harddrive automatically upon boot...

---

