---
title: "Too many Ubuntu's!"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by AccuDave on 2006-12-17
I am new to Ubuntu and have had many problems getting things going. I don't mind too much because I am a curious sort and fixing broken things is a good way to learn how they work. At one point I decided to re-install ubuntu from the LiveCD which fixed a lot of problems, However, my original Ubuntu install is still there in all it's Frankenstein glory. I would like to delete that sorry chapter in my life and reclaim the hard drive space for my good install. Any ideas? I have 2 installs of Dapper, the default one is the good one.

---

### Post by maxamillion on 2006-12-17
I assume you just repartitioned your drive to allow a second installation so I would recommend making sure what partition your "good" install is on and then booting the live cd and using gparted (Gnome Partition Manager) and just extending that partition to the entire size of the physical hard drive. This will simply overwrite the lost space on the hard drive in the partition table and the file system will see it as blank.

/me

---

### Post by AccuDave on 2006-12-17
How do I tell which is the good partition? I also have win xp spread across 2 hard drives and I am not ready to lose it yet.

---

### Post by maxamillion on 2006-12-17
enter the command "df -h" in the terminal (without the quotes) and paste the results on the forum and we can work from there

/me

---

### Post by xyz on 2006-12-17
How about posting the output of the following command line:
In a terminal:
```
sudo fdisk -l
```
Thx.

---

### Post by xpod on 2006-12-17
> I am new to Ubuntu and have had many problems getting things going. I don't mind too much because I am a curious sort and fixing broken things is a good way to learn how they work. At one point I decided to re-install ubuntu from the LiveCD which fixed a lot of problems, However, my original Ubuntu install is still there in all it's Frankenstein glory. I would like to delete that sorry chapter in my life and reclaim the hard drive space for my good install. Any ideas? I have 2 installs of Dapper, the default one is the good one.
Reply With Quote 

If you want to start afresh with a nice clean slate why dont you just wipe the whole lot and do one nice clean install.......It`s so quick to re-install that it`s sometimes the quickest option those first weeks when your just trying to get it all the way you want it.It`s all good practise and you will probably change it many times those first months anyway

Not sure how many drives you have but i have 2 with Dapper on one and Edgy on another which is great for a pc novice like myself.I can mess about with edgy and keep Dapper in good nick....by not doing tooo much to it.If anything goes wrong in one i know i got the other:mrgreen: 

Of course we`ve also got the other pc with multi hd`s and multi os`s so theres always one somewhere i can turn to:-\" .

Either way you can use the Gparted cd or the one on Ubuntu to delete and reclaim any old setups\partitions you want..

Good luck and...have fun:D

---

### Post by AccuDave on 2006-12-17
Here goes

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             7.4G  2.2G  4.8G  32% /
varrun                126M   80K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  160K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/sda1             496M  253M  244M  51% /media/SONY 512 MB
/dev/hda1              30G   25G  5.4G  82% /tmp/disks-conf-hda1
 I have an hdb but it doesn't seem to have an access path from here.

---

### Post by AccuDave on 2006-12-17
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3849    30917061    7  HPFS/NTFS
/dev/hda2   *        3850        4824     7831687+  83  Linux
/dev/hda3            4825        4870      369495    5  Extended
/dev/hda5            4825        4870      369463+  82  Linux swap / Solaris
Here is the fdisk stuff.


Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1023     8217243   83  Linux
/dev/hdb2   *        1024        7383    51086700   83  Linux
/dev/hdb3            7384        7476      747022+   5  Extended
/dev/hdb5            7384        7476      746991   82  Linux swap / Solaris

Disk /dev/sda: 520 MB, 520093696 bytes
32 heads, 32 sectors/track, 992 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         992      507888    6  FAT16

---

### Post by maxamillion on 2006-12-17
well it would appear I failed to make sure the other partitions were mounted, so xyz's command was more applicable.

It appears you still have a windows partition in existence which I assume to some would be good news.

---

### Post by AccuDave on 2006-12-17
What I really wanted was windows on one hard drive and linux on the other but I could not get it to work. Ubuntu had to be on the same drive I boot windows XP with for some reason. It was very confusing. I was happy to get it working even if it was hosed up. I just installed gparted so I'll check that out.

---

### Post by bulldog on 2006-12-17
It seems your good ubuntu is on hda2 and the bad one is on hdb.

There's another linux partition on the hdb ,hdb1 don't know what the meaning is of this one,but i suggest to get the data you want to keep from hdb and wipe the whole disk and re-partition and re-format as you like.

Also remove the sda which is probably a USB stick to avoid confusion.

After done so do an ```
sudo update-grub
``` and the non existing linux will be removed from your menu.lst.

To repartition and reformat your hdb,I recommend the gparted live cd it's only a download of 30MB,burn it to a disk and boot from it.
You have a graphical partitioner, like Partition Magic which can do the job with ease for you.
Find it here,

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Let us know if you have any questions before you begin.

---

### Post by bulldog on 2006-12-17
> **AccuDave said:**
> What I really wanted was windows on one hard drive and linux on the other but I could not get it to work. Ubuntu had to be on the same drive I boot windows XP with for some reason. It was very confusing. I was happy to get it working even 
if it was hosed up. I just installed gparted so I'll check that out.

If you want a dual boot from two different disks just say so we can manage that :D 
I take a look and post back on you,just download and burn the gparted live cd.
You must destroy your other ubuntu too,if you don't mind to do so.

You have two IDE drives,one master and one slave as I can see.
To get it the way you want in a few steps.
Can you boot,by changing the BIOS or what ever,from the second disk hdb?
If so it's easy,if not you have to switch your drives fysically,this means disconnect the both drives and set hda as a slave [jumpers on the back of the drive] and hdb as the master in the same way.
This means open your computer case and dive into it.
If you don't want to do that,another option is to reinstall windows as well as ubuntu,so you're starting from scratch.

Let me know if you want do this and which way you prefere in that case.

---

