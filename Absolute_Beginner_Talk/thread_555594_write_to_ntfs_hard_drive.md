---
title: "write to ntfs hard drive"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by robertw on 2007-09-20
I have installed Ubuntu 7.x desktop on a box with hda formatted in ext3.  I added a pci raid card with two previously formatted ntfs drives in raid 1 and set up samba sharing on the network.  It works beautifully and I can read all the files on hdb from Ubuntu as well as from other mac and windows  boxes on the network.  I am completely new to Ubuntu, and I would like to use this Ubuntu box just as a file server.  I can read but cannot write or change permissions  from any of the boxes, Ubuntu, Mac, and Windows.  Is ntfs the best file system for access by the three operating systems?  If I should use ntfs, how do I enable writes?  Thanks for any help

---

### Post by Kowalski_GT-R on 2007-09-20
you're just one click away from solving your problem.

Open Add/remove software, and search for "NTFS"

you'll find an app wich enables writing to NTFS disks.

Install

Run it and check to enable writing.

I had to reboot if I remember correctly.

ciao,

Andre

---

### Post by tenjin1 on 2007-09-20
Ntfs-Config will enable you to read/write to NTFS  from ubuntu, since by default you can't.

In terminal:
```
sudo apt-get install ntfs-config
```

Then to open this program:
```
Applications—>System Tools—>NTFS Configuration Tool
```

---

### Post by justin whitaker on 2007-09-20
Aww, guys, you are ruining all the command line fun! :)

---

### Post by ukripper on 2007-09-20
ntfs-3g - [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by tenjin1 on 2007-09-20
> **Kowalski_GT-R said:**
> you're just one click away from solving your problem.

Open Add/remove software, and search for "NTFS"

you'll find an app wich enables writing to NTFS disks.

Install

Run it and check to enable writing.

I had to reboot if I remember correctly.

ciao,

Andre

This is the exact same program I refer to but different way of getting it. :)

---

### Post by Kowalski_GT-R on 2007-09-20
> **tenjin1 said:**
> Ntfs-Config will enable you to read/write to NTFS  from ubuntu, since by default you can't.

In terminal:
```
sudo apt-get install ntfs-config
```

Then to open this program:
```
Applications—>System Tools—>NTFS Configuration Tool
```

and this is the exact way to proceed I would have posted in the first place....

:):)

---

### Post by ukripper on 2007-09-20
> **ukripper said:**
> ntfs-3g - [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

And the above is more info on ntfs-config incase you need!

---

### Post by robertw on 2007-09-20
Thanks for the replies.  I have added nts-config and enabled the ntsf drive for writing.  I can now write from the Ubuntu box to this drive (which is internal).  However when I try to write to this drive from a windows box on the network, I get a message saying "cannot copy...access is denied".  When I try to change permissions from windows I get "Unable to save permission changes on hdb1...access is denied".  When I right click the drive from the Ubuntu desktop and go to the permissions tab of properties it shows hdb1 owner is root and all the access choices are greyed out.  Since I intend to use the Ubuntu box as a file server, other boxes will have to be able to write as well as read.  Are there any suggestions?

---

