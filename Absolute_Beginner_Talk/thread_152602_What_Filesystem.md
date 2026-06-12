---
title: "What Filesystem?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by LeeDJC on 2006-03-30
I am about to ditch my Windows XP install and go for just Ubuntu. I have three Hard Drives. My First Drive is a 80gig IDE on which I'll install the OS. The second is a 40gig IDE and the third is a 250gig SATA

What's the best way to setup these drives? ie what filesystem etc? I use the 40gig for my music, and the 250gig for movies/tv stuff.

Any help would be appreciated. Thanks!

---

### Post by halfvolle melk on 2006-03-30
The default ext3 will do fine.
[https://wiki.ubuntu.com/LinuxFilesystemsExplained?highlight=%28filesystem%29](https://wiki.ubuntu.com/LinuxFilesystemsExplained?highlight=%28filesystem%29)

---

### Post by WoodyMahan on 2006-03-30
Ext3 is fine.  You might want to consider formatting one of those drives as a Fat32, just incase you have a friend with Windows come over and you want to share some files with them.

---

### Post by LeeDJC on 2006-03-30
Cool thanks. I know the first drive filesystem can be changed when I'm installing Ubuntu, but how do I change the other drives filesystems when it's up and running? (I've got Partition Magic, so would it be easier to do that beforehand?)

---

### Post by wout.wepsait.com on 2006-03-30
[quote=WoodyMahan]Ext3 is fine.  You might want to consider formatting one of those drives as a Fat32, just incase you have a friend with Windows come over and you want to share some files with them.[/quote]

Fat32 has nothing to do with that.

---

### Post by LeeDJC on 2006-03-30
Does that mean I need a FAT32 partition to share files with an external windows computer, or not? What about a USB stick?

---

### Post by Princey on 2006-03-30
[QUOTE=LeeDJC]Does that mean I need a FAT32 partition to share files with an external windows computer, or not? What about a USB stick?[/QUOTE]


You really don't need a FAT32 partition UNLESS you're dual booting and need to share files with your Windows partition (like music rip from your cd on either windows or linux) other than that, you're fine. As to converting your other drives, you can do it all when you first install linux, just chose "edit partitions manually". If you've already installed ubuntu, I think (though I've never used it. I do my partitioning during setup) gparted can do the trick. You'd want to do a search in the forums on gparted to help you out there as I don't use the gnome desktop environment.

---

### Post by meborc on 2006-03-30
a few pieces of information...

[http://linux.org.mt/article/filesystems](http://linux.org.mt/article/filesystems)

If you want to make a clean install of ubuntu, read this
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
it gives an overview how to partition and which filesystems to use etc...

(it's a dual-boot guide, so skip the win parts) ;)

---

### Post by chantra on 2006-03-30
I would recommend ext3 for /, reiserfs is pretty good.

About the fat32 filesystem, this is non sense, if you share your file through network, you need to install a samba server.

  In the other hand, if you want to be able to access your data from your windows installation (on the same computer), then you need to have your datas on a FAT32 file system.

---

### Post by halfvolle melk on 2006-03-30
[QUOTE=LeeDJC]I've got Partition Magic, so would it be easier to do that beforehand?[/QUOTE]
You can do the other disks afterwards using gParted. Also it's a good idea to create a seperate partition for your /home.

---

### Post by LeeDJC on 2006-03-30
Cool. Thanks guys for your help. I haven't installed ubuntu yet, but planning to later today. Tried the Live CD and that worked a treat.

I just wanted to make sure I was sorted and understood the filesystems before I installed it.

One question this has raised tho, lol. Is samba easy enough to setup in ubuntu? I've got a couple of xboxes networked to the pc at the min, (using xbmc) and obviously still want them to work!

---

### Post by LeeDJC on 2006-03-30
[QUOTE=halfvolle melk]You can do the other disks afterwards using gParted. Also it's a good idea to create a seperate partition for your /home.[/QUOTE]

Without sounding stupid... what is /home ? Is there a windows equivalent?

---

### Post by chantra on 2006-03-30
/home is like the Documents and Setting directory from windows.

you definitely need to have a separate /home partition from your filesystem, so, in case you install a new system, completely crashed your old system ... you can still get you personnal data.

---

### Post by meborc on 2006-03-30
[QUOTE=LeeDJC]Without sounding stupid... what is /home ? Is there a windows equivalent?[/QUOTE]

MyDocuments? ... i guess there is no equivalent... it is the home directory of your user... and the idea of keeping it on a separate partition is that all the application configuration files will be there... and if you need to reinstall the system, they will be preserved...

i myself don't keep it separate... i only keep my media in a separate place:

1 ext3 - BIG one for media (documents, all the stuff i don't want to lose)
1 ext3 - smaller one for ubuntu install and progz
1 swap partition (2*RAM)

also read this for more info - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by chantra on 2006-03-30
here is my filesystem:

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-686/volatile type tmpfs (rw,mode=0755)
/dev/sda2 on /boot type ext3 (rw)
/dev/sda5 on /home type reiserfs (rw)
/dev/sda7 on /mnt/fat type vfat (rw,noexec,nosuid,nodev,gid=100,umask=0000)
/dev/sda6 on /tmp type reiserfs (rw)
/dev/sda8 on /usr type reiserfs (rw)
/dev/sda10 on /var type reiserfs (rw)

a separate /var is usefull when you are running a server.

---

### Post by steve.horsley on 2006-03-30
Do **not** use partition magic to create the Linux partitions. This seems to cause problems, judging by several other posts I have seen. Let the Ubuntu installer do the partitioning. You can just tell the installer to use the whole disk.

---

