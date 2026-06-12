---
title: "Adding second hard drive"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by StrawberryAngel on 2008-02-10
[SIZE="4"][COLOR="Magenta"]I have a matched pair of 320gb sata drives.  Ubuntu OS is on the first.  I want to use the 2nd sata for storage. How do I go about doing that?  I'm a total nood and understand some command line stuff. But usually I need stuff explained to me. Thank you in advance[/COLOR][/SIZE]

---

### Post by mikewhatever on 2008-02-10
> **StrawberryAngel said:**
> [SIZE="4"][COLOR="Magenta"]I have a matched pair of 320gb sata drives.  Ubuntu OS is on the first.  I want to use the 2nd sata for storage. How do I go about doing that?  I'm a total nood and understand some command line stuff. But usually I need stuff explained to me. Thank you in advance[/COLOR][/SIZE]

Assuming the drive is blank, you need to connect it, then create and formate partitions, and then mount them.

To deal with partitions, use Gparted Live cd. Linux uses ext3 file system, so it's recommended. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

To mount partitions at boot, you'll need to edit /etc/fstab file.
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by spiderbatdad on 2008-02-10
you may want to look into disk manager [http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)
the fiesty build is supposed to work fine for gutsy.

---

### Post by Brantis on 2008-02-10
I am also a beginner, but I am pretty sure that I can give you some good advice because I have just done something like this myself and you'll be using the same tools as I.

First of all you are going to start up the Synaptic Package Manager and use the search function to find a program called **gparted**.
Once you find this program, download it and let it install.

Once completed, you are going to look under System>Administration>Partition Editor.
This window will show you your default Linux Partition and tell you more about what partitions there are on the drive. Very handy little utility.

Now click at the top left corner that says **GParted** and then select **Devices**, and then click the second selection. This is your second HD. Once you have made this selection, you should see your HD listed in the partition area. Now Right click on the HD and select **Format to**>**ext3**.

All Done.

Just be sure that you have selected the right HD before you go partitioning space.

---

