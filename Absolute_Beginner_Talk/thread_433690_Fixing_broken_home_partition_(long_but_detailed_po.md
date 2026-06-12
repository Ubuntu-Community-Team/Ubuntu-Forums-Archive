---
title: "Fixing broken /home partition (long but detailed post)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-05-05
When replying, if you quote the message, feel free to "trim" the message down to just the questions near the end to make it easy to find the answer(s) for myself and others. 

I hope someone can help here. I followed the directions posted elsewhere here and created a separate partition for my /home directory so, in case of a disaster like yesterday, I could reinstall Ubuntu (or perhaps another "flavor" of Linux) and have many of the things I installed previously all there, ready to use. It worked like a charm until I had to reinstall Feisty due to my inexperience and trying out a "fixed" kernel someone posted (that worked for others) to get rid of the USB_SUSPEND problem. Here is the link I used to create the /home partition. :

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

***I don't want to install or set up anything until I get this working again the way it was before. So I'll be limping along with Windows on a laptop or the very basic Ubuntu setup on my desktop until I get this back in proper order***. 

I did something wrong. I did not use the cp command after reinstalling Ubuntu to prevent copying over the files in my /home partition with new ones. I didn't know if it would delete things already there or not.

However, I did use the following commands:

[B]# mkdir /mnt/home
# mount -t ext3 /dev/hda7 /mnt/home [/B]
there's no home directory
then skipped the cp command, edited /etc/fstab with Pico to add:

***/dev/hda7 /home ext3 defaults,errors=remount-ro 0 1***

then I used these commands again from the article linked above:

[B]# mv /home /homeOLD
# mkdir /home
# umount /mnt/home
# mount -a
[/B]
I didn't get to the part of deleting the /homeOLD directory.

Now, here's what I have on /dev/hda7

[B]/donald
/homeOLD
/lost+found
/melissa[/B]  (doesn't have much in there, she logs in as me)

I doubt that this matters, but some information that might be sueful:

[B][I]/dev/hda5 is swap
/dev/hda6 is /
/dev/hda7 is supposed to be my /home folder on a separate partition[/I][/B]

These four folders are at the "top" of the hierarchy on this partition. I believe that there should be a /home folder only at the top and the other three should be below that. 

there is no /home directory on /dev/hda7, where it "should" be if I did things right. 

***The good news is that, when I set Thundar file manager/browser to show hidden files, everything I expect is under /donald, even my wine installation and all of the desktop files Firefox downloaded that I will clean up later. ***

The /homeOLD on /dev/hda7 has the default stuff on it from the new installation.

When I try to "create" a /home directory on /dev/hda7, I get an error message:

[B]root@donald:~# mkdir /dev/hda7 /mnt/home
mkdir: cannot create directory `/dev/hda7': File exists[/B]


***I need to know these things and maybe some other information as you see fit to share):***

1.) When installing Ubuntu again, I noticed in the manual partition configuration an option to set /dev/hda7 to a /home directory. I did not choose that, thinking that it would be reformatted and the default stuff put in there, leaving me with none of the applications in there from before. Could I have made it simpler by allowing the partitioning part of the install program make /dev/hda7 my /home partition and directory, or am I correct in thinking that this would overwrite my files already there?

2.) If there is a next time for a reinstall, how do I go about setting up /dev/hda7 as my /home directory when it already was set up before to do so? Unless I missed something in the article, it only covered setting the partition up the first time, not at a later time to re-join it with the main OS. 

3.) How do I fix the problem that I have now? 

4. Will my Pixus printer driver come back when the /home partition is working proprly again, or do I need to find the information again to install it to support my Canon i850 printer?

I'm sure I won't get everything back by getting this fixed, but I can handle the rest. I have important bookmarks in Firefox and I use a Windows email program running under wine that my wife insists on using if I'm going to use Linux  (and I like it, too, since I've been using it for a decade or more). My "Ubuntu Guru" is not available right now for help and I'd like to not only fix the problem, but also to know what's going on behind the scenes. 

Thanks ahead of time!!!

Donald

---

### Post by gangrelsurf on 2007-05-05
I think you've got it.

There shouldn't be a /home directory on /dev/hda7.  the /home is on your root partition, /dev/hda6.  It sounds like you have the /dev/hda7 mounted there.  All your stuff is present when you log in, right?

---

### Post by chili555 on 2007-05-05
I dont believe I quite agree with my colleague gangrelsurf. It is not only perfectly possible but quite common to have a /home on a partition other than your root partition. As an example, here is mine:```
chili@LAPTOP60:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               16G   3.5G    12G  23% /
varrun                 1.1G    99k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
procbususb              11M   123k    11M   2% /proc/bus/usb
udev                    11M   123k    11M   2% /dev
devshm                 1.1G    17k   1.1G   1% /dev/shm
lrm                    1.1G    19M   1.1G   2% /lib/modules/2.6.17-11-generic/volatile
/dev/sda3               79G   5.5G    70G   8% /home
```As you can see, my /home is on sda3 and / is on sda1.

Your /home is there. However you renamed it /homeOLD, but it's there.```
mv /home /homeOLD
```

I think to fix the problem you have now, you simply:```
mv /homeOLD /home
```

---

### Post by gangrelsurf on 2007-05-05
> It is not only perfectly possible but quite common to have a /home on a partition other than your root partition

Of course.  But what t2000kw seems to be trying to do, and what you have from your df run, and what is very common, is to have the /home directory, the mount point, on your root, then mount the drive/partition for home to that mount point, just like you have, and just like he has, from his /etc/fstab
```
/dev/sda3               79G   5.5G    70G   8% /home
``` chile555
```
/dev/hda7 /home ext3 defaults,errors=remount-ro 0 1
``` t2000kw

and just as I've had on several boxes, though not my current.  You can mount anything you want any where you want.  At work I have a directory called /var/www, as do most people running apache, on which I mount a separate drive for my webroot.  Same concept


(chili555, I'm sure you know all of this, but I think t200kw is misundestanding the file system and I'm just using you as an example)

> As you can see, my /home is on sda3 and / is on sda1.
there is a home partition (/dev/sda3) and a home directory (/home)

 / is on sda1, /home, the directory is on /.  If you unmount your /dev/sda3 (from single user), you'll still have a directory called /home, it'll just be empty because the disk isn't mounted

/dev/sda3 is mounted to /home.  When the disk is mounted, it is like a branch stuck into the directory structure at the mount point /home


t2000kw seems to be trying to make a home directory, a directory called home, as /dev/hda7/home.  

> When I try to "create" a /home directory on /dev/hda7, I get an error message:

root@donald:~# mkdir /dev/hda7 /mnt/home
mkdir: cannot create directory `/dev/hda7': File exists

chile555 - would you agree that he is misunderstanding the file structure?

t2000kw - you say that when you view hidden files your (hidden) stuff is there.  So is there stuff that is not there?  If so, just (with your new home partition mounted at /home), cp -fr /oldHome/* /home/

---

### Post by gangrelsurf on 2007-05-05
please run this and post the output so we can see what you actually have:

```
mount
```

---

### Post by t2000kw on 2007-05-05
> **gangrelsurf said:**
> I think you've got it.

There shouldn't be a /home directory on /dev/hda7.  the /home is on your root partition, /dev/hda6.  It sounds like you have the /dev/hda7 mounted there.  All your stuff is present when you log in, right?

No, it's not, and that's the problem.

---

### Post by gangrelsurf on 2007-05-05
Ok, just trying to get clear on what your situation is.  Can you please post the out put of:
```
mount
```

---

### Post by t2000kw on 2007-05-05
> **gangrelsurf said:**
> t2000kw - you say that when you view hidden files your (hidden) stuff is there.  So is there stuff that is not there?  If so, just (with your new home partition mounted at /home), cp -fr /oldHome/* /home/

I don't see anything missing. 

When I try the command above, I get an error message:

[B]root@donald:~# cp -fr /homeOLD/* /home/
cp: cannot stat `/homeOLD/*': No such file or directory[/B]

I tried it with /dev/hda7 in front of it also:
[B]
root@donald:~# cp -fr /dev/hda7/homeOLD/* /home/
cp: cannot stat `/dev/hda7/homeOLD/*': Not a directory[/B]

Not sure what I'm doing wrong. It sounds simple enough.

---

### Post by t2000kw on 2007-05-05
> **gangrelsurf said:**
> Ok, just trying to get clear on what your situation is.  Can you please post the out put of:
```
mount
```

Here it is:

[B]root@donald:~# mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda2 on /media/hda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda7 on /media/hda7 type ext3 (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)[/B]

Ignore anything on hda2--it's a Windows drive, at least for now, and one partition on hda1, (partition 1) is an old Windows partition.

---

### Post by t2000kw on 2007-05-05
I think (not sure) what I need is a directory (folder) on hda7 that is /home and have everything else that is there now (except for the /homeOLD folder) under it.

---

### Post by gangrelsurf on 2007-05-05
ok, the thing is not mounted on home:
```
/dev/hda7 on /media/hda7 type ext3 (rw)
```

can you post your /etc/fstab please?

---

### Post by t2000kw on 2007-05-05
> **gangrelsurf said:**
> ok, the thing is not mounted on home:
```
/dev/hda7 on /media/hda7 type ext3 (rw)
```

can you post your /etc/fstab please?

Here it is . . .

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=bfd03742-82c2-4811-9e49-1ed787bc71d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A8D7-2879  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=3F3B-94E9  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /media/hda7     ext3    defaults        0       2
# /dev/hdb1
UUID=D8084B7B084B57A0 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=fc342dc3-a525-4d52-a5c7-9396205fb703 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5 /home ext3 defaults,errors=remount-ro 0 1

---

### Post by gangrelsurf on 2007-05-05
you mentioned pico, so I assume that is your editor of choice, but if you want a gui try gedit, 

```
sudo pico
```
or
```
sudo gedit
```

change the line in /etc/fstab that reads:
```
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /media/hda7 ext3 defaults 0 2
```
to
```
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /home ext3 defaults 0 2
```

let me know when you have that

---

### Post by t2000kw on 2007-05-05
I did that. And, I noticed a mistake on the last line. I'm pointing to hda5, my swap partition. I changed it to hda7 but then it won't boot. So I put it back the way it was, made only the suggested change, and then rebooted. I then get a text-mode login screen. I do a control-alt-delete and then I get to the Ubuntu screen. I prefer to boot directly to the Ubuntu screen like before, and I must have did something to mess this up.

I can, if need be, reinstall Feisty and start from a clean install again. 

Anyway, the /etc/fstab file is as you suggested so far. 

> **gangrelsurf said:**
> you mentioned pico, so I assume that is your editor of choice, but if you want a gui try gedit, 

```
sudo pico
```
or
```
sudo gedit
```

change the line in /etc/fstab that reads:
```
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /media/hda7 ext3 defaults 0 2
```
to
```
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /home ext3 defaults 0 2
```

let me know when you have that

---

### Post by gangrelsurf on 2007-05-05
so you've already done a reboot?  I was going to suggest checking a few things before that , but...

run ```
mount 
```again

lets see if hda7 is where it's supposed to be

---

### Post by t2000kw on 2007-05-05
> **gangrelsurf said:**
> so you've already done a reboot?  I was going to suggest checking a few things before that , but...

run ```
mount 
```again

lets see if hda7 is where it's supposed to be

do you want a mount command?

or a copy of fstab as it is now?

I'll post both below . . .

mount shows:

donald@donald:~$ mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=bfd03742-82c2-4811-9e49-1ed787bc71d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A8D7-2879  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=3F3B-94E9  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=88db85eb-b5d0-4712-8894-8b0e7f571263 /home ext3 defaults 0 2
# /dev/hdb1
UUID=D8084B7B084B57A0 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=fc342dc3-a525-4d52-a5c7-9396205fb703 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5 /home ext3 defaults,errors=remount-ro 0 1

---

### Post by gangrelsurf on 2007-05-05
Ok.  It's not mounted.  

reboot the box, and when you get to the grub menu (you may have to press esc to get there), boot into single user mode.  I think it's called 'restore' or 'restricted'.  It just means your logging in as root on a minimalist system.

When you get there,  do 
```
mount
```
and see if /dev/hda7 is listed as mounted.
if not, run
```
mount -a
```
and then ```
mount
``` to check again
if it's still not mounted, and this is a fresh install, and you don't feel like messing with this any more, then, yeah, a reinstall might not be a bad idea, but lets not give up yet.

Let me know what you get from that

---

### Post by gangrelsurf on 2007-05-05
wow, I just re-read that fstab.  I missed what you were saying about the last line before.  Go ahead and comment that out, so it's.
```
# dev/hda5 /home ext3 defaults,errors=remount-ro 0 1

```
as is you have /dev/hda5 as both swap and home.  I don't know <em>what</em> that would do.

---

### Post by t2000kw on 2007-05-05
Nothing on hda7 shoed with the first mount. THen mount -a and another mount showed:

/dev/hda7 on /home type 3 exts (rw)

I then rebooted and was taken to a text mode login. Above the propt was this informatiohn, which may or may ot be helpful:

/dev/hda7: clean, 38,368/4905600 files, 612746/19809686 blocks

fsck died with exit status 8

file system check failed

log in /var/log/fsck/checkfs

that log shows this:

Log of fsck -C -R -A -a 
Sat May  5 12:36:55 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 49884 files, 363035/373417 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda2: 11 files, 998537/1390917 clusters
/dev/hda5 is mounted.  e2fsck: Cannot continue, aborting.


/dev/hda7: clean, 38368/4905600 files, 612746/9809682 blocks
fsck died with exit status 8

Sat May  5 12:37:09 2007
----------------

Now, if this looks like a dead end or too many variables are present to figure this out easily, let me know if I should reinstall Feisty with the / partition on hda6 and swap on hda5 with hda7 (what will be home again, I hope) untouched. 

If it looks like it can still be fixed, I'll leave it alone for now.

---

### Post by t2000kw on 2007-05-05
I'll check back around 2 PM EDT--have some errands to do. Maybe sooner than that, but just letting you know since you're being so helpful that I am paying attention and trying to make this work.  I do appreciate your help so far.

---

### Post by gangrelsurf on 2007-05-05
Yeah, it can be fixed.  But the plot is thickening here.  Glad I can help.

From your fsck output it looks like you have two conflicts:
1. your /etc/fstab is saying to mount /dev/hda5 as both swap and as an ext3 partition
2. your /etc/fstab is saying to mount both /dev/hda5 and /dev/hda7 at /home

comment out that last line in /etc/fstab, the one with /dev/hda5 as /home

then the question becomes, what is /dev/hda5 really formated as?  You have one line in your /etc/fstab looking for it as a swap, then that last line is looking for it to be a ext3.  I think that it might be a ext3 since that's what fsck thought it was, though that might have been because it looked in /etc/fstab.  I don't know where fsck gets its information from.

to find out what it really is run:
sudo cfdisk /dev/hda

this will come up with a table.  What is the 'FS Type' of /dev/hda5?

if it is listed as swap, cool.  With the conflicting final line commented out, Try a reboot.  Chances are that it will do an fsck during boot, or try to.  Watch that for any error messages.  If it goes through like that, run 'mount' and see if /dev/hda7 is mounted on /home

or

If it is listed as raw or unformatted, follow step one below to make it a swap, then reboot as above.

or

if it is listed as ext3, ext2, or anything besides swap, raw or unformated, there are a few options
1. If you are absolutely 100% positive that there is nothing of value on that partition, you can change the type through cfdisk.  Just tab over to the [type], press enter, and enter 82 for '82 linux swap / solaris', then enter, tab over to  [write], confirm and do it
2. If you are less than 100% sure of what's on the partition, you can check like this:[LIST=1]
[*]exit cfdisk
[*]open an editor for /etc/fstab as root (sudo or what ever you've been doing)
[*]Comment out the line 'UUID=fc342dc3-a525-4d52-a5c7-9396205fb703 none swap sw 0 0'
[*]So now both lines for /dev/hda5 are commented out
[*]copy the last line of your /etc/fstab and paste it at the end, then uncomment your new copy of the last line
[*]change it to read: /dev/hda5 /mnt/test ext3 defaults 0 1 (or if the type from cfdisk wasn't ext3, make it what ever it was)
[*]save and exit
[*]sudo mkdir /mnt/test
[*]sudo mount /mnt/test
[*]ls -a /mnt/test and see what you've got
[*]if it is all trash, or just empty, you'll probably want to make it a swap as in option 1, above.  Or is it fairly big, as in over a gig or so?  You can check by running cfdisk again.  If it's big enough that you might want to use it for something other than swap, or if it has stuff you want, let me know.  We'll figure out what to do with it.
[/LIST]
3. You have been booting without a swap partition any way, so at least for now to get the /home mounting right, you can just comment out the other /dev/hda5 (the line that starts with UUID...), and set up a swap properly later.


I've got a thing to go to at 4:00.  If I don't hear from you before then, I'll jump on here tomorrow and check this thread.

---

### Post by gangrelsurf on 2007-05-05
as far as the reinstall option - as long as you aren't telling the partition manager to format /dev/hda7 you should be fine.  Triple check that you aren't telling it to do that.

---

### Post by t2000kw on 2007-05-05
I'm in a catch-22 situation. When I commented out the last line and reboot, I can get to the Gnome login but then it goes to a white screen--no GUI after that. I can exit with control-alt-F1 to text mode, which I did, and I un-commented out the improper last line to let me boot to the Gnome GUI. So I'm back where I started.

I'm posting the cfdisk output below. Since I can't run wihtout the last line but it's not right with it, would this be a good time to reinstall?

I'm not hot to reinstall, I'm just wondering if it will give us a known starting point and make it simpler to figure out???

/hda5 is reported to be a swap file, which is what it should be: 

                                  cfdisk 2.12r

                              Disk Drive: /dev/hda
                        Size: 80060424192 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9733

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   W95 FAT32 (LBA)                  12239.22 
    hda5        NC          Logical   Linux swap / Solaris               855.43
    hda6                    Logical   Linux ext3                       21073.17
    hda7                    Logical   Linux ext3                       40180.50
    hda2                    Primary   Hidden W95 FAT32 (LBA)            5708.35







     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

---

### Post by t2000kw on 2007-05-05
It might be a good idea if you think it will take past 4 pm to get this fixed (with back and forth messages here) to tell me what to do after a clean install on hda6 for / and hda5 for swap if the next step doesn't fix it. 

I'm just glad that I can see the information is still there--just some problems with folder names and mounting.

---

### Post by gangrelsurf on 2007-05-05
hold off on that re - install

lets try this...

back up your /etc/fstab with sudo cp /etc/fstab /etc/fstab.bu
delete your current fstab with sudo rm /etc/fstab
(don't worry, if this fails you can still boot into single user and restore from the back up)
make a new /etc/fstab like this:

```

proc /proc proc defaults 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1  /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda2 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda5  none swap sw 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda7 /home ext3 defaults 0 2
/dev/hdb1 /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

```

---

### Post by gangrelsurf on 2007-05-05
As far as a reinstall option, if you go with that, when you get to the partition editor part tell it you want to manually edit the partition table, then mount /dev/hda5 as swap, /dev/hda6 on root (and format it), and /dev/hda7 on /home (and do not format it).  After you tell it to go ahead, there will be a conformation screen.  Look it over good and make sure it's what you want before confirming.

---

### Post by t2000kw on 2007-05-05
too late--I thought y ou had left for your function, which you surely willhave by now. I did the reinstall. Sorry about that. I did not mark the /dev/hda7 as home thinking it would overwrite those files.

I'll try again and see what happens. if the confirmation screen says it will format hda7 I will cancel out of it and go back to this fresh installation.

Don

---

### Post by t2000kw on 2007-05-05
Update--reinstalled Feisty with /hda7 marked for /home patition. 

Boot to Gnome login, then goes to white screen.

Tried another reinstallation. Copied everything under my folder /donald from the old /home partition to the default /home folder with the new installation on the / partition. 

Guess what? White screen again. Something is corrupted, it seems.

For now, I reinstalled wine, copied my Windows email program, Agent, in its folder, to where it would be after I installed it again on the /home partition under wine. Reinstalled Agent and all the email was there. The only thing I lost was lots of Linux bookmarks, but I'm sure I can find them again. 

I was hoping to find the bookmarks from Firefox on the other drive and put them in Firefox again. I tried copying the /firefox and other directlries under the /mozilla folder on the /home partition to where Firefox is on the default installation and it didn't work. 

I'll post this as a separate, unrelated question elsewhere, but if I can't get the old /home partition to work, I can always reinstall things as I need them. 

I was mostly concerned about the email messages being lost by not being able to get to them again, though they were there.

---

