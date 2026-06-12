---
title: "'GDM could not write to the authorization file'"
date: 2005-10-07
forum: Apple PPC Users
---

### Post by anechoic on 2005-10-07
I have two machines (both of which dual boot into Ubuntu 5.04 and OS X 10.3.9)
- an iBook G3 running Ubuntu 5.04 (all current updates) on a 4G partition 
- an iMac DV G3 running Ubuntu 5.04 (all current updates) on a 5G part

I have a 10G external (pocket) firewire drive which I formatted on the iBook as an ext3 fs drive
the drive shows up on my iBook after plugging it in (I guess hotplug handles the automount)
I backed up my iBook onto this drive using rsync as follows:
sudo rsync -av --progress / /media/ieee1394disc/foo1

it worked -- but I got some errors:
=====================================
 rsync: read errors mapping "/sys/class/net/eth0/carrier": Invalid argument (22)
 sys/class/net/sit0/carrier
         4096 100%    3.89kB/s    0:00:01  (123074, 38.8% of 174409)
 rsync: read errors mapping "/sys/class/net/sit0/carrier": Invalid argument (22)
 sys/devices/pci0000:00/0000:00:10.0/rom
       131072 100%   97.49kB/s    0:00:01  (123075, 38.9% of 174409)
 rsync: read errors mapping "/sys/devices/pci0000:00/0000:00:10.0/rom": Invalid argument (22)
 sys/devices/pci0002:20/0002:20:0f.0/rom
      1048576 100%    5.49MB/s    0:00:00  (123076, 39.2% of 174409)
 rsync: read errors mapping "/sys/devices/pci0002:20/0002:20:0f.0/rom": Invalid argument (22)
 ERROR: sys/class/net/eth0/carrier failed verification -- update discarded.
 ERROR: sys/class/net/sit0/carrier failed verification -- update discarded.
 ERROR: sys/devices/pci0000:00/0000:00:10.0/rom failed verification -- update discarded.
 ERROR: sys/devices/pci0002:20/0002:20:0f.0/rom failed verification -- update discarded.

 sent 2661690634 bytes  received 2461540 bytes  526044.46 bytes/sec
 total size is 2652949812  speedup is 1.00
 rsync warning: some files vanished before they could be transferred (code 24) at main.c(702)
============================================
but I saw my iBook's HD was on the backup drive -- although I am not sure how to verify the backup...

anyway...

I took the drive physically and plugged it into the iMac DV

it didn't show up on the iMac DV but I am able to cd to /media/ieee1394disc 

so I assumed it automounted but for some reason didn't place an icon on the desktop...I have it set up that Computer, Home and Trash all show up on the desktop...

I wanted to back up the iMac DV as well so I ran rsync on this machine

sudo rsync -av --progress / /media/ieee1394disc/foo2

it spews stuff to the terminal for a while and then ends with some error messages...they look a little different than the errors I got on the iBook

I'm not sure what happened but then I ran gparted  and it scanned for volumes but found nothing...something seemed wrong so

I rebooted the machine

and I get the Gnome splash screen with the login window

I enter the correct username and pswd

and I get a small error window which states:

'GDM could not write to the authorization file...
You are either out of disc space or the home dir could not be opened for writing'

I removed the external firewire drive and reboot again...

the same error message appears...

==========================
so my questions are:
	- how do I solve this?
	- did I inadvertently write to the same partition on the internal drive (and not the external firewire drive) therefor filling it to the max?
	- or did the rsync backup clobber an auth file? 
		- and if so how do I fix it?

I tried booting into 'live-expert-powerpc' mode from the Live CD
but I cannot cd to the drive for some reason

I suspect that I either have to delete the backup to free up room on the drive -- wherever the backup is on the HD
or I have to repair permissions on the authorization file...

anyone offer some insight and help?

thanks in advance!
KIM

---

