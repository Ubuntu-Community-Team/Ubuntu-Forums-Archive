---
title: "Need to add space to exsisting ubuntu load"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by azbobs on 2008-03-11
Hello,

I followed some suggestions from the forum on a schematic for ubuntu layout. I ended up only using 1GB for root. I have loaded ubuntu on a external hard drive which did have some vista files and music etc loaded on it. I had split the drive is a 500 gb and used 170 gb for ubuntu. I now have removed the files to another drive and want to know if it would be better to remove ubuntu load I have currently loaded on 7.10. Or is there a way to expand my root from 1gb to let's say 100gb. I want to expand a few of the other directories. I just have this loaded as a dual boot and I am not using the grub loader instead using the bios to switch OS between 7.10 ubuntu and Vista ultimate. I am running this on a 64bit as well. Look forward to hearing back and really hate to reload the ubuntu. I just know that I will end up filling up root if I cannot grow the / root. I love ubuntu so far and have loaded a bunch of stuff so that is why I was hoping to find another way of growing the / instead of reloading. I had some people at work say that i could just put soft links to everything. I just don't think that would be the best way. So I am going to the experts here hoping for an answer.

TIA,
azbobs

Here's my layout

root@azbobs:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=42c27482-edf1-4935-b309-c04a08870664 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=aa48204b-d629-4cf1-86d1-e75a6a449dbb /home           ext3    defaults        0       2
# /dev/sda5
UUID=43a25ca3-1a2e-466e-9450-8481f1e96276 /usr            ext3    defaults        0       2
# /dev/sda7
UUID=b9f51edf-6044-40b7-a3ee-f2d0138978e8 /usr/local      ext3    defaults        0       2
# /dev/sda6
UUID=7ea8bc5e-e50f-4df5-b4f6-dae285d54483 /var            ext3    defaults        0       2
# /dev/sda8
UUID=ffc681ce-ffd5-416b-9a34-77cdaed37777 /var/log        ext3    defaults        0       2
# /dev/sda9
UUID=5b2ff8d8-67dc-4d23-94e4-6855ab0a3666 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
root@azbobs:~# fdisk -l
The program 'fdisk' can be found in the following packages:
 * gnu-fdisk
 * util-linux
Try: apt-get install <selected package>
-su: fdisk: command not found


---

### Post by cotcot on 2008-03-11
Have you tried the [[COLOR="Red"]Gparted LiveCD[/COLOR]]("http://gparted-livecd.tuxfamily.org/") ?

---

### Post by SloYerRoll on 2008-03-11
You can go through great pains to grow and shrink your volumes w/ gparted. But I consider things like this is for advanced user (I'm not one:)) I wasn't able to figure out how to expand any volumes w/o destroying the data on it. 
Your better off creating a large volume where you want Ubuntu to sit in and then just move all the contents in your 1GB file over to your 100GB volume. 

I'm not an expert by any means, but I have researched this for a few weeks looking for the same answer you are. This is what I did:
Created the new larger volume.
Moved root files to new volume and validated all files were moved. Then backed up those files for a second level of redundancy. 
Formated the small volume that wasn't big enough from the liveCD using gparted. 
Set up grub to point to the new volume (do your in BIOS, but it's the same thing). 
Verified everything was up and running. 
Removed file backup. 

No biggie if this breaks something. All you need to do is move your files back to your formatted 1GB volume. *This is why I validated all files were moved. 

Best,

---

### Post by Oldsoldier2003 on 2008-03-11
Actually if you just use the gparted live cd you can grow and shrink your partitions just fine and it wont effect your grub menu.list at all. of course be sure to back up any partitions you plan on changing in case something goes awry...

edit: one caveat.** Never ever use gparted to mess with your vista partition**, use the vista partitioning tool instead

---

### Post by Gepetto on 2008-03-11
You say you're also running Vista. This is actually a good thing, as the Vista partitioner can actually shrink volumes (it can also expand them too, but there are some caveats with the function). It's also quite easy too. At the disk management utility, just select the drive that you want to make smaller, and type in the usual information. Then, as cotcot suggested, pop in the Gparted LiveCD and use it to expand your root partition into the newly created free space. 

Make sure you back up all the important stuff before you partake on this journey too, it's always a good idea.

---

### Post by azbobs on 2008-03-11
I tried the gpart being seeing the entry about using the Vista disk management to grow the space. Below is the new entry, looks like I need to mount the new space. Will read up about doing so. Thx for the replys and will post back here after I get it mounted and transfer the files from root to the new space. 


root@azbobs:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# /dev/sda2
UUID=42c27482-edf1-4935-b309-c04a08870664 /               ext3    defaults,errors=remount-ro 0      [/COLOR] 1
# /dev/sda3
UUID=aa48204b-d629-4cf1-86d1-e75a6a449dbb /home           ext3    defaults        0       2
# /dev/sda5
UUID=43a25ca3-1a2e-466e-9450-8481f1e96276 /usr            ext3    defaults        0       2
# /dev/sda7
UUID=b9f51edf-6044-40b7-a3ee-f2d0138978e8 /usr/local      ext3    defaults        0       2
# /dev/sda6
UUID=7ea8bc5e-e50f-4df5-b4f6-dae285d54483 /var            ext3    defaults        0       2
# /dev/sda8
UUID=ffc681ce-ffd5-416b-9a34-77cdaed37777 /var/log        ext3    defaults        0       2
# /dev/sda9
UUID=5b2ff8d8-67dc-4d23-94e4-6855ab0a3666 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



root@azbobs:~# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc2               956628    199184    708848  22% /
varrun                 1031052        96   1030956   1% /var/run
varlock                1031052         0   1031052   0% /var/lock
udev                   1031052       128   1030924   1% /dev
devshm                 1031052         0   1031052   0% /dev/shm
lrm                    1031052     38324    992728   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc3            129768544    267804 122908872   1% /home
/dev/sdc5              9614116   2624200   6501544  29% /usr
/dev/sdc7              3842376     73380   3573808   3% /usr/local
/dev/sdc6             14421344    981808  12706976   8% /var
/dev/sdc8              6728280    155640   6230860   3% /var/log
/dev/scd0               710438    710438         0 100% /media/cdrom0
/dev/sdc1            314305020    371520 313933500   1% /media/New FreeAgent Drive


Cheers,
azbobs

---

### Post by azbobs on 2008-03-11
I made the drive active it the original root that did say active is now not. The drive that I used gpart on now says active. So I have a feeling that when I reboot it will not recognize the other drive that I use gpart on. I will post back in a while and let everyone know the outcome. Maybe because it's not mounted it will still reboot will find out in a minute. 
Cheers,
azbobs

---

### Post by azbobs on 2008-03-12
I did try to use Vista's Disk Management to extend the volume and is not giving that as an option only to shrink the volume. So I will try and copy everything from root to the new drive once I can find out how to mount the drive then I will try this. 

Any one know how to go about mounting this drive. Tried the following 

root@azbobs:~# mount -o noatime,remount,rw /dev/sdc2

Below is the error

# /dev/sda2
UUID=42c27482-edf1-4935-b309-c04a08870664 / ext3 defaults,errors=remount-ro 0 1

Cheers,
azbobs

---

### Post by Gepetto on 2008-03-12
Vista won't let you extend it, but it should let you be able to shrink your current vista partition. Then you can use Gparted to extend your current Linux root partition into that space.

---

