---
title: "[SOLVED] Mounting an External HDD"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by will13 on 2007-12-10
I have an external HDD that I can't get to mount. It is a Fantom Drive Megadisk. I was able to mount it in 7.04 and everything would work great. Now that I have up graded to gusty, I can't. The drive shows up in my file browser but when i click on it I get this response. (see screenshot). 

I have tried doing > sudo apt-get install usbmount but that didn't work. Any help that you can give me is great, as this drive has a lot of files crutial for my work.

cheers!

---

### Post by lswest on 2007-12-10
are there any operating systems on the drive? or was it mounted in windows before you rebooted to Ubuntu, without removing the drive first?

---

### Post by njparton on 2007-12-10
The error seems to indicate that you currently have the hardrive mounted to another OS?

---

### Post by kpkeerthi on 2007-12-10
Perhaps you shared it with windows and it seems that it was not "Safely Removed" from windows. You may want to plug it back in windows and use "Safely remove hardware" from system tray.

---

### Post by will13 on 2007-12-10
I had it mounted on a windows box at one point, but i have since then removed windows from my computer. So there isn't anyway to go back into windows and safely remove it. Unfortunately.

Also all I have on it are files. I don't have any OS's running on it

---

### Post by njparton on 2007-12-10
It's running the NTFS filesystem so the safest bet is to reinstall windows to free the drive up using the advice above.

After that I'd recommend burning the contents to DVD and re-formatting the drive with a linux filesystem.  I like XFS and REISERFS.

---

### Post by kpkeerthi on 2007-12-10
OK.. in that case, you may force mount as follows. Your data should be safe.
1. Make folder to mount the partition to (if you haven't done already)
```

sudo mkdir /media/disk

```

2. Manually mount the partition
```

sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force

```

Optional ;)
3. Copy data to main hard drive and reformat the USB drive to ext3 :)

---

### Post by will13 on 2007-12-10
Great thanks for the help i manually mounted the partiton and now it works. Thanks again for all your help.

Cheers!

---

### Post by echris1 on 2008-05-30
Had the same problem, but manually remounting the drives worked just fine.  Just make sure you don't mix them up if you have a few.  Now to see if it will correctly boot up into Windows for once.

Thanks again!

---

