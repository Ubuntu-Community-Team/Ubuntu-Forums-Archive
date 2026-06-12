---
title: "write to NTFS partition"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by moomintroll on 2007-03-20
Hi - I have looked at all the forums but cant solve this problem - I cant write to my NTFS partition - 

Here's an excerpt from my /etc/fstab -

# /dev/hdb1                             
UUID=667480A074807519 /media/hdb1     ntfs    defaults,nls=utf8,umask=0222,gid=46 0       1

I have installed ntfs-g but when I run it only sees hda1

Also I tried to get updates for this from Automatix but couldn't - is the site down?

I cant change write access to hdb1 as root is the owner.  If I try to  sudo mount -a I get "mount: No medium found"
 Also My fstab  doesnt seem to see my hda0 which is my windows partition (C Drive)

I think I've probably f*cked up too many things in Edgy (Ultimate 1.2) and may have to blow it away and go for dapper

Any help most appreciated!!!

---

### Post by raja on 2007-03-20
Try this. 
Make a backup of your current fstab.
```
cp /etc/fstab /etc/fstab_bkp
```
Now, change the line for /dev/hdb1 like this 
```
UUID=667480A074807519   /media/hdb1   ntfs-3g defaults,locale=en_US.utf8   0    0
```

Now remount the drive
```
sudo umount /dev/hdb1
sudo mount -a
```

Remember that you should have the mount point already, else
```
mkdir /media/hdb1
```first.
Hope that helps !

---

### Post by moomintroll on 2007-03-21
thanks - i'll try it tonight !!

---

### Post by moomintroll on 2007-03-21
Tried that but unfortunately all that happened was my hdb1 disappeared so I reinstated the back up.  
If I do a sudo mount -a it comes back with mount: No medium found

root is the owner in the group plugdev and Others folder access is access files.  Its almost like the fstab is right (albeit not showing my hda0 C partition) and something else is up.  

By the way I can mount usb drives and cameras OK

If I dont get this working my girlfriend will make me use windows!!

Please see my fstab for what its worth - also notice - no hda0 (XP Partition C)  which by the way I can only boot into if I boot into Ubuntu and then restart in to XP - bizarre

All help very much appreciated.

---

### Post by Adramelech on 2007-03-21
you need to use ntfs-3g to mount your harddrive i supposed "ntfs-g" is a typo en your post and you already installed ntfs-3g.

My entry on fstab is:
UUID=3FF4EEB0113B9DD4 /media/hda2     ntfs-3g    defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0

and added my user to the group ntfs-3g. instead of unmounting and mounting again, try rebooting the pc.

---

### Post by moomintroll on 2007-03-21
If I edit 

fstab with UUID=3FF4EEB0113B9DD4 /media/hdb1 ntfs-3g defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0

I lose the mount totally - nothing there whatsoever - I also tried to add username to group ntfs-3g but this does not exist - so I have rolled back so I can see and read the drive but not write.

Hmmmm????

---

### Post by Adramelech on 2007-03-21
create the group and then add the user
System->Administration->Users and groups

did you restarted the computer after changing the fstab?

---

### Post by moomintroll on 2007-03-21
Urrr - adding groups doesn't seem to be working either - I just added ntfs-3g and applied it to users but the group does not appear in the list - or any other groups.

In the past I have added users to groups via terminal which seems to work fine.  This issue may stem from the fact I had to delete the first account when I set up 6.10 originally.  I had to delete it as I was refused access to it after trying to change some desktop themes settings.  So created a new user with admin privileges

can of worms?

downward spiral?

Reinstall - hope not!

Thanks again

P.S - I did reboot

ALso when I tried to mount -a I got a message back - mount: No medium found

---

### Post by raja on 2007-03-21
> **moomintroll said:**
> If I edit 

fstab with UUID=3FF4EEB0113B9DD4 /media/hdb1 ntfs-3g defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0

I lose the mount totally - nothing there whatsoever - I also tried to add username to group ntfs-3g but this does not exist - so I have rolled back so I can see and read the drive but not write.

Hmmmm????

The UUID must be the same as it was originally since that is the UUID assigned for your partition. So it should be UUID=667480A074807519. Also the mount point must exist beforehand. So you should have /media/hdb1 (or whatever else you want to call it) before you try to mount it. It will appear empty before you mount the drive and should get populated once it is mounted.

---

### Post by moomintroll on 2007-03-22
At work at the mo but I'll try it tonight

---

### Post by moomintroll on 2007-03-22
Evening - 

I've added UUID=667480A074807519 /media/hdb1     ntfs-3g defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0

as per previous suggestion and tried to add users to ntfs-3g group but this caused drives not to be readable (unmounted completely) so I have rolled back to my previous hdb1 fstab entry where i can at least read the drive.

If I try to add users to the ntfs-3g group I get this

sudo adduser jbloggs ntfs-3g
adduser: The group `ntfs-3g' does not exist.

If I try to mount the drive I get this - 

sudo mount -a
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.
mount: No medium found
mount: No medium found

As I mentioned earlier is it possible that because the system/administration/users and groups is empty that this is in some way screwed.  I dont seem to be able to add groups via the GUI.  How do I add groups via terminal - maybe this will go some way to solve this issue -

 what you reckon?

Thanks again

---

### Post by moomintroll on 2007-03-22
Evening - 

I've added UUID=667480A074807519 /media/hdb1     ntfs-3g defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0

as per previous suggestion and tried to add users to ntfs-3g group but this caused drives not to be readable (unmounted completely) so I have rolled back to my previous hdb1 fstab entry where i can at least read the drive.

If I try to add users to the ntfs-3g group I get this

sudo adduser jbloggs ntfs-3g
adduser: The group `ntfs-3g' does not exist.

If I try to mount the drive I get this - 

sudo mount -a
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.
mount: No medium found
mount: No medium found

As I mentioned earlier is it possible that because the system/administration/users and groups is empty that this is in some way screwed.  I dont seem to be able to add groups via the GUI.  How do I add groups via terminal - maybe this will go some way to solve this issue -

 what you reckon?

Thanks again

---

### Post by raja on 2007-03-22
Looking at some related threads, it looks to me that the problem is that the drive was not cleanly unmounted in windows. Can you try this
```
ntfsfix /dev/hdb1
ntfs-3g /dev/hdb1/ /media/hdb1 -o force
```
The other option is to boot into windows and shut down once.

---

### Post by moomintroll on 2007-03-23
I think we might be getting somewhere - ntfs-g must be working ok coz i have managed to mount my hda1 windows partition as read and read write without problem.

TRhe commands from the previous post returned the follwing -  

ntfsfix /dev/hdb1
Refusing to operate on read-write mounted device /dev/hdb1.

sudo ntfs-3g /dev/hdb1/ /media/hdb1 -o force
Failed to access '/dev/hdb1/': Not a directory

---

### Post by raja on 2007-03-23
> **moomintroll said:**
> 

TRhe commands from the previous post returned the follwing -  

ntfsfix /dev/hdb1
Refusing to operate on read-write mounted device /dev/hdb1.

Is your disk already mounted then ? Check with ```
mount
```
> 
sudo ntfs-3g /dev/hdb1/ /media/hdb1 -o force
Failed to access '/dev/hdb1/': Not a directory
Sorry. That should be 
```
sudo ntfs 3g /dev/hdb1 /media/hdb1 -o force
```

---

### Post by moomintroll on 2007-03-24
Raja

Here is the output from the commands you suggested

$ mount

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=0222,gid=46)
/dev/hda1 on /media/C type fuse (rw,nosuid,nodev,noatime,allow_other)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

$ sudo ntfs 3g /dev/hdb1 /media/hdb1 -o force

sudo: ntfs: command not found
crooky@Moomin:~$ ntfs
ntfs-3g       ntfscluster   ntfsfix       ntfsls        ntfsundelete
ntfscat       ntfs-config   ntfsinfo      ntfsmount     
ntfsclone     ntfscp        ntfslabel     ntfsresize    

$ sudo ntfs-3g /dev/hdb1 /media/hdb1 -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/hdb1 (Data)
crooky@Moomin:~$ mount -a
mount: only root can do that
crooky@Moomin:~$ sudo mount -a
mount: No medium found
mount: No medium found

Once again thanks for your suggestions

---

### Post by ComplexNumber on 2007-03-24
**moomintroll**
i haven't read through the whole thread, but i suggest that to get write access to ntfs, you need the following components:
a) the ntfs-3g packages. have a look for other ntfs packages as well in synaptic
b) [this]("http://gnomefiles.org/app.php/ntfs-config"). go to the home page, and you will find debs for fiesty and edgy. to install them, you can either double click on them or fire up the terminal and goto where the deb package is. then type in the following:
**sudo dpkg -i <name-of-package>**

i usually just type in sudo dpkg -i *.deb to save on writing. note that it accepts wildcards.

then run the ntfs-config application from the terminal (if it doesn't appear in the menu).


the above is what i did to get write access.

---

### Post by moomintroll on 2007-03-24
I'll give it a go but I've kind of proved that ntfs-3g is working ok coz i can mount r/rw my windows c partition hda1)

Ta

---

### Post by ComplexNumber on 2007-03-24
> **moomintroll said:**
> I'll give it a go but I've kind of proved that ntfs-3g is working ok coz i can mount r/rw my windows c partition hda1)

Ta
i installed all the ntfs stuff(eg ntfs-3g, gnome-vfs-ntfs, etc), but i still didn't have write access. the package above was the final element that gave me write access.

---

### Post by raja on 2007-03-24
You can see in the mount that hdb1 is mounted as ntfs. You should atleast be able to read the files from there. Now if you want to try the ntfs mount, you should first unmount it ```
sudo umount /dev/hdb1 
``` and then try the ntfs-3g force mount as before.

---

### Post by moomintroll on 2007-03-24
Can no longer read or write to hdb1 after installing ntfs-config - here is my auto generated fstab file - 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=1b1ff971-080b-4e33-b1af-429181be0846 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda3 :
UUID=7db7597f-fb6b-4f81-b840-7ca0bed7951b none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,auto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,auto 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/Data ntfs-3g defaults,locale=en_US.UTF-8 0 0

any ideas??

Thanks

---

### Post by raja on 2007-03-24
So is the partition not mounted at /media/Data ?
Whats the output of mount ?

---

### Post by moomintroll on 2007-03-24
This is the output from mount.  I have a folder in media called hdb1 and the original folder called data

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /media/hda1 type fuse (rw,nosuid,nodev,noatime,allow_other)

Thanks again

---

### Post by raja on 2007-03-24
OK. Now that /dev/hdb1 is definitely not mounted, can you try ```
ntfsfix /dev/hdb1
``` and see if it cleans it up?

---

### Post by ComplexNumber on 2007-03-24
> **moomintroll said:**
> Can no longer read or write to hdb1 after installing ntfs-config - here is my auto generated fstab file - 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=1b1ff971-080b-4e33-b1af-429181be0846 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda3 :
UUID=7db7597f-fb6b-4f81-b840-7ca0bed7951b none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,auto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,auto 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/Data ntfs-3g defaults,locale=en_US.UTF-8 0 0

any ideas??

Thanks
but did you run it after installing it? when you run, you should get a screen like the following. jsut tick the one selected and press ok. the 2nd screenshot shows my windows partition where you can clearly see that options to 'create folder' are clearly not greyed out.the following is my entry for hda1:
```
# Entry for /dev/hda1 :
UUID=6010B50710B4E566 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
```



why have you got 2 entries for your windows partition?

---

### Post by moomintroll on 2007-03-24
As far as I can tell I've got HDA partitioned for Ubuntu, XP and a SWAP which gives me HDA1,2,3

and I've got HDB1 which is a 120GB NTFS drive

I did do the ntfs-config GUI mount but it said something about doing a force mount or boot into windows twice???

This is the screenshot from my ntfs-config  attached.  My HDA1 XP partition was auto discoverer and is r/rw??

Cheers

---

### Post by moomintroll on 2007-03-24
Also, I tried this 

 ntfsfix /dev/hdb1
Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

My MTAB looks like this

/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda1 /media/hda1 fuse rw,nosuid,nodev,noatime,allow_other 0 0


Thanks again

---

### Post by raja on 2007-03-24
The problem clearly is that the partition is not 'clean'. Did you try booting into windows, run a scandisk on the partition and then shutdown cleanly ?

---

### Post by moomintroll on 2007-03-24
Booted in to xp  boot cd - ran chkdsk, booted in to windows and restarted in to edgy.

All is now working and I can read / write to HDA1 abd HDB1 without problem.

Many many thanks for all Raja and ComplexNumber's  help and advice

Another nail in the coffin for XP - hoorah

---

### Post by raja on 2007-03-24
Thats fantastic !

---

