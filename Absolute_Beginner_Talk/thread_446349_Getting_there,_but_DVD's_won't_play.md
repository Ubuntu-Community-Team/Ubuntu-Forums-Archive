---
title: "Getting there, but DVD's won't play"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by homergreg on 2007-05-16
I've got my Presario V5000 Laptop pretty much working, even wireless, thanks to reading these forums!  The only thing that is not working completely as far as I can tell right now is my CD-RW/DVD drive.  It will mount a CD just fine, but will not mount DVD's.  Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=7a0b9f4e-cb33-44fa-825e-bad93a11598b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6E48A18E2EB882AA /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=3EC6-2E70  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=81af9ee1-2b23-495d-851d-85ab11153858 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


The drive is a philips cd-rw/dvd-rom scb5265. 
Any ideas for a newbie?

Thanks!

---

### Post by chamberlain2006 on 2007-05-16
Are you trying to mount DVD's or play them?  The two are very different.

---

### Post by esoterica on 2007-05-16
If your trying to play them and can't did you somehow mis the VERY OBVIOUS sticky post at the top of the forum here. It's annoying enough having to always scroll down below all those annoying sticky posts at the top of the page, which makes it even more annoying to see no one is reading them anyhow.

The very obvious link you should read:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by homergreg on 2007-05-16
Sorry bout that.  It will mount and read, the DVD's wont play.  I do get errors from totem saying could not read from resource.  I can however cd into /media/cdrom0 directory and read the files from a DVD.  

Thanks !

---

### Post by homergreg on 2007-05-16
> **esoterica said:**
> If your trying to play them and can't did you somehow mis the VERY OBVIOUS sticky post at the top of the forum here. It's annoying enough having to always scroll down below all those annoying sticky posts at the top of the page, which makes it even more annoying to see no one is reading them anyhow.

Sorry!  I was searching using strings that must have not caught the Multimedia Sticky thread.  Thank you for pointing that out.

---

### Post by homergreg on 2007-05-16
Thanks, that fixed it!

---

### Post by esoterica on 2007-05-17
;-)

A word of caution, don't enable "Desktop Effects" or your likely going to find it stops working for you again and instead spits missing codec errors at you even though the codecs aren't missing or the problem, desktop effects enabled being the only problem. Mine would actually auto start the DVD and play the sound, but the video screen was blank.

Found that out myself the hard way and it's tough searching for a solution to a problem like that and finding the right answer when you aren't even looking for the right problem, none of my searches on missing codecs like the error was telling me suggested this was actually a problem caused by desktop effects being enabled.

---

### Post by bford16 on 2007-06-24
> **homergreg said:**
> Sorry bout that.  It will mount and read, the DVD's wont play.  I do get errors from totem saying could not read from resource.  I can however cd into /media/cdrom0 directory and read the files from a DVD.  

Thanks !

Did you find a solution? I am having the same problem.  I did enable desktop effects, but turned them off later (at least I think I did).

---

### Post by Sl1k on 2007-06-24
Awsome, Thanks for the help!

[http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624") <----- worked no problem after following this guide,

Just be sure to disable desktop effects, or you'll find the video will be buggy.:KS

---

### Post by Vic! on 2007-09-06
HEy i just tried this and the source list in my case cannot be altered because it is read only :( i went to the restricted formats ubuntu page and tried doing it their way but when i try to instal libdvdcss2 it said it was missing

---

### Post by th3rmite on 2007-09-07
To solve the problem with Desktop Effects and video, follow this guide:

[http://ubuntuforums.org/showthread.php?t=507332&highlight=Video+Playback+Problem+in+Compiz-Fusion](http://ubuntuforums.org/showthread.php?t=507332&highlight=Video+Playback+Problem+in+Compiz-Fusion)

---

