---
title: "Can't rename ext HD"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-10-24
Hey there, I've got an external USB hard drive (160 gig Western Digital model number WD1600U017-004) mounted to my laptop that I want to rename, but I can't seem to manage it. I keep getting this error message:

```
halflingrogue@ubuntu:/media$ sudo mv 'LA HUEVOSA' 'LaHuevosa'
mv: cannot move `LA HUEVOSA' to `LaHuevosa': Device or resource busy
halflingrogue@ubuntu:/media$ 
```

Anybody know an alternative way of doing this, or what the problem is? (Keep in mind that I've got 20-odd gigs of stuff on the HD, and I don't want to do anything that'll risk losing it.)

**EDIT:** Also not letting me chmod it, either. Anyone know what the problem could be? I'm running Dapper on an IBM ThinkPad. Ext HD is WD brand.

**ETA2:** Getting an I/O error off of pvdisplay, which I'm pretty sure is Not Good (also getting an I/O error on boot). Found a patch which may be useful, but as I know nothing about patches, I can't say for sure. Help?

**ETA3:** Probably related to [this problem]("http://ubuntuforums.org/showthread.php?t=561630"). Again. ](*,)

---

### Post by Halfling Rogue on 2007-10-24
Bump-de-bump bump.

---

### Post by CaptainInsaneO on 2007-10-24
Make sure your hdd is on and running, and then click Places>Computer. Right click your external, and click "Rename".

---

### Post by Halfling Rogue on 2007-10-24
"Sorry, couldn't rename "LA HUEVOSA" to "LaHuevosa"."

---

### Post by Halfling Rogue on 2007-10-24
Bump.

---

### Post by Halfling Rogue on 2007-10-24
Great. It's also not letting me chmod. Is it possibly some kind of access error?

```
lrwxrwxrwx  1 root          root              6 2007-07-23 18:01 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 cdrom0
lrwxrwxrwx  1 root          root              7 2007-07-23 18:01 floppy -> floppy0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 floppy0
drwx------ 20 halflingrogue halflingrogue 32768 1969-12-31 16:00 LA HUEVOSA
-rw-r--r--  1 root          root             17 2007-10-24 17:11 tryagain
halflingrogue@ubuntu:/media$ sudo chmod 755 'LA HUEVOSA'
Password:
halflingrogue@ubuntu:/media$ ls -l
total 44
lrwxrwxrwx  1 root          root              6 2007-07-23 18:01 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 cdrom0
lrwxrwxrwx  1 root          root              7 2007-07-23 18:01 floppy -> floppy0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 floppy0
drwx------ 20 halflingrogue halflingrogue 32768 1969-12-31 16:00 LA HUEVOSA
-rw-r--r--  1 root          root             17 2007-10-24 17:11 tryagain
halflingrogue@ubuntu:/media$ sudo chmod 755 tryagain
halflingrogue@ubuntu:/media$ ls -l
total 44
lrwxrwxrwx  1 root          root              6 2007-07-23 18:01 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 cdrom0
lrwxrwxrwx  1 root          root              7 2007-07-23 18:01 floppy -> floppy0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 floppy0
drwx------ 20 halflingrogue halflingrogue 32768 1969-12-31 16:00 LA HUEVOSA
-rwxr-xr-x  1 root          root             17 2007-10-24 17:11 tryagain
halflingrogue@ubuntu:/media$
```

---

### Post by Halfling Rogue on 2007-10-24
It's also doing this, and I'm pretty sure it's not supposed to. The HD makes 'working' noises whenever I run this check, but I never get any feedback:

```
halflingrogue@ubuntu:/media$ sudo lvdisplay -v
    Finding all logical volumes
  No volume groups found
halflingrogue@ubuntu:/media$ sudo pvdisplay -v
    Scanning for physical volume names
halflingrogue@ubuntu:/media$
```

**EDIT:** Never mind, got feedback! Not that it's *good* feedback . . . 

```
halflingrogue@ubuntu:/media$ sudo pvdisplay -v
    Scanning for physical volume names
  /dev/sda1: read failed after 0 of 2048 at 0: Input/output error
halflingrogue@ubuntu:/media$
```

---

### Post by Jittoku on 2007-10-24
Perhaps the space in the name is confusing it.  I'm a beginner and I hope this isn't a waste, but a buddy helped me rename a drive that had a two word name out of the box.  Try writing the name with a backslash before the space, like this: 

sudo chmod 755 'LA\ HUEVOSA'

Supposedly that's supposed to make the shell recognize that the space is part of the name and not a delimiter in the command. (?)  I've never used the quotes around the name before, so I don't know if that's supposed to do the same thing.  Maybe you should leave those out?

Cheers.

---

### Post by Halfling Rogue on 2007-10-24
Hmm, looks like Linux is already recognizing it as part of the name:

```
halflingrogue@ubuntu:/media$ sudo chmod 755 'LA\ HUEVOSA'
chmod: cannot access `LA\\ HUEVOSA': No such file or directory
halflingrogue@ubuntu:/media$
```

Thanks, though!

**Edit:** Ah, never mind, it was the quotes. Still didn't work, though. :(

```
halflingrogue@ubuntu:/media$ sudo chmod 755 LA\ HUEVOSA
halflingrogue@ubuntu:/media$ ls -l
total 44
lrwxrwxrwx  1 root          root              6 2007-07-23 18:01 cdrom -> cdrom0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 cdrom0
lrwxrwxrwx  1 root          root              7 2007-07-23 18:01 floppy -> floppy0
drwxr-xr-x  2 root          root           4096 2007-07-23 18:01 floppy0
drwx------ 20 halflingrogue halflingrogue 32768 1969-12-31 16:00 LA HUEVOSA
-rwxr-xr-x  1 root          root             17 2007-10-24 17:11 tryagain
halflingrogue@ubuntu:/media$
```

---

### Post by Halfling Rogue on 2007-10-24
Found a patch that may be relevant, anyone let me know if it's any good?

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg16405.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg16405.html)

---

### Post by Halfling Rogue on 2007-10-24
Bump.

---

### Post by Halfling Rogue on 2007-10-25
Bump. Anyone know where I can get a patch?

---

### Post by Halfling Rogue on 2007-10-27
Bump.

---

### Post by CaptainInsaneO on 2007-10-27
I apologize for my bad advice earlier, I can help you though. What format is this hdd? (i.e. NTFS, fat32, ext3, vfat?)

---

### Post by Halfling Rogue on 2007-10-27
FAT32. Here's the fdisk output, it's sda1:

```
Disk /dev/hda: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         753     6048441   83  Linux
/dev/hda2             754         789      289170    5  Extended
/dev/hda5             754         789      289138+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    c  W95 FAT32 (LBA)
halflingrogue@ubuntu:/media$
```

---

### Post by CaptainInsaneO on 2007-10-27
Ok, good.

Do the following:

Make sure that your external drive is ON, but UNMOUNTED.
apt-get mtools if you don't already have it.
```
sudo mlabel -i /dev/sda1 -s ::
```
and then
```
sudo mlabel -i /dev/sda1 ::LaHuevosa
```
now, to check your work:
```
sudo mlabel -i /dev/sda1 -s ::
```

If all went well you should get something like "Volume Label is LaHuevosa", etc.

Now, just remount it and you should be good.

---

### Post by Jittoku on 2007-10-30
HR, did that last piece of advice work?

---

### Post by Halfling Rogue on 2007-10-30
Ack! Sorry, I didn't get an alert for some reason. I'm at school at the moment, I'll give it a try as soon as I get home.

(I'll also note that the HD won't mount on Windows at *all*, and usually causes Windows to freeze on top of that--although when I first got it, it would work on both Ubuntu and Windows just fine. So if anyone knows a way for me to find out what's wrong with that . . . )

---

### Post by Jittoku on 2007-10-30
This is a total "hail Mary" (and probably a very silly newbie suggestion, excardon me) but one of the first things I noticed when I started reading your thread was the date of the drive:  December 31st, 1969.   At first I discounted it, but then I got to wondering . . .  

That drive is living in "negative Unix time", which started at 12:00:01 on January 1, 1970.  Do you suppose that could be the problem?  Maybe Linux can't handle a negative sign in the time.  Can you get ls to show seconds, too?  Maybe it's stalled at one second before midnight.  

Could you use "touch" to fix that?  If it's not the problem, how do you suppose that time ended up on the drive, anyway?

---

### Post by CaptainInsaneO on 2007-10-31
Wow... you have some sharp eyes there! I completely missed that.

My externals all have the correct timestamp on them, so I don't know could cause Halfling's drives to do that. I don't think touch will work, the man page says it's for timestamping files, but not drives. Great idea though!

---

### Post by Halfling Rogue on 2007-11-02
I was wondering why it had that date, but I didn't realize it was negative Unix time. Odd.

Anyway, now I'm having unmounting problems too:

"Unable to eject media

Error: could not determine real path of the device: No such file or directory
eject: unmount of `/media/LA\040HUEVOSA' failed"

---

### Post by Halfling Rogue on 2007-11-02
Never mind, it's late and I'm being stupid.

```

halflingrogue@ubuntu:~$ sudo mlabel -i /dev/sda1 -s ::
Can't open /dev/sda1: No such file or directory
Cannot initialize '::'
mlabel: Cannot initialize drive
halflingrogue@ubuntu:~$
```

Can't seem to find it if it's not mounted.

---

### Post by Halfling Rogue on 2007-11-02
Can't do it if it's mounted, either!

```
halflingrogue@ubuntu:~$ sudo mlabel -i /dev/sda1 -s ::
Cluster # at 2944 too big(0xd905aeb)
Probably non MS-DOS disk
Cannot initialize '::'
mlabel: Cannot initialize drive
halflingrogue@ubuntu:~$
```

---

### Post by Halfling Rogue on 2007-11-03
Oops, got it to work unmounted! Well, kind of. At least I got a return:

```
halflingrogue@ubuntu:~$ sudo mlabel -i /dev/sda1 -s ::
Password:
Bad media types 39/f8, probably non-MSDOS disk
Cannot initialize '::'
mlabel: Cannot initialize drive
halflingrogue@ubuntu:~$ sudo mlabel -i /dev/sda1 ::LaHuevosa
Bad media types 6e/f8, probably non-MSDOS disk
Cannot initialize '::'
mlabel: Cannot initialize drive
halflingrogue@ubuntu:~$
```

---

### Post by LinuxGuy1234 on 2007-11-28
"MS-DOS disk"

Reformat the stick with FAT16 and try the mlabel commands. Does that help? (Risk to lose data on it, backup it first)

---

### Post by Halfling Rogue on 2007-11-28
Gaah, I can't back it up. It's 20 gigs of stuff and I don't have access to any non-Windows machine with that much memory.

---

### Post by Artsaypunk on 2007-12-09
I have a similar problem.  My external harddrive did not mount the first time I ever plugged it in to my gutsy install.  It said it was not shut down properly in Windows.  I couldn't force it to mount either.  So I found a windows machine, plugged it in and shut it down properly.  Now it mounts in ubuntu no problem, but it is no longer accepted by windows.  I can't remember what the error message was, something along the lines of "There is a problem with this device," which was obviously very helpful.

Oh, and I get the same error messages as Rogue when trying to rename the drive.

Any ideas out there?

---

### Post by CaptainInsaneO on 2007-12-09
I hate to say this, but I had a problem with one of my externals a couple days ago, the only thing that fixed it was booting into windows and running chkdsk with the /F switch on it.

It recovered over 300 gigs of data that I thought I had lost forever... :mad:

Should try running chkdsk on it... hate to say that.

---

