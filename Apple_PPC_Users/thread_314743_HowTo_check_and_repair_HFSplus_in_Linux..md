---
title: "HowTo check and repair HFSplus in Linux."
date: 2006-12-08
forum: Apple PPC Users
---

### Post by Gen2ly on 2006-12-08
This is a howto made simple and easy for Macintosh and Ubuntu users who need to be able to access HFSplus drives and partitions.  HFSplus support is included in the Edgy (Ubuntu 6.10) kernel but it will require a few extra tools to have it be both dependable and reliable.

First of all to have your hfsplus drive mounted, make a directory that will hold the mounted disk.
```
sudo mkdir /mnt/Shared_Disk
```

I use /mnt/Macintosh_HD, you can name it what you want.  Some people do this as /media/Macintosh_HD, but this is generally reserved for CD's and other removable types.

Now to temporarily mount it use this command:
```
sudo mount /dev/sda2 -t hfsplus -o rw /mnt/Shared_Disk
```
...replacing sda2 with your disk **dev**ice and hard disk partition(**#**).  My USB drive is /sda, my clamshell iBook is hda, etc.  See which one your's is by typing:
```
df -h
```
here's what mine looked like:
```
/dev/sda3              17G   12G  4.3G  73% /
/dev/sda2              43G   29G   15G  68% /mnt/OSX
/dev/sda4              15G  2.9G   12G  20% /mnt/Shared_Disk
```

NOTE:  You'll see other entries besides these.  They are temporary and virtual file systems.  Just notice the /dev entries.

Now, I must point out that Linux at this time is only able to mount Journaled HFSplus filesystems as read-only.  Journaling helps the filesystem preserve its data - especially useful for power outages.  Journaling got added to HFSplus when OSX came out.  

If you want to be able to read and write from and HFSplus drive, be sure journaling is off.  To see if your disk/partition is head to: System > Administration > System Log and click on syslog.  Now, punch ctrl+f and type in "mount".  If the above partition that we mounted is journaled, there will be a warning here.  To turn off journaling, restart with the OSX install CD, select Disk Utility from the drop down menu, click the drive you want to have journaling shutoff of and use the button Journaling disable.

To have the HFSplus drive/partition mounted everytime you boot, the fstab file must be changed:
```
sudo gedit /etc/fstab
```
and add this:
```
/dev/sda4 /mnt/Shared_Disk hfsplus rw,exec,auto,users 0 0
```

**Not cleanly unmounted HFSplus partitions or drives.**

The Linux Kernel is pretty picky about it's HFSplus drives, but it's a good thing.  If it ever occurs where your system is locked up and you have to force reboot, then your HFSplus disk will not be cleanly unmounted.  If you look into your syslog and see (once more ctrl-F, and use "mount" filter):
```
hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only
```
Then we need to add fsck.hfsplus support
```
sudo bash
cd /usr/src
mkdir hfsplus_support
wget http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz
wget http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2
tar zxf diskdev_cmds-332.14.tar.gz
bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
cd diskdev_cmds-332.14
make -f Makefile.lnx
cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cd /sbin
ln -s fsck.hfsplus fsck.hfs
```
Note: The compiler didn't compile the program newfs_hfs.  I'm not experienced enough to know why.  If someone knows how, please let me know.

Type fsck.hfsplus to see the list of option types - there is no man page.  You can delete the downloaded files and unstuffed folders if you wish.

Now to make the partition/drive read-write enabled, the filesystem needs to be checked:
```
fsck.hfsplus -r /dev/sda4
```


Sources:
original Gentoo piece:[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)
Debian derived piece:[http://www.debian-administration.org/users/lee/weblog/21](http://www.debian-administration.org/users/lee/weblog/21)

---

### Post by wesswei on 2008-03-13
great how-to for ubuntu. i guess no one needs fsck.hfsplus. all documentation are years old. not to mention open darwin is dead. however for the time being, i found the zipped source [here]("http://www.filesearching.com/cgi-bin/s?q=diskdev_cmds&t=f&d=&x=0&y=0&l=en")

this does NOT work for amd64 or 64 bit versions for that matter.

```
ubuntu:~$ fsck.hfsplus -r /dev/hda1
** /dev/hda1
** Checking HFS Plus volume.
Segmentation fault (core dumped)

```

does anyone know how to compile this for 64-bit systems? granted no one will ever see this post, but if so, I'm dying to have fsck for hfsplus. or a workaround for the error: [HTML]hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.[/HTML]

best,

Wes

---

### Post by krU6)#43 on 2008-04-30
If you're on Hardy Heron you can:
```
sudo aptitude install hfsprogs
```

Then:
```
sudo fsck.hfs /dev/sdb1
```

Replace sdb1 with your partition.

---

