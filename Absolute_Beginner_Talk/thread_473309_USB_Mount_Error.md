---
title: "USB Mount Error"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-06-13
I'm  using 6.06 and all of a sudden getting problems mounting USB thumb drives.  Here's the error message.  Any ideas?


mount: only root can mount /dev/sda1 on /media/sda1

---

### Post by mocqueanh on 2007-06-13
When you plug USB into your machine, Ubuntu will auto mount it.

I dont understand this problem
Have you try to use command:

sudo mount /dev/sda1 /media/sda1


What's the File System of your USB ?

---

### Post by Inxsible on 2007-06-13
for external and usb flash drives you should use pmount to mount it and pumount to unmount it.

if you dont have pmount installed:
```
sudo aptitude install pmount
```

then to mount
```
pmount /dev/DEVICE_NAME MOUNT_POINT
```

where DEVICE_NAME  could be sdb1 hdb1 etc and mount point is the name of the folder where you want to mount it.

Note: make sure the mount point is NOT already an existing folder. pmount creates the folder for you under /media

---

### Post by tgbrowning on 2007-06-14
> **mocqueanh said:**
> When you plug USB into your machine, Ubuntu will auto mount it.

I dont understand this problem
Have you try to use command:

sudo mount /dev/sda1 /media/sda1


What's the File System of your USB ?

When I open "Computer" in Places I see the icon for the drive labeled "LEXOR JD FIREFLY: LEXAR" and it's got a small red cross on the drive icon. Clicking on it gives me the error message I related. Trying your command gives me no response that I can see. In terminal, it comes back without any message whatsoever.
 
One other symptom: The little light on the thumb drive is on all the time. No flashing, just on. The system is obviously trying to do something with the drive, but is unable to.

All of this started after I did some updates to the system, via the package manager.

Browning>>>

---

### Post by Campingman on 2007-06-14
"When you plug USB into your machine, Ubuntu will auto mount it."

Oh if only that was true!!

---

### Post by abburdlen on 2007-06-14
do I understand that previously you could just plug in your your thumbdrive and it would just show up?  
I'm just curious because I'm have similar problems with my USB HDD.

---

### Post by jcconnor on 2007-06-14
I was actually having a similar problem with a RIO Carbon (uses mass storage - MSC mode), an Ipod, other things.  Only started having problems a couple of weeks ago - been running fine for the last 6 months with no problems.

What I did was go in to Package Manager and reinstalled:

gnome-volume manager
hal
hal-device-manager
kdebase-kio-plugins
libhal1
libhal-dev
libhal-storage1
pmount

I had to reboot after I did that and now all my USB devices are working properly again.  My CD/DVD drive works  again too, I'm pretty sure it's related.

I'm not sure that I needed to reinstall all of them.  I just did a search on hal and pmount in the Package Manager and reinstalled the ones that looked relevant.  Anyway, it worked for me but your mileage may vary.

John

---

### Post by Inxsible on 2007-06-14
> **tgbrowning said:**
> When I open "Computer" in Places I see the icon for the drive labeled "LEXOR JD FIREFLY: LEXAR" and it's got a small red cross on the drive icon. Clicking on it gives me the error message I related. Trying your command gives me no response that I can see. In terminal, it comes back without any message whatsoever.
 
One other symptom: The little light on the thumb drive is on all the time. No flashing, just on. The system is obviously trying to do something with the drive, but is unable to.

All of this started after I did some updates to the system, via the package manager.

Browning>>>

Did you try the commands i gave you ?
If you dont have pmount installed you can install it by
```
sudo aptitude install pmount
```

---

### Post by tgbrowning on 2007-06-14
> **abburdlen said:**
> do I understand that previously you could just plug in your your thumbdrive and it would just show up?  
I'm just curious because I'm have similar problems with my USB HDD.

Indeed, that's one of the things that surprised the heck out of me. As son as I got Ubuntu up and running, USB thumb drives worked fine. I used a SanDisk half gig drive and a 4 gig Lexar drive. 

I even had a USB external hard drive working. That, too, is no longer functioning. 

Browning>>>

---

### Post by tgbrowning on 2007-06-14
I'll give them a try. I suspect some libray that got updated might be the problem. I neglected to add that I've been trying to get Totem to read DVDs and just two days ago, finally got Ogle to work okay, and some partial (but very flaky) sus there.

You guys are a great help. I'm much obliged to you all, even if I don't get things working okay immediately. I now have an avenue to explore.

Browning>>>

---

### Post by tgbrowning on 2007-06-15
> **Inxsible said:**
> for external and usb flash drives you should use pmount to mount it and pumount to unmount it.

if you dont have pmount installed:
```
sudo aptitude install pmount
```

then to mount
```
pmount /dev/DEVICE_NAME MOUNT_POINT
```

where DEVICE_NAME  could be sdb1 hdb1 etc and mount point is the name of the folder where you want to mount it.

Note: make sure the mount point is NOT already an existing folder. pmount creates the folder for you under /media

Tried reinstalling that list from john but that didn't seem to work. So, I tried the pmount command and got the following result.
I don't think I fully understand what's going on. The USB drive shows up as "SanDisk Cruzer Mini -- is that supposed to be the mount point?

Browning>>>
browning@browning-laptop:~$ pmount -d /dev/sandisk /dev/sandisk cannot be resolved to a proper device node mount point to be used: /media/sandisk no iocharset given, current locale encoding is UTF-8
locale encoding uses UTF-8, setting iocharset to 'utf8'
Cleaning lock directory /var/lock/pmount/_dev_sandisk
Error: device /dev/sandisk does not exist
policy check failed

---

### Post by Inxsible on 2007-06-15
it should be something liek 
```
sudo pmount /dev/sda* SanDisk
```

pmount will create a folder for you under /media...so you only have to name SanDisk. also device name is /dev/sda1 or /dev/hda1  whichever drive you are tying to mount

post your output of 

```
sudo fdisk -l
``` -l is lowercase L. i can probably give you the exact command then.

---

### Post by tgbrowning on 2007-06-15
> **Inxsible said:**
> it should be something liek 
```
sudo pmount /dev/sda* SanDisk
```

pmount will create a folder for you under /media...so you only have to name SanDisk. also device name is /dev/sda1 or /dev/hda1  whichever drive you are tying to mount

post your output of 

```
sudo fdisk -l
``` -l is lowercase L. i can probably give you the exact command then.

Okay, here's the output from fdisk -l

*******

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6174    49592623+   7  HPFS/NTFS
/dev/hda2            6175        7506    10699290    f  W95 Ext'd (LBA)
/dev/hda3            7507        8742     9928170   83  Linux
/dev/hda4            8743        9729     7928046    c  W95 FAT32 (LBA)
/dev/hda5            6175        7449    10241406   83  Linux
/dev/hda6            7450        7506      457821   82  Linux swap / Solaris

Disk /dev/sda: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         992      499851+   b  W95 FAT32
browning@browning-laptop:~$

*****************

I see the sandisk as sda1, no?  So the problem is, what? A bad mount point?

What exactly *IS* a mount point and who do I have to maim to get a valid one?

:)

Browning>>>

---

### Post by tgbrowning on 2007-06-15
Further update.

This has me really, really bugged. To have something quit working and not be able to figure out what caused it!

So, in the interests of actually tracking down precisely went wrong, I killed my installation of Ubuntu and reinstalled, to see if it would once again mount USB drives automatically.

Guess what?

It does.  I'm back to where I started with the USB drives working fine, no problem. 

In the interest of figuring out what went right and what was done to wreck it, I went through the package manager and noted down exactly what had been installed. The list isn't complete, yet, but I'm going to include with this post a partial list, using search, of everything that seemed like it might have an effect. A bit later, I'll have a complete list for anyone who's interested.

So, here's the list of installed packages that seem to relavent.

*****************************************
Installation began at 3:30 pm 06/15/07

using Ubuntu 6.06 Dapper Drake

after installation, the following packages were present
() indicates a duplicate entry

after search for "mount"
binutil-static
busybox-initramsf
fdutils
gnome-applets
gnome-volume-manager
initramfs-tools
libblkid1
mount
pmount
smbelient

after search for hal
cron
gnome-power-manager
(gnome-volume-manager) 
hal
hal-device-manager
libhal1
libhal-storage1
(pmount)
sysvinit

search for ndiswrapper
ndiswrapper-util NOT INSTALLED

search for dvd
dvd+rw-tools
(ghome-volume-manager)
libnautilus-burn3
mkisofs
nautilus-cd-burn3
totem
totem-gstreamer

search for wifi
linux-restricted-modules 2.6.15-23-386

search for network
bittorrent
dhcp3-client
fping
ftp
(gnome-applets)
gnome-netstatus-applet
gnome-nettool
gnome-panel
gnome-system-tools
gnome-utils
hostname
hpijs
hplip
ifupdown
(initramfs-tools)
iproute
iptables
iputils-ping
iputils-tracepath
libaudio2
libavahi-client3
libavahi-common3
libavahi-common-data
libavahi-glib1
libgtop2-7
libjessie-java
libkrb53
libmng1
libnetcdf3
libnspr4
libnss3
libcap0.8
libping12-0
libslp1
libsnmp9
libsnmp-base
libsoup2.2-8
libuniconf4.2
libwrap0
libwvstreams4.2-base
libwvstreams4.2-extras
mii-diag
mtr-tiny
netbase
netcat
net-tools	
ntpdate
openssh-client
pcmcia-cs
pcmciautils
python
python2.4
python2.4-eunuchs
python-netcdf
rsync
tcpd
tcpdump
vnc-common
wget
wpasupplicant
xvncviewer
*************************************************

---

### Post by abburdlen on 2007-06-15
> **tgbrowning said:**
> Further update.

This has me really, really bugged. To have something quit working and not be able to figure out what caused it!

So, in the interests of actually tracking down precisely went wrong, I killed my installation of Ubuntu and reinstalled, to see if it would once again mount USB drives automatically.

Guess what?

It does.  I'm back to where I started with the USB drives working fine, no problem. 

In the interest of figuring out what went right and what was done to wreck it, I went through the package manager and noted down exactly what had been installed. The list isn't complete, yet, but I'm going to include with this post a partial list, using search, of everything that seemed like it might have an effect. A bit later, I'll have a complete list for anyone who's interested.

So, here's the list of installed packages that seem to relavent.

*****************************************
Installation began at 3:30 pm 06/15/07

using Ubuntu 6.06 Dapper Drake

after installation, the following packages were present
() indicates a duplicate entry

after search for "mount"
binutil-static
busybox-initramsf
fdutils
gnome-applets
gnome-volume-manager
initramfs-tools
libblkid1
mount
pmount
smbelient

after search for hal
cron
gnome-power-manager
(gnome-volume-manager) 
hal
hal-device-manager
libhal1
libhal-storage1
(pmount)
sysvinit

search for ndiswrapper
ndiswrapper-util NOT INSTALLED

search for dvd
dvd+rw-tools
(ghome-volume-manager)
libnautilus-burn3
mkisofs
nautilus-cd-burn3
totem
totem-gstreamer

search for wifi
linux-restricted-modules 2.6.15-23-386

search for network
bittorrent
dhcp3-client
fping
ftp
(gnome-applets)
gnome-netstatus-applet
gnome-nettool
gnome-panel
gnome-system-tools
gnome-utils
hostname
hpijs
hplip
ifupdown
(initramfs-tools)
iproute
iptables
iputils-ping
iputils-tracepath
libaudio2
libavahi-client3
libavahi-common3
libavahi-common-data
libavahi-glib1
libgtop2-7
libjessie-java
libkrb53
libmng1
libnetcdf3
libnspr4
libnss3
libcap0.8
libping12-0
libslp1
libsnmp9
libsnmp-base
libsoup2.2-8
libuniconf4.2
libwrap0
libwvstreams4.2-base
libwvstreams4.2-extras
mii-diag
mtr-tiny
netbase
netcat
net-tools	
ntpdate
openssh-client
pcmcia-cs
pcmciautils
python
python2.4
python2.4-eunuchs
python-netcdf
rsync
tcpd
tcpdump
vnc-common
wget
wpasupplicant
xvncviewer
*************************************************

Being in the same boat your are - or were - I'm interested.  I'm not quite ready reinstall yet but I'm curious what exactly screwed everything up so i can avoid it in the future.

---

### Post by tgbrowning on 2007-06-17
Well, so far I've not found anything that screws up the mounting of USB drives in my quest to figure out just what the hell happened. Maybe today. 

If anyone has any suggestions, I'd be glad to hear them.

My first thought was that somehow, my attempting to get Totem to play DVD movies might have been the cause, but I haven't been able to duplicate my earlier partial success and the mounting of USB drives is still funtioning. 

I'm planning on installing updates today, one by one, checking to see if one screws up the USB drive. I'll keep a list to see what might or might not be the problem. I kind of suspect that an update was installed that conflicts, somehow, with something already on board and working. We'll find out.

Browning>>>

---

### Post by tgbrowning on 2007-06-17
Okay, gone through all of the possible updates and my USB drives still mount just fine. It must have been something new that I had loaded and I'm going to have to mess around to figure out what they might have been. I'm afraid I didn't keep very good records.

New question, however:  I have listing in the Synaptic Package Manager that one of the libraries I have install is "Local or obsolete" -- libdvdcss2.  

What does that mean, precisely?

Browning>>>

---

