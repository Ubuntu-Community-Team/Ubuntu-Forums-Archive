---
title: "HDD Trouble"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Tyscorp on 2007-02-23
I installed Ubuntu 6.06 a few days ago, and so far I have a million questions.

There are 2 HDD in the computer, both exactly the same. (Western Digital 80gig) One is mine, and one is my dads. The computer isnt even mine, im using it until I buy my own (in a few days). Now, I moved all my stuff I needed on to my fathers HDD, reformatted my HDD then installed Ubuntu. I have a 1gig swap partition, 15gig ext3 and the rest is fat32. I then moved all my stuff back onto the Fat32 partition (using Windows XP, which is installed on his HDD) And now I cant access it through Ubuntu. Could somone tell me how to access my data. I think its called 'Mounting' or somthing. 

Also, when I get my computer, I will take my HDD with me. And when my HDD is removed the computer doesnt boot in XP. (My HDD is currently slave) Is there any way to fix it so it boots in XP with my HDD removed? I think its called 'grub'...

---

### Post by taurus on 2007-02-23
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And before you remove the harddrive that has Ubuntu on, boot into XP and fix the MBR with

```
fixmbr
```
Then, shutdown the machine and remove the second harddrive.

---

### Post by netkid91 on 2007-02-23
GRUB needs to read you config file off the partition which contains the /boot directory, which is why it won't boot without your HD in.  As for getting the data, type this in a console and post the output:
ls /dev | grep hd

---

### Post by Tyscorp on 2007-02-23
Thanks a lot! :)

Here are the results for the first request:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hda5            1276        9728    67898691    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1987    15960546   83  Linux
/dev/hdb2            1988        9729    62187615    f  W95 Ext'd (LBA)
/dev/hdb5            1988        9636    61440561    b  W95 FAT32
/dev/hdb6            9637        9729      746991   82  Linux swap / Solaris


And the second:

hda
hda1
hda2
hda5
hdb
hdb1
hdb2
hdb5
hdb6
hdd

---

### Post by taurus on 2007-02-23
I assume you want to mount /dev/hdb5.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb5   /media/hdb5   vfat   iocharset=utf8,umask=000   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb5
sudo mount -a
df -h
```

---

### Post by Tyscorp on 2007-02-23
Yay! Thankyou! *huggles*

So, to fix the boot thingy, do I just go into the command prompt and type fixmbr?

---

### Post by taurus on 2007-02-23
You have to boot into XP first and run that command from a terminal in XP.  Then, you won't be able to boot Ubuntu again since XP will overwrite the MBR with it own bootloader.

---

### Post by Tyscorp on 2007-02-23
Ok.

Will I still be able to boot in Ubuntu when I put my HDD in my new computer?

---

### Post by netkid91 on 2007-02-23
Not sure if the command is available in the installed XP terminal.  I tried that once and it didn't work, you might have to use the install CD and go into the recovery console to do so.  Be warned that running fixmbr will prevent you from booting Ubuntu without going through some other hoops, so don't do it until you plan on leaving.  When you are going to leave I'd recommend making another post and we'll help you then.

---

### Post by Tyscorp on 2007-02-23
Ok then. Thankyou very muchlys for your help.

---

### Post by netkid91 on 2007-02-23
No problem, thats why we are here.  Feel free to come back any time, have a good day.

---

