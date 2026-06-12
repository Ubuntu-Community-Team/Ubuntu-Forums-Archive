---
title: "Mounting HFS+ hard drives with 8.10"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by ataylor1988 on 2008-11-05
Hello i have a odd situation and need some help.  I am not good at all this command line stuff because the only systems i have mounted are NTFS drives which you can do through the GUI, but anyways

We are the apple certified repair center for central IL, i am trying to set up a Linux machine so we can back up users data and things to this machine over the network, the reason for choosing this instead of a network storage device is the fact that we can get linux to share both a HFS drive and a NTFS drive for our windows customers.

So anyway, i have a 120 and a 500 gb drive formatted in HFS on the 3rd IDE channel and i need to mount them both so i can set up a samba share with them, can anyone give me a step by step to do this, i can take care of the SAMBA part just need to know how to get them to mount. Any help will be greatly appreciated

Thanks 
Andrew

---

### Post by tiresia on 2008-11-05
When you select with the mouse a Drive in GNOME, it will be mounted on /media.

If you want to mount a hfsplus formatted drive or partition, e.g. /dev/sda1

1. Make a **mount point** for it, that you can call as you like, e.g. 'hfsplus', where you like (usually on /mnt or /media).
You need to run this commands always with root privileges 
```
sudo mkdir /mnt/hfsplus
```

2. **Mount** it, specifying file system, device and mount point 
```
sudo mount -t hfsplus /dev/sda1 /mnt/hfsplus
```
An icon will appear on your desktop.

3. To **unmount** the HD
```
sudo umount /mnt/hfsplus
```

4. In order to avoid to repeat this step every time you start your computer, edit the file **/etc/fstab** (the file system table), so that the Drive will be always mounted.

```
sudo nano /etc/fstab
```
You can add a line for each partition, you want to be mounted at startup.
Following our example:
```
# <file system> <mount point> <type>  <options>    <dump><pass>
/dev/sda1     /mnt/hfsplus       hfsplus  defaults      0       0 
```
Exit (ctrl+X) and save


The options 'defaults' are 'rw, suid, dev, exec, auto, nouser, and async'.
There are a lot of options that you can specify. May be you can have a look to the man pages of 'mount'```
man mount
```
Or you can google 'how to edit /etc/fstab'

::::::::::
Linux can read/write hfsplus, but if it is journaled Linux can only read.
To disable journaling on an hfs volume, open a terminal in OSX and run```
diskutil disableJournal /Volumes/TheVolumeName 
```

---

### Post by cyberdork33 on 2008-11-05
> **ataylor1988 said:**
> So anyway, i have a 120 and a 500 gb drive formatted in HFS on the 3rd IDE channel and i need to mount them both so i can set up a samba share with them, can anyone give me a step by step to do this, i can take care of the SAMBA part just need to know how to get them to mount. Any help will be greatly appreciated

Thanks 
Andrew
HFS+ support is in the Linux kernel. You should just have to have that enabled in your kernel and the hfsplus tools and you can mount.

However, I think that you are headed down the wrong path. It doesn't matter what the format of the filesystem is on the Linux box as long as the Linux system can read/write to it. (in other words, the windows and apple machines do not need support for the filesystem that you are using on your Linux box for the samaba share). So, with that in mind, it is BEST to use a Linux-native file system for this purpose to be used for both your Mac _and_ Windows customers. all that the remote machine sees is a samba share... that is the "filesystem" that it needs to write to.

In fact, a Mac could do the same job... Maybe I am misunderstanding what you are trying to do though.

---

### Post by DJiNN on 2008-11-07
Don't know if it's any use at all, but i've just had an iMac apart for a friend who needed the data retrieved from the HD (iMac's not working anymore). I attached it to the CDROM IDE cable of my Linux Mint machine, fired it up, ran Synaptic & did a search for HFS, which showed me a few things that were needed to be able to read HFS discs.  Installed that lot, then followed the info from "tiresia" above, and it worked a treat..... all the data on the Mac drive was retrievable and is now safe on my Linux system, waiting to be transferred to a USB stick. 

I thought it would be a lot harder than that, but it was very easy & straighforward. :)

---

