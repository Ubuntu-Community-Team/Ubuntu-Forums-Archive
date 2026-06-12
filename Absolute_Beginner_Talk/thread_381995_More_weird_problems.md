---
title: "More weird problems"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by wasteoftime on 2007-03-11
Hi guys back with more stuff i cant figure out!

The first one is that when i boot up my laptop and am asked by grub which operating system to boot i get two sets of ubuntu options. Ive booted into both and they both work all with the same passwords. Whats going on?!? I know I didnt install it twice with the same passwords!:confused: 

The second problem is that when i did install ubuntu i created a smallsih boot partition and an extended partition which i cant access windows can see it in disc management but ive tried everything i know in lnux to find it but am stuck! Please help.:( 

The third one is more of an annoyance than problem. Ive got an external harddrive that is picked up by ubuntu straight away. When i unmount it i can still remount it using the gui file browser. My problem is i cant do it in cli i cant even find it though i can see it in the gui. Only when i remount it using the gui does it appear in:  

" /media" 

Can someone explain why please:confused:  

Thanks in advance :)

---

### Post by lloyd_b on 2007-03-12
> The first one is that when i boot up my laptop and am asked by grub which operating system to boot i get two sets of ubuntu options. Ive booted into both and they both work all with the same passwords. Whats going on?!? I know I didnt install it twice with the same passwords! 

Look at the grub menu carefully, and you'll probably note that it references two different kernel versions (such as "2.6.17-10" and "2.6.17-11").  What's going on here is that at some point the update program installed a newer kernel version, and by default when a new kernel version is installed, the old version is kept (in case you have problems booting from the new version).  

Both boot to the same disk partition (which is why you have the same passwords), they just start up with the different kernel versions.

You can go into Synaptic, and uninstall the older kernel version (since the newer version works properly for you), and those "extra" entries will disappear from Grub.
> 
The second problem is that when i did install ubuntu i created a smallsih boot partition and an extended partition which i cant access windows can see it in disc management but ive tried everything i know in lnux to find it but am stuck! Please help.

The third one is more of an annoyance than problem. Ive got an external harddrive that is picked up by ubuntu straight away. When i unmount it i can still remount it using the gui file browser. My problem is i cant do it in cli i cant even find it though i can see it in the gui. Only when i remount it using the gui does it appear in:

" /media"

Can someone explain why please

Could you post the contents of the file "/etc/fstab"?  That file controls what's mounted and where it mounts (by default - if you use the "mount" command in the command line with the proper options you can mount things just about anywhere).  At any rate, seeing that may provide some clues as to your problems.

As far as the external drive mounting under "/media", that's the default unless another mount location is specified in "/etc/fstab".  By editing that file, you can change the default mount point.   Note: Changing the *wrong* thing in that file can leave you with an unbootable system!!!  Don't make any changes to that file unless you have a good idea as to what you're doing.

Lloyd B.

---

### Post by wasteoftime on 2007-03-12
Thanks llyod_b i didnt even look at the numbers on the kernal how stupid do i feel! Sorry but im still new wheres Synaptic?

Heres the print out from "/etc/fstab"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b415ea4b-46cd-4f5b-aa59-a783d67d337a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F604A71904A6DBBD /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=54101b3e-dd86-484f-b08c-f92cb1397eb0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Hope this makes sense to you?!?;)  I can see the sda3 but have no idea how to mount it since when i try i get a message saying:

" can't find sda3 in /etc/fstab or /etc/mtab"

I dont know if this helps either but when i try "mount /dev/sda3" i get back:

"mount: mount point none does not exist"

---

### Post by lloyd_b on 2007-03-13
> wheres Synaptic?

Look under "Administration" from the main menu (I think - I run Xubuntu rather than Ubuntu, and things are a little different).  Or you can type "sudo synaptic" from a terminal window.

> ```
# /dev/sda3
UUID=54101b3e-dd86-484f-b08c-f92cb1397eb0 none swap sw 0 0
```

Hope this makes sense to you?!? I can see the sda3 but have no idea how to mount it since when i try i get a message saying:

" can't find sda3 in /etc/fstab or /etc/mtab"

I dont know if this helps either but when i try "mount /dev/sda3" i get back:

"mount: mount point none does not exist"

"/dev/sda3" is your SWAP space (i.e. "virtual memory").  You shouldn't be able to mount this (it should be automatically enabled by the system when the machine boots).  To verify this:
```
swapon -s
```
And see if /dev/sda3 is in fact enabled as swap space.
 
So, in summary:
"/dev/sda1" : Windows, NTFS format, mounted at "/media/sda1"
"/dev/sda2" : Linux, ext3 format, mounted at "/"
"/dev/sda3" : Linux, swap, not mounted

So those three partitions are accounted for.  Is there another partition that you're trying to mount?

Lloyd B.

---

### Post by wasteoftime on 2007-03-13
I hope so.

My disk is about 60gb. When I partitioned my disc i already had windows on half of it, so i created a large partition for linux about 17gb then 3gb swap, what was left was 7-8gb. I created another partition, an extended one. I know its there because when im in windows i can see it in the "disk management" section in computer management as a logical drive of unknown format on the right side i of the swap (as you look at the graphic in disk management interface)

I cant find that "logical drive" in linux and i know its not seeing it all as one because if it was id be missing about 8gb, so i assume its not mounted. :confused: 

Now all this might be my fault as i might not have done something right when i partitioned it, but i dont know:( 

I hope all this makes sense and thanks for the reply:) 

I kind of wish i hadnt messed around in custom mode and let it partition itself!

---

### Post by lloyd_b on 2007-03-13
Okay, let's see if we can find that other partition.  Most likely it would be at "/dev/sda4", but it's better to verify things first.  Please run the following command in a terminal, and post the output from it:
```
sudo fdisk -l /dev/sda
```

Once we see that the partition exists (and what "/dev" entry references it), it's just a matter of adding an appropriate line in the "/etc/fstab" file to get it to mount.

Lloyd B.

---

### Post by wasteoftime on 2007-03-13
Heres the print out though i dont know why ive got what seems to be five partitions:confused: 

```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649        5943    18434587+  83  Linux
/dev/sda3            5944        6325     3068415   82  Linux swap / Solaris
/dev/sda4            6326        7296     7799557+   5  Extended
/dev/sda5            6326        7296     7799526   83  Linux

```

I got no idea.

---

### Post by wasteoftime on 2007-03-13
Another quick one on synaptic. I dont get what youre ment to do it opens the package manager which has alot of stuff in it. What am i ment to do when its open?

I dont suppose you know why "sudo" doesnt work and i have to "su" into root??

Sorry for being a pain:)

---

### Post by lloyd_b on 2007-03-13
> Heres the print out though i dont know why ive got what seems to be five partitions

I wouldn't worry too much about it - that "extended" partition is a result of some limitations in the way partition tables are stored on disk.

The important part thing is that we've found your other partition - "/dev/sda5" looks like a 7Gb linux partition, which is pretty much what you've described.

So let's get it mounted.

1. Create a directory to mount it on.  In a terminal window:
```
cd /media
sudo mkdir sda5
```

2. Manually mount the partition
```
sudo mount /dev/sda5 -t ext3 /media/sda5
```

At this point, the partition will be mounted under "/media/sda5".  

Now, if you want to simplify this procedure, you can add a line to your "/etc/fstab" file for that partition.  Note: you need superuser status to edit this file, so "gksudo gedit /etc/fstab":
```
/dev/sda5  /media/sda5  ext3  auto  defaults   0  2
```
Will cause this partition to be mounted at boot time, at "/media/sda5"

You can create a new directory most anywhere in the system and have that partition mounted on that directory - just create the directory, and change the "/media/sda5" to the directory you've chosen.

Note: there are places where you do NOT want to mount this.  Some of the directories on the system are actually virtual file systems in their own right, and directories that you create under them will not be there after the next boot.  Here's a list of those "special" directories:
/dev
/var/run
/proc
/sys

Lloyd B.

---

### Post by lloyd_b on 2007-03-13
> Another quick one on synaptic. I dont get what youre ment to do it opens the package manager which has alot of stuff in it. What am i ment to do when its open?
Looks like we're both online at the same time - you posted your last message while I was still composing mine:) 

I referred you to synaptic to get rid of that older kernel version.  What you're looking for are entries that start with "linux-image-...".  Right click on the older version (based on the version number), and select "Mark for removal".  Then click the "Apply" button towards the top of the screen.

Be certain that you leave at least one linux-image... installed.  Otherwise you'll have an unbootable system!

> I dont suppose you know why "sudo" doesnt work and i have to "su" into root??

Ouch - that one I can't answer.  Once you get your partitioning straightened out, you might try posting it under a new topic.

Lloyd B.

---

### Post by wasteoftime on 2007-03-13
Refuses to mount i get
```

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
           missing codepage or other error
           In some cases useful info is found in syslog - try 
           dmesg | tail or so

```

when i tried editing fstab anyway it said it was a bad line in fstab.

I sure this is my fault somewhere:) !!!!!!!!!!!!!

---

### Post by wasteoftime on 2007-03-13
The synaptic thing worked though it was scary restarting it to see if it would actually restart so thanks much appreciated:)

---

### Post by lloyd_b on 2007-03-13
> Refuses to mount i get
```
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
           missing codepage or other error
           In some cases useful info is found in syslog - try 
           dmesg | tail or so
```

when i tried editing fstab anyway it said it was a bad line in fstab.

Let's leave fstab alone for now - once we have the filesystem mountable, we can worry about that.

I wonder if that partition got formatted?  Since you don't have anything on it anyway, it won't hurt to format it again:
```
sudo mkfs -t ext3 /dev/sda5
```

If that appears to succeed, then
```
sudo mount -t ext3 /dev/sda5 /media/sda5
```

If either step appears to fail, please post the error(s).

Lloyd B.

---

### Post by wasteoftime on 2007-03-14
Followed all your instructions and i had no problems though i dont know if it worked. Heres what it did:

```
root@bob:~# mkfs -t ext3 /dev/sda5
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
975360 inodes, 1949881 blocks
97494 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2000683008
60 block groups
32768 blocks per group, 32768 fragments per group
16256 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@bob:~# mount -t ext3 /dev/sda5 /media/sda5
root@bob:~# 

```

I assume the formatting worked but not sure of the mounting since i didnt get a confirmation just a new prompt. And being a noob i dont know if its worked or not, is there a way to check?

Oh and thanks for being patient with me:)

---

### Post by wasteoftime on 2007-03-14
It wont mount i just found out. I know this as i checked the free space of the normal filesystem which was 14gb, when sda5 is apparently mounted it should have a different size but its still 14gb. I could be wrong as this is just a guess:confused: !!!!!

---

### Post by lloyd_b on 2007-03-14
> It wont mount i just found out. I know this as i checked the free space of the normal filesystem which was 14gb, when sda5 is apparently mounted it should have a different size but its still 14gb. I could be wrong as this is just a guess !!!!!

Could you run the command "df" (in a terminal window), and post the results?  "df" stands for "disk free" - it will show all mounted filesystems.

Mounting that file system will NOT change the size of the "normal" (root) filesystem.  Under "df", you should see a separate entry, referencing "/dev/sda5", with a mount point of "/media/sda5". 

Note: You'll also see several entries from "df" referring to the "special" filesystems I mentioned in a previous post: /dev, /proc, etc).

If the "mount" command didn't generate any errors, then I suspect that the formatting took, and that the filesystem mounted correctly.  The "df" output will confirm this.

Lloyd B.

---

### Post by wasteoftime on 2007-03-15
It works must have been mistaken yesterday sorry:---) :-# ill try an not open my mouth next time, so thanks again ive learned a lot from this! Heres the stuff you asked for:```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             18145120   2533412  14689980  15% /
varrun                  224716        80    224636   1% /var/run
varlock                 224716         0    224716   0% /var/lock
procbususb               10240       124     10116   2% /proc/bus/usb
udev                     10240       124     10116   2% /dev
devshm                  224716         0    224716   0% /dev/shm
lrm                     224716     17580    207136   8% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1             29302528  19199860  10102668  66% /media/sda1
/dev/sda5              7677052    148368   7138708   3% /media/sda5

```

Just need to know how to get it started at boot up now:)... then i can find out why "sudo"  doesnt work and why i have to "ifdown eth0" then "ifup eth0" everytime i connect to internet then find out oh well you get the picture!:D 

Thanks again.

---

### Post by lloyd_b on 2007-03-15
> Just need to know how to get it started at boot up now

To get it automatically mounted at boot, you need to add that line to the "/etc/fstab" file:
```
/dev/sda5  /media/sda5  ext3  auto  defaults   0  2
```

Then, after you reboot, run "df" and see if it mounted correctly.

Lloyd B.

---

### Post by wasteoftime on 2007-03-15
Its definately mounted as its now on my desktop with sda1 cant thank you enough for the help and the learning your a :KS 

Cheers mate.

You think i should post another thread about the sudo not working?

---

### Post by lloyd_b on 2007-03-15
> You think i should post another thread about the sudo not working?

First off, I would suggest searching the forums.  I did a quick search and turned up this thread.

[_[COLOR="Blue"]How To Recover From A Broken Sudo[/COLOR]_]("http://www.ubuntuforums.org/showthread.php?t=233502")

If a search turns up nothing that helps, *then* start a new thread.

Lloyd B.

---

### Post by wasteoftime on 2007-03-16
After looking at the one you suggested i think i know why its not working and its my fault, i really shouldn't play with stuff i don't understand but i know what i did so i can fix it thanks again im sure ill need help again some time soon:)

---

