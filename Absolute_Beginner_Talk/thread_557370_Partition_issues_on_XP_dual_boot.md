---
title: "Partition issues on XP dual boot"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by eljaydub on 2007-09-22
I'm just getting started with Linux and Ubuntu and did some reading before I started the install but I'm having trouble with the partitions. I have a C: primary partition for XP and a D: logical partition for NTFS data. I tried to use gparted on my livecd to use the D: empty space for 3 new partitions:
100mb Ext3 (for /home)
2GB swap
30 GB Ext for data (/root or / ?) 
When I tried to apply the changes I got an error but no info on what error, however a lock appeared over the 2 existing partitions. I then used Acronis in XP to create a logical 2gb swap, logical 30gb ext3, and a  primary100mb Ext3 (again for /home, on the advice I read in a book and on a forum). Applying the changes went smoothly but these drives (G:, H:, I: ) do not show up in  My Computer'. They do show up when I open Acronis though. 
I then booted into Ubuntu off the cd and tried to install, selecting "Manual" at the partition window. Now NONE of my partitions show up, not even the 2 original ones. All that appears is a greyed out single partition of all my 250gb which the program claims is 'Unallocated'.  I cancelled and checked gparted which showed the same thing.
Anyone know whats wrong or what to do here?
Thanks!

---

### Post by Pumalite on 2007-09-22
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Duck2006 on 2007-09-22
> 100mb Ext3 (for /home)
2GB swap
30 GB Ext for data (/root or / ?) 

10Gb /   root
  1Gb swap
the rest for home 
Thats where your files are keeped.
If for some reason you have to reinstall your files will still be there 
(don't format the home partition if you have to reinstall)

---

### Post by eljaydub on 2007-09-22
Here are some screenshots of what I am seeing

---

### Post by eljaydub on 2007-09-22
I found this interesting: When I went to put the screenshots on my Lexar usb stick it showed the new partitions in the side window...so ubuntu knows they are there?

---

### Post by Pumalite on 2007-09-22
If you followed my link, you should be ready to install.

---

### Post by eljaydub on 2007-09-22
Here is what sudo fdisk -l showed:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       30401   202250317+   5  Extended
/dev/sda3           26421       26484      514080   83  Linux
/dev/sda5            5223       26093   167646276    7  HPFS/NTFS
/dev/sda6           26094       26420     2626596   82  Linux swap / Solaris
/dev/sda7           26485       30401    31463271   83  Linux

Disk /dev/sdb: 2029 MB, 2029518848 bytes
243 heads, 32 sectors/track, 509 cylinders
Units = cylinders of 7776 * 512 = 3981312 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     1981936    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 242, 32) logical=(509, 184, 32)

---

### Post by eljaydub on 2007-09-22
Thanks for the link Pumalite but I had already read that page before I started the install/parition. Is there anything specific no the page that I may have missed on the first reading?
Thanks for your help

---

### Post by Pumalite on 2007-09-22
You have trouble with the partition table in sdb1:

/dev/sdb1 1 510 1981936 4 FAT16 <32M
Partition 1 has different physical/logical endings:
phys=(249, 242, 32) logical=(509, 184, 32)
__________________

---

### Post by eljaydub on 2007-09-22
Ok thanks,so what can or should I do about that?

---

### Post by eljaydub on 2007-09-22
and shouldn't every show as hda and not sda?

---

### Post by Duck2006 on 2007-09-22
> shouldn't every show as hda and not sda?

FF shows all hard drives as sdX so it you have hdx or sdx it will show up as the same.

---

### Post by Pumalite on 2007-09-22
> **eljaydub said:**
> Ok thanks,so what can or should I do about that?

Use rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) and examine and fix your drive if necessary.

---

### Post by eljaydub on 2007-09-22
OK I just ran the System Restore CD  and then TestDisk but honestly I have no idea what it is I'm supposed to be doing... sorry but I'm new at this and don't understand the problem at all...

---

### Post by eljaydub on 2007-09-22
Ok so that physical/logical problem was on my usb and had nothing to do with the partitions. With the USB removed here is what sudo fdisk -l gives:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       30401   202250317+   5  Extended
/dev/sda3           26421       26484      514080   83  Linux
/dev/sda5            5223       26093   167646276    7  HPFS/NTFS
/dev/sda6           26094       26420     2626596   82  Linux swap / Solaris
/dev/sda7           26485       30401    31463271   83  Linux

---

### Post by Pumalite on 2007-09-22
You are fine then. You have something installed in sda7?

---

### Post by eljaydub on 2007-09-22
I believe that is the 30gb ext3 partition for /root that Acronis created, I think the one that doesn't belong is the sda2 one, it's 202gb? I have no idea what that one is... (my hd is 250gb Maxtor SATA)
Any ideas as to what the problem with the installer is then? Why doesn't it (or gParted) recognize that there are any partitions?

---

### Post by Pumalite on 2007-09-22
The rescuecd has a partitioner too. It usually succeeds where Gparted fails. Give it a try.

---

### Post by eljaydub on 2007-09-22
OK the other System Rescue partitioner sees the partitions that Acronis created and the pre-exsiting partitions no problem but the Ubuntu installer (and gparted of course) still doesn't recognize any partition  which means I can't install Ubuntu. Where do I go from here?

---

### Post by Pumalite on 2007-09-22
Do the partitioning with rescuecd, create 10 GB for '/', 500 MB for /swap and the rest for /home; install>Manual and use the partitions created. You'll be OK.

---

### Post by tomot on 2007-09-22
> **eljaydub said:**
> OK the other System Rescue partitioner sees the partitions that Acronis created and the pre-exsiting partitions no problem but the Ubuntu installer (and gparted of course) still doesn't recognize any partition  which means I can't install Ubuntu. Where do I go from here?

may I just say you have balls! (unless you are a women) :)

I have not even attempted a dual boot yet for fear of losing my original install of XP
or being able to read any of my data only HDD's 
I finally was told to remove all of my Hdd's except the one I wanted to install Ubuntu on
and that FINALLY was the only way I was able to get Ubuntu to boot after the install.
then after I replaced my data Hdd's Ubuntu would not boot at all.

I think the entire install process of Ubuntu is still a work in progress, and many failures 
lie ahead in this area for newbies.  goodluck!

my 2 cents

---

### Post by Pumalite on 2007-09-22
Life has to be lived with courage. And we learn with the knocks. That's how one day we get to be wise.

---

### Post by eljaydub on 2007-09-23
Good news! I am posting this message from a fully functional Ubuntu/XP dual boot. Here's what happened:

I tried to use the SystemRescue partitioner with no success so I went back to Acronis and deleted the 3 partitions I had created earlier. This gave me 33gb of unallocated space. I booted from the Ubuntu LivedCd and used gParted to split that 33gb into an 11gb ext3 and a 2gb swap leaving 20gb unallocated for now. I then installed Ubuntu with just root and swap and here I am. Windows is also working fine. 

Some issues to be resolved: I wanted to have a /home partition, a /boot partition, a swap, and a root but gParted would not let me create logical volumes hence I was limited to creating 2 primaries (root and swap) because I already had the C: (a primary) and D: (A logical under a primary umbrella?). How can I get gParted to create those logicals? GParted says to create them under an extended format or something but this is not an option under 'use format'(or whatever). I'm just going to start playing with it for now until the next Ubuntu release next month but I want to know how to do it right when that time comes. 
Also, my screen is shifted to the right and off the side about 5mm. I am running the amd64 version and I noticed the i386 did not do this. How can I fix it?(I played with the monitor already, it appears to be a software thing)


PS My understanding is that: root is where all the system(OS etc) and programs will be, /home is where all my settings and files are(or will be when I get the partition fully figured out). Is the /boot a partition that just contains the OS, making root just have programs? I am just trying to make it easy to install new versions and recover from crashes etc..

Thanks for all the help!

---

