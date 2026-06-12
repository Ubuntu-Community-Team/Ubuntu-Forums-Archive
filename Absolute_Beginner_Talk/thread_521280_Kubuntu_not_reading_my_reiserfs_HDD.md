---
title: "Kubuntu not reading my reiserfs HDD"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-08-09
Ubuntu does but not Kubuntu.
Here is the output of
```
sudo fdisk -l
```
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18890   151733893+  83  Linux
/dev/hda2           18891       19457     4554427+   5  Extended
/dev/hda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10337    78147688+  83  Linux

Disk /dev/sde: 259 MB, 259522560 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          31      248976    b  W95 FAT32

```
then when I try and mount HDB it says this
```
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab
```

---

### Post by schorsch on 2007-08-09
You have to mount /dev/hdb[COLOR="Red"]1[/COLOR] .....

---

### Post by blithen on 2007-08-09
Same thing gives me this
```

blithen@Sparky:~$ mount /dev/hdb1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab
```

---

### Post by splintercellguy on 2007-08-09
You have to add an entry in fstab if you want to mount on boot, else you have to put:

mount -t reiserfs (? i think) /dev/hdb1 /mnt/point/here

---

### Post by blithen on 2007-08-09
Also when I try to open it up in kate it gives me this

```
blithen@Sparky:~$ sudo kate /etc/fstab
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
```

---

### Post by splintercellguy on 2007-08-09
Personally I use gedit/nano.

---

### Post by schorsch on 2007-08-09
Try:

```
kdesu kate /etc/fstab
```

sudo works only in terminal mode; if you want to start a graphic application you have to use "kdesu" when running KDE and "gksudo" or "gksu" when running GNOME.

---

### Post by blithen on 2007-08-09
Yay it worked! Thanks!!

---

### Post by blithen on 2007-08-09
I have another problem. When I click on ADD/REMOVE. It never pops up. Any help on that?

---

### Post by splintercellguy on 2007-08-09
Try firing up app-install from the Terminal.

---

### Post by blithen on 2007-08-09
That works fine. Also so does Adept Manager. Just not the add/remove one.

---

### Post by blithen on 2007-08-09
What does this mean?

```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

