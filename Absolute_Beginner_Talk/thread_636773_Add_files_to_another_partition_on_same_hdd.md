---
title: "Add files to another partition on same hdd"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by pooper on 2007-12-10
quick question, how do I mount the windows nfts partition in linux to add some file to it?
I've managed to mount the partition, but when I go to add files I get prompted with permission denied.

---

### Post by philinux on 2007-12-10
Have you got the ntfs-3g driver installed

[http://ubuntuforums.org/showthread.php?t=546959](http://ubuntuforums.org/showthread.php?t=546959)

---

### Post by geirha on 2007-12-10
You need to mount it using [ntfs-3g]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by kpkeerthi on 2007-12-10
The following method is applicable for Gutsy only. If you are using feisty (as I read from your profile), you need to manually install ntfs-3g from synaptic.

1. Make folders where the partions will be mounted
```

sudo mkdir /media/DATA

```

2. Make a backup of /etc/fstab
```

sudo cp /etc/fstab /etc/fstab.backup

```

3. Open /etc/fstab
```

gksudo gedit /etc/fstab

```

4. Add the following line at the end of the file
```

/dev/sda3 /media/DATA ntfs-3g defaults 0 0

```

5. Save and Exit. Restart. You should now see shortcut to DATA on your desktop.

---

### Post by njparton on 2007-12-10
You could also mount it via CIFS in fstab or via autofs (although I can't get latter to work reliably).

---

