---
title: "Ubuntu 6.06 Server - Raid5 Issues"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-11-13
Hi All,

Got a strange one....

I have setup a Hardware Raid 5 on my 6 SAS Hard Drives which are 146.8GB each, which means Ubuntu should see only: 683.56GB...

However, Ubuntu sees all Six Disks and the space for Hard Disk formatting is 733.97GB

Any Ideas why Ubuntu is see the all the Disks and not the RAID?

Thanks for reading

Regards

Robin

---

### Post by robinlennox on 2007-11-13
*BUMP* :confused:

---

### Post by PointyWombat on 2007-11-13
what's your controller?  most mobos with built-in controllers rely on a windows raid driver to function and are not true raid controllers at all. these are commonly referred to as fake raid controllers .. support of which is limited in linux, but there has been some progress. Try this [link]("https://help.ubuntu.com/community/FakeRaidHowto") for more info.

PointyWombat

---

### Post by robinlennox on 2007-11-13
I'm Using a IBM ServeRAID-8k.... Is this a fakeraid! :confused:

---

### Post by PointyWombat on 2007-11-13
if it's built into the motherboard, then most likely.

---

### Post by overdrank on 2007-11-13
> **robinlennox said:**
> Hi All,

Got a strange one....

I have setup a Hardware Raid 5 on my 6 SAS Hard Drives which are 146.8GB each, which means Ubuntu should see only: 683.56GB...

However, Ubuntu sees all Six Disks and the space for Hard Disk formatting is 733.97GB

Any Ideas why Ubuntu is see the all the Disks and not the RAID?

Thanks for reading

Regards

Robin

HI maybe this link will help
[http://cgi.cse.unsw.edu.au/~neilb/mdadm](http://cgi.cse.unsw.edu.au/~neilb/mdadm)
Good luck!
Edit one more link
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html)

---

### Post by robinlennox on 2007-11-14
I have Googled various of sites... and most of them don't say it hardware or software raid....

I'm reluctant to use fakeraid... as this puts an additional strain on the OS.

---

### Post by robinlennox on 2007-11-14
[FONT=Tahoma]This seems really odd to me... maybe someone can help:

Just run fdisk -l from the terminal and got:

Disk /dev/sda: 733.4 GB, 733457940480 bytes
255 heads, 63 sectors/track, 89171 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      208813+  83  Linux
/dev/sda2              27        1333    10498477+  83  Linux
/dev/sda3            1334        2379     8401995   82  Linux swap / Solaris
/dev/sda4            2380       89171   697156740   83  Linux

However if i go into Webmin then:

Hardware > Partitions on Local Disks; I get the following which is set in ServRAID 8k:[/FONT]
          [FONT=&quot]
[ [IMG]http://hotimg16.fotki.com/a/82_211/102_159/partitions.jpg[/IMG]]("http://hotimg16.fotki.com/p/a/82_211/102_159/partitions.jpg")

[FONT=Tahoma] Any Ideas, Why fdisk is showing all disks without raid and Webmin is showing the Raid5 partitions?[/FONT][/FONT]

---

### Post by robinlennox on 2007-11-14
*Bump*

Any Ideas?

---

### Post by PointyWombat on 2007-11-14
What does the following show?

df -lB1024

and

df -kl

---

### Post by schorsch on 2007-11-14
I'm pretty sure that your ServeRaid adapter (I hate IBM servers ...prefer HP :-) ) is not a fakeraid one. If Ubuntu would not see the raid the command"fdisk -l" would report any of the six discs and not just one /dev/sda. Furthermore six discs with 146.8 GB resp. would show as ~880 GB. But why are you using such a large /var filesystem? Is your system a really large webserver?

---

### Post by PointyWombat on 2007-11-14
Also, looking at this, consider that the fdisk view is block level based, but it appears that the webmin view (as it pertians to how it's determing the disk space) is file system based. This makes sense in that

Your original 6 X 146GB disks = ~876GB
RAID 5 parity (1 Disk) = 876-146G= ~730GB
ext3 filesystem overhead for root reserved (5%)  = ~37GB
ext3 filesystem overhead for journalling ( ?%) = Roughly what you're seeing with 680GB at the filesystem level.

---

### Post by robinlennox on 2007-11-16
> **PointyWombat said:**
> What does the following show?

df -lB1024

and

df -kl

When I run:df -lB1024, I get the following...

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             10333488    805832   9002736   9% /
varrun                 1030544        60   1030484   1% /var/run
varlock                1030544         4   1030540   1% /var/lock
udev                   1030544        96   1030448   1% /dev
devshm                 1030544         0   1030544   0% /dev/shm
lrm                    1030544     21512   1009032   3% /lib/modules/2.6.15-29-amd64-xeon/volatile
/dev/sda1               195694     23779    161475  13% /boot
/dev/sda4            686217780    561964 650797980   1% /var

When I run: df -kl, I get the following...

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             10333488    805832   9002736   9% /
varrun                 1030544        60   1030484   1% /var/run
varlock                1030544         4   1030540   1% /var/lock
udev                   1030544        96   1030448   1% /dev
devshm                 1030544         0   1030544   0% /dev/shm
lrm                    1030544     21512   1009032   3% /lib/modules/2.6.15-29-amd64-xeon/volatile
/dev/sda1               195694     23779    161475  13% /boot
/dev/sda4            686217780    561964 650797980   1% /var

---

### Post by robinlennox on 2007-11-16
> **PointyWombat said:**
> Also, looking at this, consider that the fdisk view is block level based, but it appears that the webmin view (as it pertians to how it's determing the disk space) is file system based. This makes sense in that

Your original 6 X 146GB disks = ~876GB
RAID 5 parity (1 Disk) = 876-146G= ~730GB
ext3 filesystem overhead for root reserved (5%) = ~37GB
ext3 filesystem overhead for journalling ( ?%) = Roughly what you're seeing with 680GB at the filesystem level.

As, I'm a Noob at RAIDS....

I used: [http://www.ibeast.com/content/tools/RaidCalc/RaidCalc.asp](http://www.ibeast.com/content/tools/RaidCalc/RaidCalc.asp)

To calculated how much space I should be seeing for RAID 5, 

Number of Disks: 6 
Space of each drive: 146.8 (GB)

Which they work it out to be

Total Array Size: 733.67 GB
Total Useable Disk Space: 683.56 GB

Theses totals tally with IBM ServeRAID Management Software....

My concern is that the /dev/sda4 697 GB EXT3 /Var Partition is reading as more then the usable diskspace this is why I think their is a problem with Ubuntu....

> But why are you using such a large /var filesystem? Is your system a really large webserver?I thought it would be easier to manage, if someone with no linux experience had to take over my job.

---

### Post by robinlennox on 2007-11-16
*bump*

Any Ideas?:confused:

---

### Post by robinlennox on 2007-11-17
*bump*

Any Ideas?:confused:

---

### Post by robinlennox on 2007-11-19
*bump*

Any Ideas?:confused:

---

### Post by robinlennox on 2007-11-19
I've run out of Ideas... Does no-one have any other Ideas; I could try to get Ubuntu working on a RAID5, ServeRAID8K controller.

Otherwise, it looks to be a Windows Solution :(

---

