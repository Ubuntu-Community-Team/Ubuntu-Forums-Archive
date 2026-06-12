---
title: "Externial hardware drive problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-11-16
Greetings all,
I am getting some weird errors with my external hard drive.  When I plug my hard drive, I get an icon on my desktop for the drive, but when I try to open it, I get an error stating that nautilus can not open media, use a different viewing program.  I can access the drive through other programs (like VLC or Amarok).  Now when I try to mount the drive I get this error message

Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

I have no idea what is going on now.  Any ideas?

---

### Post by Shinbu-Otaku on 2007-11-16
it would appear that your external hard drive is NTFS partitioned. Although i think linux can read these, it has a damn hard time doing so. Your best bet would be to format it to a linux equiviliant (ext3 i think the main one is called or something like that) and then it should be fine. If however you need it for windows awell, format it to FAT16 or FAT, because i think these work fine with both windows and linux.

hope that helps

---

### Post by mangurt on 2007-11-16
Doh,
I don't want to format it (I have a lot of information on it (music, movies, ect).  I was hoping there was something else I could do.

---

### Post by laidback on 2007-11-16
You could just set up a partition for Linux leaving the current data on NTFS.
I suspect that you'll need to take a section of the drive and allocate it to Linux as the current format will most probably have taken the entire drive for NTFS. Be careful, before you do this, clean the NTFS partition with the Windows program for sorting out hdds (cannot remember its name, sorry), defragment it also. It can also be sensible to back up important data.
In Ubuntu there is a program called Gparted which will repartition your external hdd for you. It may already  be available via System>Administratiion>Gnome Partition Editor. If not you can get it via Synaptic whci will place an item on the menu for you.

Gparted allows you to view the hdds on your system. BUT...you can only alter partitions that are NOT mounted. If you find that your external hdd is mounted there is an Unmount option within Gparted. Once you have your exernal hdd selected and unmouted you will be able to reduce the size of your NTFS partition, using the new freed space to create an Ext3 partition for Ubuntu. You can format it from within GParted. I find it all quite straight forward and intuitive to use. If not there is a Gparted web site, Google for it.

Hope this helps.


If you really want to go to town I would advise you get hold of the Gparted Live CD, ISO available from the Gparted site. It's bootable and allows you therefore to alter your main hdd partitions as well as external ones. It has a more up to date version of Gparted as well. A very handy tool.

---

