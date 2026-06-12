---
title: "[SOLVED] External USB NFTS Hard Disk"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by etotheipiplusone on 2008-02-27
Hey guys, I've searched the forums and been unable to find help for my issue. 

So I mounted an external NTFS USB drive on Gutsy Gibbon, and I can read and write from it most of the time without an issue.  However, randomly, some folders will become unreadable, and I can't tell why.  Generally, mounting and unmounting the disk fixes this problem, but every mount and umount, some folders (it seems random folders) are unreadable.  The error it throws when I try to cd to them is "Input/output error" which is about as vague as it gets. 

Any help would be appreciated.  My fdisk -l is below. 

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9969    80027797+   7  HPFS/NTFS
/dev/sda3            9970       19060    73023457+  83  Linux
/dev/sda4           19061       19452     3148740    5  Extended
/dev/sda5           19061       19452     3148708+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```]

The drive in question is  /dev/sdb1, and is a Seagate Freeagent. 

Thanks!

---

### Post by jan quark on 2008-02-27
can you post the fstab file please


```
cat /etc/fstab
```

thank you

---

### Post by etotheipiplusone on 2008-02-27
My fstab file is below: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e290f8cd-0c3a-4ce8-98b7-7a37213699fd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=860d8302-7947-4233-b10b-0247e78e1922 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Thanks.

---

### Post by etotheipiplusone on 2008-02-28
Bump.

---

### Post by ryanhaigh on 2008-02-28
your /etc/fstab doesn't show any info on your usb drive, the output of mount when the drive is mounted may be more useful for those trying to help you. When I read your post I remembered seeing a slashdot article related to freeagent drives and problems with linux, googling seagate freeagent linux points me [here]("http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/")  wwhich may be related and has a workaround that might help.

---

### Post by etotheipiplusone on 2008-02-28
Thanks for your reply.  I don't know that that's necessarily the issue.  My Seagate still won't let me read/write from it when it is mounted even after I force it to come out of idle.  The engadget article had a hard fix for the idle issue, but it doesn't solve my problem.  

My sudo mount output is below: 

```
sjoshi@sjoshi-desktop:/$ sudo mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

I don't know enough to parse the /dev/sdb1 line, but does "nosuid" and "nodev" mean something is wonky?  They don't appear on on sda3 my Linux install partition.  And I know not having the drive listed in my fstab file is bad, but I don't know how to add it.

---

### Post by ryanhaigh on 2008-02-28
actually its not bad at all considering that it is an external drive. it seems strange to  me that mount is reporting the type as fuseblk i would have though it would be ntfs-3g (could be wrong about this), the nosuid and nodev options are normal i believe. The nosuid means that no executables on the drive can be run as root from a normal user.
Have you plugged the drive into a windows machine and tried a checkdisk maybe? Are you using strange characters in the filenames?

edit: yep was wrong just checked my own ntfs-3g mount and it says fuseblk as well

---

### Post by etotheipiplusone on 2008-02-28
So the paths on the drives do have spaces in directory names, but like I said, some directories I can access even though they have spaces in the path.  

I haven't done a checkdisk on the drive, but I have machine set up in dual boot with XP and I can access anything I want in XP, so it seems to me that the data is uncorrupted.  

What I find most unusual is that which folders get unreadable ("input/output error"-ed) seems to be a function of time.  Strange.

---

### Post by ryanhaigh on 2008-02-28
Spaces should not cause and problems I was more referring to things like & which are acceptable in linux but not windows. Your problem does seem quite peculiar, maybe try having a look at the bugs for ntfs-3g in launchpad and the projects own home page. Apart from that maybe the output of dmesg when the read failures occur could provide some useful information.

---

### Post by SneakPeak on 2008-03-02
Hi,

Possibly not directly related to the question but... if the drive is re-formatted as an ext3 drive does this problem of random missing directories go away?

Thanks 

Sneak Peak

---

### Post by etotheipiplusone on 2008-03-02
I supposed I could give it a shot, but I kind of wanted to avoid this so as to let the drive interface with Windows.  I mean the whole point of an external disk is that its movable, right?  And since the bulk of PC's are non linux, I'd rather leave it more compatible with the masses.  And yeah, I do take it around a decent amount for projects in groups and whatnot.  I guess I'll use this as my nuclear option.

---

### Post by etotheipiplusone on 2008-03-02
As of now, I think I can consider the problem solved.  

After using the fix described [here]("http://alienghic.livejournal.com/382903.html"), I think I fixed the issue, but not immediately.  After preventing the drive from ever going to sleep using the fix, I had to unmount and mount it again.  Since then I have not had an issue with the drive.  

Call this tentatively solved?  I'll change the thread title, but if I have any future trouble, I'll post in here. 

Thanks to everyone who helped!

---

### Post by SneakPeak on 2008-03-02
Hi 

I saw the stuff below here: [http://www.ntfs-3g.org/support.html#locale3](http://www.ntfs-3g.org/support.html#locale3) 

I am too much of a newbee to know if it will help or how to use it but perhaps you can use it to solve the problem???

Missing, disappeared files or directories?
or
Why can't I see all filenames with national characters?
or
Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?
    This means that your operating system (OS) doesn't have the correct language specific settings (locale, LANG variable, LC_ALL, etc) thus some filenames can't be converted to your language and won't be visible. The reason can be:

        * The locale setting wasn't configured during installation.
        * Not the correct locale was configured.
        * The configured value doesn't exist on the system.
        * The OS configures the setting in a too late stage during the boot process, only after the NTFS volume was already mounted. 

    The most common explanation is the latter one. This is why unmounting then mounting such volumes after boot often makes all filenames visible.

    Solution: The OS vendor should move the language specific configuration to an earlier phase to precede the mounts of the NTFS volumes in time.

    Workaround: ntfs-3g supports the 'locale' mount option which can be used to set the correct language value. You can see what locales you have on your system by using the following command:

    locale -a

    If you can't find the preferred setting then you must generate it, which is very distribution dependent. To do so, a package like glibc-i18ndata (openSUSE, Mandriva, ...) or locales (Debian, Ubuntu, ...) must be installed then enter the below command as root to generate the language_COUNTRY.UTF-8 locale. For example the Brazilian is:

    localedef -i pt_BR -f UTF-8 pt_BR.UTF-8

    Then you can use the "locale=pt_BR.UTF-8" option during mount.

    If some of your softwares are not UTF8 ready then they will not show correctly the UTF8 filenames. Please consult your distribution documentation about how to enable full UTF8 support.

    Status: Not ntfs-3g problem. Please ask your OS vendor to fix the boot time configuration problem.

---

### Post by etotheipiplusone on 2008-03-02
[This]("http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent") may actually be a better fix to the problem than the [previous one]("http://alienghic.livejournal.com/382903.html").  The new fix actually allows Linux to wake up the napping FreeAgent drive, whereas the previous fix just prevents the drive from going to sleep at all.  Better for power savings, if that's important to you. 

To Sneak Peak: 

I looked through that page, but my error was never that the files were *missing* persay, just that I couldn't read/write to certain directories, that were very much visible.  The closest thing on that page was the "I/O error" section, as I was getting a very similar error message.  Its logged in /var/log/daemon.log, so I've pasted it below. 

```
Feb 27 19:44:59 sjoshi-desktop ntfs-3g[9398]: Error reading $Mft record(s): Input/output error
Feb 27 19:44:59 sjoshi-desktop ntfs-3g[9398]: ntfs_mft_record_read failed: Input/output error
Feb 27 19:44:59 sjoshi-desktop ntfs-3g[9398]: ntfs_attr_pread: ntfs_pread failed: Input/output error

```

Now, I don't know what that means or anything, but a quick Google search **led me to the solution below, on Ubuntu forums itself.**  The symptoms don't overtly match my drive's symptoms, but that the error messages logged are similar leads me to beleive that they are in fact the same. 

[SIZE="5"]Solution:[/SIZE]
[SOLUTION.http://ubuntuforums.org/showthread.php?t=494673]("http://ubuntuforums.org/showthread.php?t=494673")
[http://ubuntuforums.org/showthread.php?t=494673]("http://ubuntuforums.org/showthread.php?t=494673") via [http://forums.fedoraforum.org/archive/index.php/t-171254.html]("http://forums.fedoraforum.org/archive/index.php/t-171254.html"). 

This fix is essentially the same one called "This" above.  

I suppose the moral of the story is that sleeping drives = trouble in linux.  Basically you just have to fiddle a little bit to let Linux wake them up when they go to sleep.  

I hope this helps some people out there.  

PS: This may be a good excercise in why searching the forums first is a good idea.  I'd like to point out that I made a good faith effort to do so, and I was only led back to the link in Ubuntu forums by links that people who posted here provided me.  Thanks to you all!

---

### Post by SneakPeak on 2008-03-03
Thanks:

This solution worked for me:

To resume the above URL use:

 /usr/bin/sdparm --clear STANDBY -6 /dev/sd[YOUR_DEVICE] 

(eg: /usr/bin/sdparm --clear STANDBY -6 /dev/sda)

You can put this command in your /etc/init.d/rc.local if needed.

The other solution gave me a permission denied error even when I used sudo?  Anyway this worked.  I have to say it's a bit freaky doing something when you have no idea what the command you are typing does!!  Oh well it works so I guess that is all that counts.

Sneaks.

---

### Post by etotheipiplusone on 2008-03-04
Alright, I have another question! 

So I implemented the fix that tells the drive to never go to sleep.  How do I undo this?  My drive literally spins constantly, and this is annoying and probably not good for the drive.  

For reference, I used the fix described below. 

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

I just don't know the unix commands to change the STANDBY cha=n to cha=y. 

Thanks.

---

### Post by ryanhaigh on 2008-03-04
actually while it may be annoying having the drive stay spinning is ARGUABLY better as it maintains its temperature (not expanding and contracting) and i think there is less wear on the motor not having to spin-up constantly. personally i think i would find the drive spinning up and down more annoying(not to mention file corruption!) but that depends on usage habbits.

sorry can't help with the fix but u may want to have a look at the man page for sdparm it might be able to help. Based on the quick read i had i think you should be able to do sudo ```
 sdparm --set STANDBY -6 /dev/sde
``` although I have no idea what the -6 does and Im just taking it from the howto you referenced.

---

