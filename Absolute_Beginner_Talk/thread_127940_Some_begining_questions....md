---
title: "Some begining questions..."
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Lost-Ninja on 2006-02-10
Sorry if these are answered somewhere obvious, I'm perhaps blind...

[LIST=1]
[*]My Ubuntu is installed and seems to be fine I've used Automatix to add various programs and things that seemed like being a good idea to have. The machine is a dual boot with winXP but I really want to get the hang of linux. Though I tend to run it through a tightVNC server/viewer (and that works fine) I want to be able to set the monitor's refresh rate to something higher than headache inducing 60hz, but cannot find anything that will allow that. I have installed the nvidia driver for my card. (I assume as I have an nvidia options dialog thing under system tools.) But it still refuses to allow any refresh over 60hz @ 1024x768 (I can go lower at 800x600)
[*]I have a second hard drive on my ubuntu machine it is mainly a media drive I keep a backup of my windows documents and my MP3s on it, mainly so if my main PCs HDD dies I don't lose everything. How do I get this to appear? I formatted it from within ubuntu and could access it straight away but since rebooting it remains listed as inaccessible from within the 'Disks Manager' if I click enable nothing happens. Before the reboot I could access it under the file browser by using 'Go...' and typing //Media/ media being the location I used in the 'disks manager' access path.
[*]Having used [this]("http://www.samba.netfirms.com/index.htm") guide to setting up samba's config I can no longer see my Ubuntu PC at all from within windows (Ubuntu can see the windows PC and is sharing the internet.) How do I set up file sharing easily between the two PCs? (Specifically so Windows can see Ubuntu. Or drives therein.)
[*]How do I make an unattended login? I want to be able to either login from my windows PC using the VNC system or for the ubuntu to login automatically so that I can use the VNC system...
[*]How do I find out the DHCP assigned IP for my ubuntu PC?
[/LIST]

I'm sure that any answers to these questions will only lead to more questions but I have to start somewhere. ;)

---

### Post by Vladimirm on 2006-02-10
> # I have a second hard drive on my ubuntu machine it is mainly a media drive I keep a backup of my windows documents and my MP3s on it, mainly so if my main PCs HDD dies I don't lose everything. How do I get this to appear? I formatted it from within ubuntu and could access it straight away but since rebooting it remains listed as inaccessible from within the 'Disks Manager' if I click enable nothing happens. Before the reboot I could access it under the file browser by using 'Go...' and typing //Media/ media being the location I used in the 'disks manager' access path.

try this.
Open up a terminal and type

sudo mkdir /mnt/hdb
sudo mount /dev/hdb /mnt/hdb

that should be fine

---

### Post by Lord Illidan on 2006-02-10
As regards your hard drive, can you give us your /etc/fstab
Just do this:
```
gedit /etc/fstab
```

To find the ip address, try running ```
ifconfig
``` in a terminal.

---

### Post by Lost-Ninja on 2006-02-10
Yes:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Tried running ipconfig in a termainl but get command not found.

---

### Post by gavinb on 2006-02-10
> # How do I make an unattended login? I want to be able to either login from my windows PC using the VNC system or for the ubuntu to login automatically so that I can use the VNC system...


Check out this thread.

[http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc4server](http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc4server)

Gavin

---

### Post by carlosqueso on 2006-02-10
It's i**f**config in ubuntu.  also, do you know what the partition name is called in ubuntu? Please post your fdisk -l after you mount the drive the way Vladimirim told you and I can figure out the line you have to add.

---

### Post by Woggie on 2006-02-10
> try this.
Open up a terminal and type

sudo mkdir /mnt/hdb
sudo mount /dev/hdb /mnt/hdb

that should be fine

I'm having the same kind of issue.  I tried your suggestion and it didn't work.  Here is my fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Sorry Ninja, don't mean to steal your thunder.

---

