---
title: "[SOLVED] Installed Fedora 8 on Ubuntu/XP, but no Fedora in Grub and Ubuntu &amp;quot;error&amp;quot;"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by conradinsf on 2008-01-24
I think this post is different than other posts, and warrants a *new thread*.  Let me give a brief history of this...

I initially had a dual boot dual drive Ubuntu/XP system, which was previously a single drive XP.  With the new configuration, I set up the HDs to boot master Linux (SATA0) and slave XP (SATA1). I used PartedMagic to partition Master drive for ext3 partitions for Ubuntu, Needless to say, I did several Ubuntu installation before I ended up with my current and functional setup.  

After playing with the partitions using PartedMagic, I ended up with the following fdisk -l output:

> 
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16517   132672771    5  Extended
/dev/sda2           16518       68734   419433052+   7  HPFS/NTFS
/dev/sda3           68735      120951   419433052+   7  HPFS/NTFS
/dev/sda5               1        2550    20482812   83  Linux
/dev/sda6            2551        5737    25599546   83  Linux
/dev/sda7            5738        5868     1052226   82  Linux swap / Solaris
/dev/sda8            5869        7929    16554951   83  Linux
/dev/sda9            7930       11193    26218048+  83  Linux
/dev/sda10          13255       16517    26210016   83  Linux
/dev/sda11          11194       13254    16554951   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6       30392   244083577+   7  HPFS/NTFS


I have Ubuntu (/) on sda5, and (/home) on sda6.  Then, I tried to install** Fedora 8** (using LiveCD) on sda8 and sda9 (for / and /home, respectively) using manual install.  I believe I also installed MBR on sda8 (Fedora root).  Should I have installed MBR on sda1 (boot)?

I can boot up with XP fine.  When I try to start Ubuntu, I get an error **"File system check failed" **which I can bypass using Ctrl-D.  Then, Ubuntu starts fine (which is what I am on while I am posting).  

Another issue is that I don't know how to configure Ubuntu grub for Fedora boot, It shows up in grub, but when I select it, I get an error (which I forget, and I can post it on the next start-up). I guess I don't know how to configure the root 

My current grub configuration is the following:

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=eceacaa7-6d8c-4d96-92cf-1f4c0c92e9cd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=eceacaa7-6d8c-4d96-92cf-1f4c0c92e9cd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title Fedora
rootnoverify (hd0,6)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Windows XP
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Should I change "root=UUID=eceacaa7-6d8c-4d96-92cf-1f4c0c92e9cd" to "root=/dev/sda5" for Ubuntu?

I am also wondering if it is because I messed up the Fedora install?  At the end of the Fedora install, I only got a window saying that the install was completed.  My computer did not restart.  

Please help?!

---

### Post by logos34 on 2008-01-24
For Fedora try the ['configfile' boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile"). (you don't need the map commands for linux)

As for ubuntu and the filecheck error, I doubt the UUID in menu.lst is the problem--if it was it wouldn't mount at all.  I mean, you can try /dev/sda5, but I don't think it will help.

You could boot frm the ubuntu live cd and manually run a filesystem check, see if you get the same message, or maybe it will fix it, who knows.

sudo fsck /dev/sda5

or

sudo e2fsck -f -v -y /dev/sda5

ADD:
> 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
"Some Windows users have a program called Partition Magic, but many Ubuntu users have reported problems with setting up a dual boot after using Partition Magic. It's better to use one of these partitioning tools instead (and they're all cost-free). Here are some: QTParted - available on Knoppix live CDs. GParted - available as the default partitioning program for Ubuntu's Desktop CD. DiskDrake - available on PCLinuxOS's live/installer CD."

So, it *could* be related to PM.  Something to consider.

---

### Post by conradinsf on 2008-01-25
> **logos34 said:**
> For Fedora try the ['configfile' boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile"). (you don't need the map commands for linux)

As for ubuntu and the filecheck error, I doubt the UUID in menu.lst is the problem--if it was it wouldn't mount at all.  I mean, you can try /dev/sda5, but I don't think it will help.

You could boot frm the ubuntu live cd and manually run a filesystem check, see if you get the same message, or maybe it will fix it, who knows.

sudo fsck /dev/sda5

or

sudo e2fsck -f -v -y /dev/sda5

ADD:


So, it *could* be related to PM.  Something to consider.

- I'll try the ubuntu live cd, and run sudo fsck /dev/sda5

- PartedMagic uses GParted for partitioning.

---

### Post by rickycodie on 2008-01-25
the easiest thing that i have found is to mount the partition with the os that you want on it, go to grub/menu.lst copy the os's entry and paste it into ubuntu's grub/menu.lst. it usually works for me, only sometimes does it need tweaking.

---

### Post by logos34 on 2008-01-25
> **rickycodie said:**
> the easiest thing that i have found is to...go to grub/menu.lst copy the os's entry and paste it into ubuntu's grub/menu.lst...only sometimes does it need tweaking.

right, like after a kernel update.  Which is one of the advantages of configfile entry--you can set it and forget it.

---

### Post by smurphy_it on 2008-01-25
Your grub configuration doesn't look right to me.  I thought you had to subtract 1 to get at the real partition....

So your Ubuntu is pointing to (hd0,4) which is an NTFS partition SDA3, and your Fedora is pointing to (hd0,6) SDA5 which would be a Linux partition, but should be your Ubuntu distribution..

It looks to me like your Ubuntu entries should be (hd0,6) and your fedora entry should be (hd0,9).

Make a backup of your /boot/grub/menu.lst and then modify it... if anything goes wrong, you can boot a live cd and reverse the process.

That might explain some of your error messages (which weren't posted).

---

### Post by logos34 on 2008-01-25
> **smurphy_it said:**
> I thought you had to subtract 1 to get at the real partition....

sorry, incorrect. you add +1.  (hd0,4) = /dev/sda5

you need to [read this]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

But you're right about there being an error in the Fedora entry--I didn't catch that.  If it's sda8, then:

> title Fedora
**root (hd0,[COLOR="Red"]7[/COLOR])**
...

---

### Post by conradinsf on 2008-01-25
> **logos34 said:**
> For Fedora try the ['configfile' boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile"). (you don't need the map commands for linux)

As for ubuntu and the filecheck error, I doubt the UUID in menu.lst is the problem--if it was it wouldn't mount at all.  I mean, you can try /dev/sda5, but I don't think it will help.

You could boot frm the ubuntu live cd and manually run a filesystem check, see if you get the same message, or maybe it will fix it, who knows.

sudo fsck /dev/sda5

or

sudo e2fsck -f -v -y /dev/sda5

ADD:


So, it *could* be related to PM.  Something to consider.

I did both , sudo fsck /dev/sda5 AND sudo e2fsck -f -v -y /dev/sda5, but neither found any errors.  Honestly, I don't really know what to look for.  Maybe it is because / and /home are in different partitions?  When I tried for sda6 (where /home is), I got the following:

> 
**sudo fsck /dev/sda6**
[sudo] password for conrad:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)

/dev/sda6: recovering journal
/dev/sda6: clean, 1797/3204992 files, 368775/6399886 blocks

**sudo e2fsck -f -v -y /dev/sda6**
e2fsck 1.40.2 (12-Jul-2007)

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

    1797 inodes used (0.06%)
     112 non-contiguous inodes (6.2%)
         # of inodes with ind/dind/tind blocks: 170/11/0
  368775 blocks used (5.76%)
       0 bad blocks
       1 large file

    1349 regular files
     404 directories
       0 character device files
       0 block device files
      16 fifos
       0 links
      19 symbolic links (19 fast symbolic links)
       0 sockets
--------
    1788 files
  

Also, I tried to change to /dev/sda5 in menu.lst, but that didn't solve the problem either.  

Here's the error log that I copied from checkfs
> 
Log of fsck -C -R -A -a 
Fri Jan 25 18:18:07 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda6: clean, 1793/3204992 files, 368687/6399886 blocks
fsck.ext3: Unable to resolve 'UUID=f6e9cb28-3fbb-4058-be29-5ec55473e562'

/home: clean, 362/3286752 files, 152593/6554512 blocks (check in 3 mounts)
fsck died with exit status 8

Fri Jan 25 18:18:08 2008


---

### Post by logos34 on 2008-01-25
> **conradinsf said:**
>  When I try to start Ubuntu, I get an error **"File system check failed" **which I can bypass using Ctrl-D.  Then, Ubuntu starts fine (which is what I am on while I am posting).  

Another issue is that I don't know how to configure Ubuntu grub for Fedora boot, It shows up in grub, but when I select it, I get an error (which I forget, and I can post it on the next start-up). I guess I don't know how to configure the root 

Maybe the filesystem check failure is referring to ubuntu /home (sda6) rather than root partition:

> fsck 1.40.2 (12-Jul-2007)
/dev/sda6: clean, 1793/3204992 files, 368687/6399886 blocks
fsck.ext3: Unable to resolve 'UUID=f6e9cb28-3fbb-4058-be29-5ec55473e562'

Try replacing the 'UUID=...' in /etc/fstab with '/dev/sda6' -- see if that helps.

Otherwise fsck output looks normal. 

So, does Fedora boot with **root (hd0,[COLOR="Red"]7[/COLOR])**, as I suggested above?

I don't know what further to suggest for ubuntu root error message at boot other than reinstalling.

---

### Post by conradinsf on 2008-01-28
I found the log for the errors, but I don't know enough to see what I need to do to correct the error.  I did fsck, and it did find some errors.  I had to Ctrl-D out of it to boot up to Ubuntu.  What do I need to do to fix this problem?:confused:

I posted the output here:

> 
Log of fsck -C -R -A -a
Mon Jan 28 10:00:59 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda6 contains a file system with errors, check forced.
/dev/sda6: Inode 2600216, i_blocks is 1416, should be 720. FIXED.
/dev/sda6: Duplicate or bad block in use!
/dev/sda6: Multiply-claimed block(s) in inode 2600561: 5239254
/dev/sda6: Multiply-claimed block(s) in inode 2600686: 5239254
/dev/sda6: (There are 2 inodes containing multiply-claimed blocks.)

/dev/sda6: File /conrad/.mozilla/firefox/2qkzhkv5.default/prefs.js (inode #2600561, mod time Fri Jan 25 19:36:24 200
has 1 multiply-claimed block(s), shared with 1 file(s):
/dev/sda6: /conrad/.mozilla/firefox/2qkzhkv5.default/sessionstore.js (inode #2600686, mod time Fri Jan 25 19:36:24 200
/dev/sda6:

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck.ext3: Unable to resolve 'UUID=f6e9cb28-3fbb-4058-be29-5ec55473e562'

/home: clean, 362/3286752 files, 152593/6554512 blocks (check in 2 mounts)
fsck died with exit status 12


I ran fsck manually, as suggested, but it gave me a message saying that I had to unmount, or that running this utility on a mounted drive is bad (or something like that).  What do I need to do to run fsck on this drive?

---

### Post by conradinsf on 2008-01-28
I also tried to run apt-get update, and I got this:

> 
conrad@xxx:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 58.9kB in 2s (25.9kB/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Can this be the cause of the errors previously posted?

---

### Post by conradinsf on 2008-01-28
> **logos34 said:**
> Maybe the filesystem check failure is referring to ubuntu /home (sda6) rather than root partition:



Try replacing the 'UUID=...' in /etc/fstab with '/dev/sda6' -- see if that helps.

Otherwise fsck output looks normal. 

So, does Fedora boot with **root (hd0,[COLOR="Red"]7[/COLOR])**, as I suggested above?

I don't know what further to suggest for ubuntu root error message at boot other than reinstalling.


here's something I noticed when I was comparing the error log with the fstab file.  The "unable to resolve 'UUID=..." is pointing to the /root mount of Fedora, which matches the UUID of sda8 (Fedora / mount).  Does this mean that Ubuntu is trying to look for its /home mount (which is on sda6) on sda8?  I posted my previous post quoted below:

> 
Log of fsck -C -R -A -a
Fri Jan 25 18:18:07 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda6: clean, 1793/3204992 files, 368687/6399886 blocks
fsck.ext3: Unable to resolve 'UUID=f6e9cb28-3fbb-4058-be29-5ec55473e562'

/home: clean, 362/3286752 files, 152593/6554512 blocks (check in 3 mounts)
fsck died with exit status 8

Fri Jan 25 18:18:08 2008

Here's my current fstab file:

> 
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda5

UUID=eceacaa7-6d8c-4d96-92cf-1f4c0c92e9cd /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda6

UUID=9793d642-20e2-465f-b7e3-cad59e115801 /home           ext3    defaults        0       2

# /dev/sda2

UUID=139B15E6147CB728 /media/sda2     ntfs-3g    defaults,umask=0 0 0

# /dev/sda3

UUID=2F757E9A7E506B2A /media/sda3     ntfs-3g    defaults,umask=0 0 0

# /dev/sda8

UUID=f6e9cb28-3fbb-4058-be29-5ec55473e562 /media/sda8     ext3    defaults        0       2

# /dev/sda9

UUID=728b782c-11c7-4bfc-be60-d00588b3925e /media/sda9     ext3    defaults        0       2

# /dev/sda7

UUID=d4b7b11a-2b7c-4d2e-842c-47215030ed0c none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by logos34 on 2008-01-28
> **conradinsf said:**
> I also tried to run apt-get update, and I got this:

Can this be the cause of the errors previously posted?

I doubt it, that's a separate issue.

Did you try editing fstab as I suggested above (post #9)?  It's complaining about /home UUID and a firefox settings file.   The filesystem is clean but it dies at the end

maybe someone else has some ideas.

---

### Post by conradinsf on 2008-01-29
> **logos34 said:**
> I doubt it, that's a separate issue.

Did you try editing fstab as I suggested above (post #9)?  It's complaining about /home UUID and a firefox settings file.   The filesystem is clean but it dies at the end
maybe someone else has some ideas.

I did edit the settings in fstab to change the UUID to /dev/sda6, and that threw a big wrench in the works.  I couldn't boot up into Ubuntu because it was looking for /home, which did not mount when I changed the UUID.  

So I had to boot up with LiveCD and edit the fstab back to original, and somehow that fixed all the problems!!!  I know I did not change anything, because I just put # before the original settings, and then removed it to bring back the original setting, and now it works.  Well, I'll take it.  :guitar:

Regarding the** Firefox error**, I found a resolve for the Firefox error.  I ran the following
> apt-get update -o Acquire::http::No-Cache=True
This code sets the cache-control headers to turn caching off.  Like I said earlier, this fixed the firefox error.

---

### Post by conradinsf on 2008-01-29
> **logos34 said:**
> sorry, incorrect. you add +1.  (hd0,4) = /dev/sda5

you need to [read this]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

But you're right about there being an error in the Fedora entry--I didn't catch that.  If it's sda8, then:

Thank you for the link and the explanation.  Fedora did boot with root (hd0,7), as you suggested.  Now I have Fedora booting up, and now I can finally play with Ubuntu and Fedora 

You are a rock-star :guitar:

---

### Post by dirk_diggler on 2008-01-29
> **conradinsf said:**
> I did edit the settings in fstab to change the UUID to /dev/sda6, and that threw a big wrench in the works.  I couldn't boot up into Ubuntu because it was looking for /home, which did not mount when I changed the UUID.  

So I had to boot up with LiveCD and edit the fstab back to original, and somehow that fixed all the problems!!!  I know I did not change anything, because I just put # before the original settings, and then removed it to bring back the original setting, and now it works.  Well, I'll take it.  :guitar:

Regarding the** Firefox error**, I found a resolve for the Firefox error.  I ran the following

This code sets the cache-control headers to turn caching off.  Like I said earlier, this fixed the firefox error.

This code helped.  Thanks!

---

### Post by logos34 on 2008-01-29
> **conradinsf said:**
> So I had to boot up with LiveCD and edit the fstab back to original, and somehow that fixed all the problems!!!  I know I did not change anything, because I just put # before the original settings, and then removed it to bring back the original setting, and now it works.  Well, I'll take it.  :guitar:

oh, the mysteries of linux!  

Enjoy Ubuntu and Fedora!

---

