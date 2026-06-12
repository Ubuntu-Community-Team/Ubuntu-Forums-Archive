---
title: "[SOLVED] Problem mounting XP share"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-01-30
From my 7.04 machine i am having a problem mounting a FAT32 partition on an XP machine on the LAN.  In the network file browser I can see the host (opteron-185) and I can see all of the drives and shared directories under it.  However, I cannot open the shared directory (file_archive). When I attempt to view the contents, I get the following message: "The folder contents cannot be displayed.  Sorry, couldn't display all the contents of file_archive."

I have attached the fstab file, and the output of fdisk -l.

---

### Post by dstew on 2008-01-30
Did you try to mount it using the command line? You might get error messages that will help.```
sudo mount -t smbfs -o username=whatever,password=whatever //opteron-185/file_archive /mnt/file_archive
```I notice that the server name has a hyphen in it. I know that Samba has trouble with special characters in file names, and that can lead to strange things. In my case, a file name with a $ caused none of the other files to appear. You can troubleshoot these kind of things from the command line using [smbclient]("http://linuxcommand.gds.tuwien.ac.at/man_pages/smbclient1.html")

---

### Post by ThunderRd on 2008-01-31
Here's what I got when I entered your command; it just looks like it's the wrong usage:
```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

I changed the name of the host to opteron185, and I used the admin username and password on the windows box.

---

### Post by oedha on 2008-01-31
sudo apt-get update
sudo apt-get install smbfs
make a new folder for this mount ( i used /media/x )
then do like dstew advised
or put this on your fstab
//servername/sharedfolder /media/x cifs rw,gid=root,uid=root,file_mode=0775,dir_mode=0775 0 0


regards;
~E~

---

### Post by ThunderRd on 2008-01-31
Found the problem.  It wasn't a Linux problem (no surprise there).

I discovered that I couldn't browse the shared directories from the windows machine itself-so I poked around in the event viewer and found some errors regarding IRPStackSize; a search provided this document:
[http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

Apparently some antivirus software can cause this, in my case it was a recently installed new ver sion of NOD32 on the windows machine.  There is a registry value to change, it's quite easy.  As soon as it was changed all the clients were able to see the shares, including the Ubuntu machine.

Thanks for your input.

---

