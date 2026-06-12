---
title: "totem mounting problem"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by matthewstory on 2005-11-22
I'm running Ubuntu 5.10 on a Dell Inspiron 8200 with a CD-RW/DVD-ROM combo drive, i'm also running it partitioned so i can use both windows and ubuntu.  I repartitioned the drive when I installed ubuntu rewriting a partition that used to house Suse 9.1.  

My problem is this, when i put a DVD into the combo drive and try to open it in the totem movie player it doesn't recognize the disk and i get an error saying: 
"Failed to find mountpoint for device /dev/hdb in /etc/fstab."  
If i mount the disk manually in a terminal window with 
$ mount /dev/hdb, 
it recognizes the disk as being a DVD and i can get it to try to open the DVD but i get an error message reading:
 "Error invoking "dvdnav_get_next_block": Error reading from DVD.."  
I havn't updated or added any codecs to totem, and i'm using totem as it is out of the box.  Any help with this would be great.  

On a somewhat related note (and this is super noobish so appologies in advance) I was wondering what package to search for with Synaptic to support other codecs (specifically vob, xvid and x264).  If the answer to all of this is to get MPlayer then i am wondering if it is possible to get a complete package on Synaptic (my attempts to do this have resulted in unresolvable dependencies) or if i'll just have to build the app.

regards,
Matt

---

### Post by Original Brownster on 2005-11-22
Hi,
Do you have just the one cdrom / dvd drive? I am suprised that there is no mount point for it, take a look at the /etc/fstab file,
from a console :$ less /etc/fstab

 there should be a line for the device /dev/hdb, this is what it looks like in my file:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

If no line exists for the device add one similar to above substituting /dev/hdc/ with /dev/hdb

backup your existing file in case you screw it up first ;) :

$ sudo cp /etc/fstab /etc/fstab.bak

use your favourite editor :
$ sudo gedit /etc/fstab

and add the line mentioned and then try inserting a disk, it should mount automatically onto the mount point mentioned in the above line. Assuming

---

### Post by matthewstory on 2005-11-22
Yes, i only have one CD-RW/DVD-ROM drive, and there is a mount point in the fstab file, i can mount to it in a terminal window ($ mount /dev/hdb) and the CD player application mounts to it automatically and plays audio CDs, but totem doesn't mount to it, and if I mount to it in a terminal window it's blocked from totem, the problem could be that i don't have the right add-on for totem to play DVDs, but reading the documentation it looks like totem is supposed to play DVD "out of the box:"

* DVD (with menus), VCD and Digital CD (with CDDB) playback

regards,
matt

---

### Post by Original Brownster on 2005-11-22
ah, totem out of the box will only play unencrypted dvds, not shop bought ones.
Because of legal issues the necessary library to play them is not supplied in the main repository, you need libdvdcss2 which you can either download and install manually, or add an extra repository to your apt sources.list file. 
I am using 
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

They also do win32codecs which are useful for playing wma files etc.

---

### Post by matthewstory on 2005-11-22
I installed the package, I still get an error if i don't mount the drive in the terminal window, but if I do mount the drive I don't get an error, but it also doesn't actually play the DVD.  I would think it was a driver issue for the DVD player functionality of the combo drive, but i have vobcopy and HandBrake running and i can successfully rip down DVDs and encode them.  Thanks for the repository though.

cheers,
matt

---

### Post by Original Brownster on 2005-11-22
Hi,
It does sound like it might be a driver issue.
What about in 'system > admin > disks'
If you look at the cdrom entry here maybe that will give a clue as to whether it's been recognised as a dvd player correctly? I have a combo drive and I have ticks against all the supported features listed. If yours reports this correctly that narrows it down a bit as it's not a driver issue.

---

### Post by sjh on 2005-11-23
<I haven't updated or added any codecs to totem, and i'm using totem as it is out of the box.  Any help with this would be great.  

Totem out of the box is Totem-gstreamer.  With all the packages loaded I could not get it to work.  With Synaptic, I loaded Totem-xine and things started to work.  

Note:  Don't uninstall Totem-gstreamer, just load Totem-xine and Synaptic will take care of the details.

SJH

---

### Post by matthewstory on 2005-11-23
I installed the totem-xine package, and totem still can't find the mount point itself, but if i mount the disk in a terminal window totem can open and play the volume.  Thanks alot for the help, now I just need to find out why it's not automatically mounting the combo drive when i select to play it.

cheers,
matt

---

