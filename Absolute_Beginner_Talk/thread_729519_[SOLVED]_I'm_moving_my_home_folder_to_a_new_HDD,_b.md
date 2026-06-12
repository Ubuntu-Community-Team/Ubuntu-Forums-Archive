---
title: "[SOLVED] I'm moving my /home folder to a new HDD, but I'm worried"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2008-03-19
in nautilus, when I go to access the second disk, it needs my sudo password.

Will this cause problems?

Also; I'm using this guide:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Anyone for see troubles in my future?

---

### Post by glennric on 2008-03-19
Once your home directory is relocated you will have permission to access it properly.  The reason you have to have root permission to access it now is because it is not in your home directory, and you haven't set the permissions so that you can access it.

---

### Post by Majin Zero on 2008-03-19
> **glennric said:**
> Once your home directory is relocated you will have permission to access it properly.  The reason you have to have root permission to access it now is because it is not in your home directory, and you haven't set the permissions so that you can access it.

Is the guide I found accurate though?

Do you see any potential problems with it?

---

### Post by aspen_dv on 2008-03-20
I read thru the guide quickly and it seems accurate. If you value your data, do a backup before commit to this. Also make sure everything working before do the last step (he suggesting sudo rm -r /old_home). You can always go back to your old directory.

---

### Post by Majin Zero on 2008-03-20
> **aspen_dv said:**
> I read thru the guide quickly and it seems accurate. If you value your data, do a backup before commit to this. Also make sure everything working before do the last step (he suggesting sudo rm -r /old_home). You can always go back to your old directory.

the data isn't all that important, it's not anything I couldn't re-obtain, but it'd be time consuming.

I'm mostly worried about borking my system, not data loss.

thank you for the replies though. I really appreciate it.

---

### Post by unutbu on 2008-03-20
The guide looks ok. But I suggest you 'man' each of the commands suggested in the guide before you use them, so you have at least a general idea of what each command is doing. Also try to understand the overall strategy -- why what the guide is saying is going to work. If you have any questions, feel free to post here. I'll be happy to help.

---

### Post by Majin Zero on 2008-03-20
$cd /home/
$find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/


I'm on this step; and it's saying it can't copy, no such file or directory; and it can't make the file in /newhome

permision denied.

And I even sudo'd it.

 Cannot open: No such file or directory


cannot make directory Permission denied

---

### Post by Tews on 2008-03-20
Check this thread out .. It will solve your problems and more...


[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by unutbu on 2008-03-20
So we can better help you, would you please post the output to
```

sudo fdisk -l
mount
cat /etc/fstab
ls -ld /mnt 

```

---

### Post by Majin Zero on 2008-03-20
> **unutbu said:**
> So we can better help you, would you please post the output to
```

sudo fdisk -l
mount
cat /etc/fstab
ls -ld /mnt 

```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94aaf13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb854d39b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux


/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98c1e663-24e3-49b1-b4b5-dec4e45f53be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=022a2eec-9a2f-48b6-8a0b-de8b97b52e8a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


drwxr-xr-x 3 root root 4096 2008-03-20 00:17 /mnt


I want to move my /home folder to the entirety of my second HDD. labled /dev/sda2

---

### Post by stchman on 2008-03-20
> **Majin Zero said:**
> in nautilus, when I go to access the second disk, it needs my sudo password.

Will this cause problems?

Also; I'm using this guide:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Anyone for see troubles in my future?

In System--->Administration--->Users you can specify your home folder as it defaults to /home/<your_name> you can change that to a different location.  

Say you have another partition mounted at /media/my_stuff then you can make a folder called home and change /home/<your_name> to /media/stuff/home.  Easy.

---

### Post by Majin Zero on 2008-03-20
> **stchman said:**
> In System--->Administration--->Users you can specify your home folder as it defaults to /home/<your_name> you can change that to a different location.  

Say you have another partition mounted at /media/my_stuff then you can make a folder called home and change /home/<your_name> to /media/stuff/home.  Easy.

wow, nice!

but, how do I transfer *everything* in my current home folder to it?

If I view hidden files and just copy all, will that do the trick?

What will happen to things that point to my home folder if I move it?

---

### Post by logos34 on 2008-03-20
> **Majin Zero said:**
> 
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb854d39b

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       14593   117218241   83  Linux**

...

I want to move my /home folder to the entirety of my second HDD. labled /dev/**sda2**

Is that just a typo?

You should have done:

$mkdir /mnt/newhome
$sudo mount -t ext3 /dev/**sdb1** /mnt/newhome

---

### Post by Majin Zero on 2008-03-20
> **logos34 said:**
> Is that just a typo?

You should have done:

$mkdir /mnt/newhome
$sudo mount -t ext3 /dev/**sdb1** /mnt/newhome

yes it's a typo

---

### Post by logos34 on 2008-03-20
delete

---

### Post by logos34 on 2008-03-20
Try changing the permissions and ownership on /mnt/newhome (I assume it's there).

sudo chmod -R 777 /mnt/newhome

Then, if it allows you to copy, change it back to 755 (i.e. drwxr-xr-x)

---

### Post by Majin Zero on 2008-03-20
> **logos34 said:**
> Try changing the permissions and ownership on /mnt/newhome (I assume it's there).

sudo chmod -R 777 /mnt/newhome

Then, if it allows you to copy, change it back to 755 (i.e. drwxr-xr-x)

sadly I'm a tiny bit noobish.

how do you change ownership, and whta's all this about 777 and 755?

---

### Post by logos34 on 2008-03-20
when you create a new ext3 partition you have to set the permssions and ownership to write to it, even if you add it to fstab to automount.  I have to set mine to 777 before I get write access.  But then you want to change it back to the standard settings for /home

more here:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

ADD:

You could always try moving /home using [this guide]("http://www.psychocats.net/ubuntu/separatehome") instead (it's the one I've used).  Only slightly different than what your using (it actually refers your command-line howto).  But you might have better luck.

---

### Post by Majin Zero on 2008-03-20
w00t after changing the permissions, the first guide's command that wouldn't work before works fine.

thanks for the permissions tip!

---

### Post by unutbu on 2008-03-20
[Edit: Sorry, somehow my browser did not show me everyone else's posts...]

```

mkdir /mnt/newhome
sudo mount -t ext3 /dev/sdb1 /mnt/newhome
cd /home
sudo sh -c "find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome"
sudo umount /mnt/newhome
sudo mv /home /old_home
sudo mkdir /home
sudo mount /dev/sdb1 /home

```

Verify everything looks right, but do not reboot yet.

Now let's depart a little bit from the guide. The guide tells you to add a line to /etc/fstab that begins with /dev/sdb1. This works as long as your new HDD gets assigned /dev/sdb1. What if you buy another drive some day, and your home drive becomes /dev/sdc1? Then your /etc/fstab would have to be edited. The modern way of handling this is to refer to the new HDD by a unique identifier, its UUID:

```

sudo umount /home
blkid /dev/sdb1

```

Look for something like UUID="03a507ee-cdac-4bd9-b438-eccd616b66ed". (That's my HD; yours will be something different).

```

gksudo gedit /etc/fstab

```

Add a line to the end of /etc/fstab:

```

UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /home ext3 nodev,nosuid 0 2

```

Again, change 03a507ee-cdac-4bd9-b438-eccd616b66ed to whatever blkid told you is right for you.

```

sudo mount /home

```

This tests that your /etc/fstab entry is correct. Again verify your /home directory looks correct.  If it does, you can try rebooting. 

As the guide says, if everything works, you can delete /old_home:

```

sudo -rm -rf /old_home

```

---

### Post by Majin Zero on 2008-03-20
unutbu, thanks, I'll try that when I make it to that step.

Currently I ran into a new problem.

while copying the files; it "ran out of space"

when it's only 11 gigs on a 120 gig HDD

so that's making no sense, and on top of that; I now can only go through mnt/newhome/[username]

to get to those files; I can't access the HDD or my partion manager now...says I don't have permission.

Any thoughts guys?

: (

this is turn out to be far more difficult then it should be...

---

### Post by Majin Zero on 2008-03-20
> **Majin Zero said:**
> unutbu, thanks, I'll try that when I make it to that step.

Currently I ran into a new problem.

while copying the files; it "ran out of space"

when it's only 11 gigs on a 120 gig HDD

so that's making no sense, and on top of that; I now can only go through mnt/newhome/[username]

to get to those files; I can't access the HDD or my partion manager now...says I don't have permission.

Any thoughts guys?

: (

this is turn out to be far more difficult then it should be...

ugh!

what happened here?!

some how I made a whole new partion on my first HDD...which filed up the disk...ok...so kinda I solved my own problem, need to delete that partion and start over

---

### Post by Majin Zero on 2008-03-20
> **Majin Zero said:**
> ugh!

what happened here?!

some how I made a whole new partion on my first HDD...which filed up the disk...ok...so kinda I solved my own problem, need to delete that partion and start over

wait...no....

I don't know where those files are now...

I need to unmount /mnt/newhome then delete that

what's the commands to do that?

---

### Post by unutbu on 2008-03-20
Not sure what the state of your filesystem is at this point.
Are you sure you want to delete anything?
Do you have a copy of your home dir?

---

### Post by logos34 on 2008-03-20
sudo umount /mnt/newhome

---

### Post by unutbu on 2008-03-20
Please run and post:

```

df -h

```

---

### Post by Majin Zero on 2008-03-20
yes, I figured out where stuff went

and I just want to delete my "newhome" folder now

my original home is untouched

Also, thanks for the un mount command....funny that it's just umount

not unmount

---

### Post by unutbu on 2008-03-20
```

sudo rm -rf /mnt/newhome

```
This will remove /mnt/newhome and all files within it.

---

### Post by Majin Zero on 2008-03-21
> **unutbu said:**
> [Edit: Sorry, somehow my browser did not show me everyone else's posts...]

```

mkdir /mnt/newhome
sudo mount -t ext3 /dev/sdb1 /mnt/newhome
cd /home
sudo sh -c "find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome"
sudo umount /mnt/newhome
sudo mv /home /old_home
sudo mkdir /home
sudo mount /dev/sdb1 /home

```

Verify everything looks right, but do not reboot yet.

Now let's depart a little bit from the guide. The guide tells you to add a line to /etc/fstab that begins with /dev/sdb1. This works as long as your new HDD gets assigned /dev/sdb1. What if you buy another drive some day, and your home drive becomes /dev/sdc1? Then your /etc/fstab would have to be edited. The modern way of handling this is to refer to the new HDD by a unique identifier, its UUID:

```

sudo umount /home
blkid /dev/sdb1

```

Look for something like UUID="03a507ee-cdac-4bd9-b438-eccd616b66ed". (That's my HD; yours will be something different).

```

gksudo gedit /etc/fstab

```

Add a line to the end of /etc/fstab:

```

UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /home ext3 nodev,nosuid 0 2

```

Again, change 03a507ee-cdac-4bd9-b438-eccd616b66ed to whatever blkid told you is right for you.

```

sudo mount /home

```

This tests that your /etc/fstab entry is correct. Again verify your /home directory looks correct.  If it does, you can try rebooting. 

As the guide says, if everything works, you can delete /old_home:

```

sudo -rm -rf /old_home

```

Everything works fine till I try to edit the fstab.

here's what I got for my blkid:

/dev/sdb1: UUID="EC981248981211A6" TYPE="ntfs" 

So I try to open gedit, it won't

I remount my /home

then it'll open so I can edit the fstab

I put in your line like you said; but when Iunmounted my home then tried:

sudo mount /home

it gives me this error:

mount: special device /dev/disk/by-uuid/EC981248981211A6 does not exist


this computer will probably never change hardware, since I'm going to be building a new one soon anyhow.

Would it be safe to go about how that guide did things?

---

### Post by unutbu on 2008-03-21
Yes, it would be safe to follow the guide and use
```
/dev/sdb1 /home ext3 nodev,nosuid 0 2
```

However, the UUID command should actually work if you simply reboot too.
The error
```

mount: special device /dev/disk/by-uuid/EC981248981211A6 does not exist

```
will go away because this file will be created at boot time provided the UUID in /etc/fstab matches your hard drive.

---

### Post by stchman on 2008-03-21
> **Majin Zero said:**
> wow, nice!

but, how do I transfer *everything* in my current home folder to it?

If I view hidden files and just copy all, will that do the trick?

What will happen to things that point to my home folder if I move it?

Use the cp (copy command).  Lets assume your name is joe for example.

```
cp -R -v ~/ /media/stuff
```

This will create a folder in /media/stuff called joe.  The -R is recursive and the -v is verbose to print out each file being copied.  This will get hidden files as well.

Now make the changes in the user profile manager.  Set it to /media/stuff/joe and you are set.

---

