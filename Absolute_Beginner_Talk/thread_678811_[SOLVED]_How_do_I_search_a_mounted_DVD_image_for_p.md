---
title: "[SOLVED] How do I search a mounted DVD image for packages/dependencies?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-26
I have an offline Ubuntu box and I'm working on installing various packages and dependencies (via using a separate online XP system and NoNetDebs).  However somewhere along the way it was suggested that I could use a mounted .iso image of the Ubuntu DVD to accomplish much of the same thing.  I've been able to successfully mount the image using Gmount-ISO, however I don't know how to get Ubuntu to look at that source for packages/dependencies.  What am I missing?

Thanks!

---

### Post by jw5801 on 2008-01-26
You want to run ```
sudo apt-cdrom add */cd/mountpoint*
```Obviously you'll need to replace */cd/mountpoint* with wherever the LiveCD is mounted to.

---

### Post by toastysquirrel on 2008-01-26
> **jw5801 said:**
> You want to run ```
sudo apt-cdrom add */cd/mountpoint*
```Obviously you'll need to replace */cd/mountpoint* with wherever the LiveCD is mounted to.
I just gave it a try (mount point: /media/hdc1/disc) and it seems to ignore the mounted DVD and tries to spin up my (empty) CDrom drive.

Is there perhaps a better way to mount an ISO image that would work with the above?  Or any other solution of course :)

---

### Post by jw5801 on 2008-01-26
Hmm... I've never tried it with an .iso. It might need to be included in your /etc/fstab (which would explain why it goes looking in your CD drive, since that gets an entry by default during install). I'll have a play and get back to ya!

---

### Post by jw5801 on 2008-01-26
Hmm... apparently my syntax was wrong! Try:
```
sudo apt-cdrom add -d /media/hdc1/disc
```

If that works correctly you should be able to run "sudo apt-get update" and then install packages as you normally would with an internet connection.

The man page does say that the mountpoint should be in /etc/fstab however. So if the first bit doesn't work then you'll need to add a line to the end of /etc/fstab that looks like the following:
```
# first create a mountpoint:
sudo mkdir /media/iso/
# now open fstab for writing
gksudo gedit /etc/fstab
# the append the following to the end of the file
*/path/to/ubuntu.iso*     /media/iso      iso9660 defaults,loop   0       0
```
Once again you'll need to replace the italics with wherever the iso is kept. The try the first command (sudo apt-cdrom...) again and see if it works better!

---

### Post by toastysquirrel on 2008-01-28
Foey, so far no luck. I followed your instructions, but apparently to no avail.

1) created mount point "[COLOR="Green"]/media/iso[/COLOR]"
2) edited fstab with the following info, placing it below the last line of code: [COLOR="Green"]/media/hdc1/../ubuntu_dvd.iso     /media/iso      iso9660 defaults,loop   0       0[/COLOR]
3) I then saved and exited gedit.
4) mounted the iso with gmount-iso to the point [COLOR="Green"]/media/iso[/COLOR]
5) ran the code [COLOR="Blue"]sudo apt-cdrom add -d /media/iso[/COLOR]

And the result is simply the output if you type "[COLOR="Blue"]sudo apt-cdrom[/COLOR]"

Veeeery strange indeed.  Any other thoughts? :)  Thanks for the help thus far though, I really appreciate it.

---

### Post by jw5801 on 2008-01-29
Everything works alright here. Maybe try mounting it from the commandline?
```
jw5801@laptop:~$ sudo mount -o loop .install/LiveCDs/ubuntu-7.10-desktop-amd64.iso /media/iso/
jw5801@laptop:~$ ls /media/iso
autorun.inf  casper    dists    isolinux    pics  preseed   README.diskdefines  start.exe  ubuntu      wubi-cdboot.exe
bin          disctree  install  md5sum.txt  pool  programs  start.bmp           start.ini  ubuntu.ico
jw5801@laptop:~$ sudo apt-cdrom add -d /media/iso/
Using CD-ROM mount point /media/iso/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [284ba92e6968a9d1bb8adac436b01aff-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 09:52:52 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set
jw5801@laptop:~$ 
```

Hang on, it unmounts it anyway (I remember it doing this with the physical CD too), it's possible umount tries to unmount it and fails since it was mounted using a Gnome app. You'll find you can't unmount things using gnome if you mounted them at system level from the commandline or vice versa.

So first off, try it without the iso mounted at all (same command though). If that fails try mounting it from the command lline as I have above, and see if that helps.

---

### Post by toastysquirrel on 2008-01-30
Okay, I altered the syntax slightly to [COLOR="Blue"]sudo apt-cdrom -d /media/iso add[/COLOR] (changing the order of "add") and I received the output:

```
Using CD-ROM mount point /media/iso/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [3633e61c4bcae09f47684c44397af3ff-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)'
Copying package lists...gpgv: Signature made Wed 17 Oct 2007 03:55:09 AM PDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.

```
So far so good; FYI I think it found it both times when it was previously mounted and unmounted.  I then loaded up Synaptic Package Manager and I saw the two entries listed (main and restricted).
I then tried to load one of the listed packages, and I got this:
[IMG]http://img352.imageshack.us/img352/4857/screenshotsynapticld4.png[/IMG]

I've received that when the image was mounted at /media/iso and when unmounted.  Almost there but not quite. :)

---

### Post by jw5801 on 2008-01-30
Ok, I'm not sure why it insists that the disc be mounted to /media/cdrom/ but it seems to need to be mounted there. I encountered the same thing you have here (I use apt-get from the command line though) and unmounting the iso and mounting it at /media/cdrom/ got everything working properly.

---

### Post by toastysquirrel on 2008-02-01
> **jw5801 said:**
> Ok, I'm not sure why it insists that the disc be mounted to /media/cdrom/ but it seems to need to be mounted there. I encountered the same thing you have here (I use apt-get from the command line though) and unmounting the iso and mounting it at /media/cdrom/ got everything working properly.

Okay, I think it's finally all squared away now that it's mounting to cdrom0.  Here's an additional question though: since I've altered the 'fstab' file, the DVD is mounting with every boot.  What's a good way to mount it on an as/need basis, or is convenience just something that gets sacrificed with mounting an ISO this way?

---

### Post by jw5801 on 2008-02-02
Try adding the "noauto" option to the fstab line. I'm reasonably sure that's what that option is for. Then you should just need to mount it as you were mounting it before.
```
*/device     /mntpoint*      iso9660 defaults,loop,noauto   0       0
```

---

### Post by toastysquirrel on 2008-02-08
> **jw5801 said:**
> Try adding the "noauto" option to the fstab line. I'm reasonably sure that's what that option is for. Then you should just need to mount it as you were mounting it before.
```
*/device     /mntpoint*      iso9660 defaults,loop,noauto   0       0
```

Awesome, that worked like a champ: no mount at startup, successful mount via Gmount-ISO, installed a package from the DVD image, and unmounted afterwards without a hitch.

Thanks JW!

---

### Post by jw5801 on 2008-02-08
No probs! :)

---

