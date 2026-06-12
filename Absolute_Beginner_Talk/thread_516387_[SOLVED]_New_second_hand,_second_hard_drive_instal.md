---
title: "[SOLVED] New second hand, second hard drive installation"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by tahitiwibble on 2007-08-03
Please, please, HELP!

I have an old computer and have installed this wonderful ubuntu 7.04 on my "master" drive.

I have added a second previously used and formatted internal hard drive for media storage and have succeeded in newly formatting it ext3.

Now it is owned by "unknown" and is 'read only'.

I have done this [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") and everything went ok, but I still can't write to it.

Please be kind! I am lost and confused and really need some assistance.

Many, many thanks for whatever input you can give me.

Cheers

---

### Post by bernied on 2007-08-03
Can you post the output (from a terminal - see [this](http://www.psychocats.net/ubuntu/terminal) to find out how if you don't know) from the following commands:
```
cat /etc/fstab
df -hT
mount
```
cat means output the file, or print to screen. So this will show me the contents of your fstab file
df is display filesystems, this will show me what filesystems are mounted and what type they are (and how much free space is in them)
mount, on it's own, displays all mounted filesystems, and the command used to mount them. This should give us some clues as to what's gone wrong.

---

### Post by rufi_dukes on 2007-08-03
> **bernied said:**
> Can you post the output (from a terminal - see [this](http://www.psychocats.net/ubuntu/terminal) to find out how if you don't know) from the following commands:
```
cat /etc/fstab
df -hT
mount
```
cat means output the file, or print to screen. So this will show me the contents of your fstab file
df is display filesystems, this will show me what filesystems are mounted and what type they are (and how much free space is in them)
mount, on it's own, displays all mounted filesystems, and the command used to mount them. This should give us some clues as to what's gone wrong.

hi, i found the above response you made to someone and thought you might be able to help me out;
i have just bought a new computer with feisty preinstalled but i can't get the dvd to work;
i cut and pasted what you advised the other guy to do and got this:

michael@tester-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65337b33-b4ca-45cf-a42e-00c7cd597bfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=238d9f43-ae49-4a1d-959f-711e0344bbe2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
michael@tester-desktop:~$ df -hT
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda1     ext3    288G  3.0G  271G   2% /
varrun       tmpfs   1005M  100K 1005M   1% /var/run
varlock      tmpfs   1005M     0 1005M   0% /var/lock
procbususb   usbfs   1005M  124K 1005M   1% /proc/bus/usb
udev         tmpfs   1005M  124K 1005M   1% /dev
devshm       tmpfs   1005M     0 1005M   0% /dev/shm
lrm          tmpfs   1005M   33M  972M   4% /lib/modules/2.6.20-16-generic/volatile
michael@tester-desktop:~$ mount

just glancing at it (and i am a total beginner with all of this) it would seem that the computer is reading my 2 drives as cdrom only...
can you suggest how i can fix this?

and if not, would going back to an earlier version (like dapper) help?
i mean, would installing the LTS version automate the mounting of devices so that, at the end of the install, without any further tweaking, i could watch dvds?

thx for taking the time to read and answer,
rufus

---

### Post by rufi_dukes on 2007-08-03
btw, when i do try to view a dvd, this is the message i get from totem:

"totem  could not play 'dvd:///media/cdrom1'
There is no plugin to handle this movie"

do you know what gives here?

rufus

---

### Post by bernied on 2007-08-03
> **rufi_dukes said:**
> btw, when i do try to view a dvd, this is the message i get from totem:

"totem  could not play 'dvd:///media/cdrom1'
There is no plugin to handle this movie"

do you know what gives here?

rufusTo me, this sounds like it means that the files can be read, which would mean that the device is being mounted correctly, but they cannot be decoded. You can check this by looking for files on the device. For instance, if you get a picture of a cd or dvd appearing on your desktop, click (or double-click?) on it, you should find two folders, probably labeled TS_AUDIO and TS_VIDEO. If you can find these folders then the problem is not with mounting (so no need to mess with /etc/fstab), the problem is just with decoding and/or playing.

So if that is the case, the easiest way to fix it might be just to install another video player, some of them come with all the codecs that you need. Try googling 'ubuntu video codecs', and see what you get, or just looking for 'video player' in your package manager. You will probably need to have non-free repositories enabled (google those words if you don't understand them, again with the word ubuntu) to install this stuff.

It's all about licences and free software and open source - very boring when you just want to watch a video, but it's part of the modern world, eh?

When you google, you will probably find lots of links to Automatix and/or EasyUbuntu. My advice is to try to avoid these as they are not part of Ubuntu, and tend to break stuff, but you will get plenty of advice saying that they are the bees knees and will solve all your troubles (including personal ones).

And next time, you should start your own thread, or search for similar. This has all been covered a hundred times before. Unless of course you can't access the files on the dvd, which means you've got some hardware issue, but then you should definitely start your own thread.

---

### Post by tahitiwibble on 2007-08-03
dad@daddesktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=1cad138f-bbae-482f-adcf-e465db72a344 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=942f7cc7-ea3a-42b2-9a57-f78e586a5cb1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd1 /media/floppy0 auto rw,user,noauto 0 0
dad@daddesktop:~$ 


dad@daddesktop:~$ df -hT
Filesystem Type    Size Used Avail Use% Mounted on
/dev/hda1     ext3     72G   54G   15G  79% /
varrun       tmpfs    252M  212K  252M   1% /var/run
varlock      tmpfs    252M     0  252M   0% /var/lock
procbususb   usbfs    252M  120K  252M   1% /proc/bus/usb
udev         tmpfs    252M  120K  252M   1% /dev
devshm       tmpfs    252M     0  252M   0% /dev/shm
lrm          tmpfs    252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2  fuseblk    152G   12G  141G   8% /media/155gigs
/dev/sda1  fuseblk    147G  138G  9.1G  94% /media/150gigs
/dev/hdb1     ext3    113G  188M  107G   1% /media/mynewdrive
dad@daddesktop:~$ 


dad@daddesktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/155gigs type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/150gigs type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdb1 on /media/mynewdrive type ext3 (rw)
dad@daddesktop:~$

---

### Post by tahitiwibble on 2007-08-03
BTW bernied, your explanations are second to none, very clear, helpful and very very appreciated. A Gentleman and a scholar!

---

### Post by rufi_dukes on 2007-08-03
[QUOTE=bernied;3126325]To me, this sounds like it means that the files can be read, which would mean that the device is being mounted correctly, but they cannot be decoded. You can check this by looking for files on the device. For instance, if you get a picture of a cd or dvd appearing on your desktop, click (or double-click?) on it, you should find two folders, probably labeled TS_AUDIO and TS_VIDEO. If you can find these folders then the problem is not with mounting (so no need to mess with /etc/fstab), the problem is just with decoding and/or playing.

thanks kindly,
yes, the files video_ts and audio_ts are both being read,
so, i'll go and see if i can find another dvd player...

much appreciated,
rufus

---

### Post by bernied on 2007-08-03
First, a question - how have you been trying to access the drive? Were you clicking on an icon on the desktop? Or were you manually mounting the drive at the command line?

Ok, so this stuff ...
> **tahitiwibble said:**
> dad@daddesktop:~$ df -hT
Filesystem Type    Size Used Avail Use% Mounted on
...
/dev/hdb1     ext3    113G  188M  107G   1% /media/mynewdrive

dad@daddesktop:~$ mount
/dev/hdb1 on /media/mynewdrive type ext3 (rw)
... tells me that the drive in question is called /dev/hdb1, it is indeed mounted on /media/mynewdrive, that it has tons of free space, and that it is mounted read/write (rw). 

But you say it's owned by unknown user and is read-only. Did you do the chown command that was suggested in that howto? Maybe there was a typo somewhere. Can you post the output of the following (stop if you get any error messages)?
```
df -hT
cd /media/mynewdrive
ls -al
sudo mkdir test
sudo chown dad test
touch test/testfile
ls -al test/
```
So that's
- show what's mounted, to make sure it hasn't changed since last time you did that command. If the '/dev/hdb1' line is not there, then there is no point continuing. Do whatever you did to try to access the drive before (relates to my question above), then try again.
- go to the base directory of the drive
- list all the files in the drive, with lots of detail. The two called '.' and '..' are the base directory itself and the parent directory - in this case /media. Other than these it's probably empty.
- make a new directory, with root privileges. Stop here if this doesn't work.
- change the ownership of the directory to you (assuming your username is dad)
- make a new empty file in the new directory called testfile
- list the content of the new directory

So, if you can create a directory, then you can write to the disk, and all you have to do is sort out the permissions (who owns the base of the filesystem, who owns the files/folders within it, and who can do what to them). You do that with the chown and chmod commands. This is pretty well explained in that howto you used.

If you cannot create a new directory, then there is something weird going on with the mounting of the drive. And you're doing something else that I don't understand with your ntfs partitions (windows is on that machine as well, right?), which is probably related. But the solution is probably to create an entry in the /etc/fstab file, which would tell the machine exactly how you want the drive mounted and when. That is also explained in that howto.

And flattery will get you everywhere.

---

### Post by tahitiwibble on 2007-08-03
Oh dear me! I feel so silly! I thought that I had finished when I got the drive to a 'mount point'. 

(It **was** 3 am though and I have had a lot of 18 hour days in front of my machine since going "jump in the deep end" 100% Ubuntu 10 days ago)

I finished the procedure and everything works perfectly now.

Your help was priceless and catalysed the solutions to a number of other little quirks I have come across. Thank you Squire!!!

Just before I posted my thread last night I had resolved an external XP formatted USB hard drive read/write/ownership dilemma and now find it curious that this is happening; 

#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

It's not doing any harm obviously but I wonder why this happens?

Anyway , thank you very much Sir.

Flattery has nothing to do with it ...................... credit where credit's due!

PS What book/website would you recommend for someone who is an old Mac power-user (started with the Classic but the best computer I ever had was the 6100 with a Windows card in it), has been able to tame the Microsoft mess over the past few years and now wishes to master the command line in Ubuntu 7.04?

---

### Post by bernied on 2007-08-03
You are welcome, it keeps me off the streets and out of the crack dens.

I didn't understand that text in the fstab file either, either some ubuntu magic, or something you've installed.

And I've no tips for books or guides. I've never opened a book about linux - all the information is on t'internet. It's just a question of learning how to search. 

There was one more wee nugget, about reserved disk space. When you create a new ext3 filesystem, the default behaviour (of mkfs.ext3) is to reserve 5% for the root user only. So on that 100GB disk, that's 5GB that you'll never be allowed to use. To reclaim it, you can use tune2fs, like:
```
sudo tune2fs -m 0 /dev/hdb1
```

Please say hello to the pacific ocean for me - i miss it.

---

### Post by tahitiwibble on 2007-08-04
:lolflag::lolflag::lolflag:

and I was wondering how many green sea turtle sightings there are a year in Edinburgh!

---

