---
title: "NAS setup on Ubuntu"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by blu4899 on 2007-03-23
Hi,

I'd like to setup an Ubuntu server in my home network, with one of its prime usages being network attached storage for Windows clients. It should be able to do other things as well such as web server, tivo home server, etc, so I don't want to use a pure NAS distribution of Linux. 

This is my setup:

Ubuntu Server:
1.4GHz Pentium 4  w/ 1GB of RAM
200MB Disk for Ubuntu OS and software
300MB SATA Disk in tray for data 
300MB SATA Disk in tray for backup + another one in a secure location. 

Windows Desktop
2.8GHz Pentium 4 w/2GB of RAM
300MB SATA Disk for Windows XP Prof, software, and short-term data use such as Video editing
using the Ubuntu 300MB network drive

Windows Laptop ...

So, now my questions: 

What FS would you recommend for the data partition on the Ubuntu server? I'd prefer a Windows-readable FS to have the option of connecting the disk to the other machine. I'd like a single 300MB partition. What are the performance implications?

Also, what software do you recommend for backup? I'd prefer something with a UI, I don't particularly like Unix commands. Backup should run every night; if there is something with a web ui so I can configure and restore remotely, that would be even better... Just mirroring the drive would also be an alternative; unfortunately the MB doesn't support SATA raid. 

Does gigabit Ethernet make a big difference in the above setup? What else can I do to maximize NAS performance?

Any other suggestions? Which Ubuntu distribution and additional software would you recommend? 

Thanks,
blu

---

### Post by blu4899 on 2007-03-29
:confused: anyone? Thanks!:)

---

### Post by sicofante on 2007-03-29
First of all, you have a pretty capable system for NAS uses. I can't confirm on the other server services you plan to use, but NAS is a very lightweight service for a server to provide, so just go ahead.

> **blu4899 said:**
> What FS would you recommend for the data partition on the Ubuntu server? I'd prefer a Windows-readable FS to have the option of connecting the disk to the other machine. I'd like a single 300MB partition.
Just use your ordinary ext3 partition and share it via SMB. It will be seen by every Windows machine in the network.


> What are the performance implications?Performance depends on network bandwidth and number of users connected to the server and accessing the disk at the same time. If you plan to access files from your NAS one client at a time, you will have little performance issues anyway. I recommend you use Gigabit Ethernet. Gigabit adapters are cheap these days. Spend just a little bit more on the switch for best performance. (HP, Dlink or Netgear have affordable and capable GbE switches.)


>  Also, what software do you recommend for backup? I'd prefer something with a UI, I don't particularly like Unix commands. Backup should run every night; if there is something with a web ui so I can configure and restore remotely, that would be even better... Just mirroring the drive would also be an alternative; unfortunately the MB doesn't support SATA raid. 
I'm sorry I don't know of any GUI solution. I would suggest anything based in rsync. Google around a bit, maybe someone has created some little app to manage rsync from a GUI.

You can manage the Ubuntu box remotely using VNC. I support Ubuntu remotely over ADSL using VNC and it's pretty manageable. Over a Gigabit network is almost like being there.

Regarding RAID, you don't need your motherboard to support it. You can do software RAID in Linux. I do not recommend RAID as a backup method though. A nightly good old backup will be safer than RAID-1.

>  Does gigabit Ethernet make a big difference in the above setup? What else can I do to maximize NAS performance?Yes it does. GbE has a maximum theoretical throughput of 125 MB/s (that's megabytes per second). Let's be conservative and suppose you won't get more than half of that on your network. It's still above what most ordinary SATA disks can provide to the system locally, so you're safe using GbE. Divide these figures by 10 and you'll see why old Fast Ethernet is not a good idea.

However, setting it all up is equally easy with an old Fast Ethernet infrastructure and you can update network speed later without even touching your setup.

>  Any other suggestions? Which Ubuntu distribution and additional software would you recommend? 
Honestly, ANY Linux distro will do for simple NAS purposes and Ubuntu is great. I just set up the other week an Openfiler NAS ([www.openfiler.com]("http://www.openfiler.com")) for a customer and it took me quite a while. I installed Ubuntu in the very same machine for testing purposes, and sharing a disk from Ubuntu took me about three mouse clicks...

Good luck!

---

### Post by dannyboy79 on 2007-03-30
simple backup is a great backup solution for backing up your linux server. its also referred to as sbackup. it was developed in the google summer of code in 2005 I think. it's great and still being developed. I use it now. I am in the process to make sure tha my backups work, I am restoring to a different partition and am going to add an entry for it in grub and fix the fstab and see if it's boots and runs, this way I know that if my computers ever crash I have a recovery method and it's been tested! look into freenas if you just want a nas distro, you don't need ubuntu. but if you want to learn linux and use ubuntu than freenas wouldn't be the way to go,. [http://www.freenas.org/](http://www.freenas.org/)
it's a minimal bsd version of linux specialized for supporting: CIFS (samba), FTP, NFS, AFP, RSYNC, iSCSI protocols, S.M.A.R.T., local user authentication, Software RAID (0,1,5) with a Full WEB configuration interface. FreeNAS takes less than 32MB once installed on Compact Flash, hard drive or USB key.
The minimal FreeBSD distribution, Web interface, PHP scripts and documentation are based on M0n0wall.
Heck you could install it on a usb flash stick that way you;d have that other 200gb hard drive for storage. good luck

---

### Post by sicofante on 2007-03-30
FreeNAS and Openfiler are great NAS distros but the OP clearly stated:
> **blu4899 said:**
> It should be able to do other things as well such as web server, tivo home server, etc, so I don't want to use a pure NAS distribution of Linux.

SBackup looks nice. I'll try it myself.

---

### Post by iduriduridur on 2007-04-29
I would suggest installing EVMS and evms-gui for RAID setup. Once you learn the gui it is pretty easy to use. Novell has some good writeups with picts on the web. 

EVMS is a volume manager that does it all.

OK so install ubuntu and leave 2 "raid disks" alone.
install evms-gui setup raid 1

I know raid is not a backup. 

There are a lot of backup programs with a gui under synaptic package manager. In evms you can put in a 3rd disk and add it as a hot spare. You could then backup nightly to another machine. 

backuppc is nice.

---

