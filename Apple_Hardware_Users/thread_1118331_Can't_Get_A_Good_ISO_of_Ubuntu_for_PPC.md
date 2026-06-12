---
title: "Can't Get A Good ISO of Ubuntu for PPC"
date: 2009-04-06
forum: Apple Hardware Users
---

### Post by dsnort33823 on 2009-04-06
I have a couple of old iBook clamshells laying around that I play with, decided to try to Ubuntu on one. I came to this forum and clicked on the download link in the sticky. Took forever to download, and when it finished, the volume won't mount. Get a message "No Mountable Files Found". Repeated download several times, no joy. 

Was able to download Ubuntu i386 from a torrent, it's fine, but can't find a PPC version?

Anyone know where to get one that works?

---

### Post by cyberdork33 on 2009-04-06
> **dsnort33823 said:**
> I have a couple of old iBook clamshells laying around that I play with, decided to try to Ubuntu on one. I came to this forum and clicked on the download link in the sticky. Took forever to download, and when it finished, the volume won't mount. Get a message "No Mountable Files Found". Repeated download several times, no joy. 

Was able to download Ubuntu i386 from a torrent, it's fine, but can't find a PPC version?

Anyone know where to get one that works?
you don't need to mount it, you need to burn the image to disc...

---

### Post by dsnort33823 on 2009-04-06
I'll give that a try, thanks

---

### Post by dsnort33823 on 2009-04-06
I was able to get the iBook to boot to the boot prompt, hit enter. The disk spun for a second, message "Please Wait, Loading Kernel". Then "Read Failed", returned to boot prompt.

---

### Post by cyberdork33 on 2009-04-06
> **dsnort33823 said:**
> I was able to get the iBook to boot to the boot prompt, hit enter. The disk spun for a second, message "Please Wait, Loading Kernel". Then "Read Failed", returned to boot prompt.
I'd guess bad burn or download then... did you verify the disc? 

It also helps to burn the disc at a very slow speed.

---

### Post by dsnort33823 on 2009-04-06
Well, I finally got a good image, booted, installed kernal, now "No Common CD-ROM Detected". It's asking if I want to install CD-ROM Module from a floppy, or activate card services?

---

### Post by dsnort33823 on 2009-04-06
I don't know if this makes a difference, but this model iBook has a DVD-CD-ROM.

---

### Post by pxwpxw on 2009-04-07
> **dsnort33823 said:**
> Well, I finally got a good image, booted, installed kernal, now "No Common CD-ROM Detected". It's asking if I want to install CD-ROM Module from a floppy, or activate card services?


The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.

[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)
__________________

---

### Post by dsnort33823 on 2009-04-07
Thanks, I tried that, no joy. My Clamshell has a DVD Rom, will that change things?

---

### Post by cyberdork33 on 2009-04-07
This user is having the same problem:
[http://ubuntuforums.org/showthread.php?t=1118336](http://ubuntuforums.org/showthread.php?t=1118336)

---

### Post by dsnort33823 on 2009-04-07
Hey, I figured it out! Yaaaay me! (In fact I'm typing on it now!

Thanks for the help, you got me pointed in the right direction!):P

---

### Post by cyberdork33 on 2009-04-07
> **dsnort33823 said:**
> Hey, I figured it out! Yaaaay me! 
can you post what you did so that other users can get it working?

---

### Post by dsnort33823 on 2009-04-07
Basically it was a picnic problem, (Problem In Chair Not In Computer).

I was downloading on a Mac, default action on disk images is to open after download, that's when I would get a corrupted download message. Just ignored it and burned image to disk in "Disk Utility", worked fine. ( You have to let the Mac attempt to open the iso in disk utility to get it to appear in the left pane of Disk Utility. It will give a "No Mountable Files Found Error", click "Do Not Open', the downloaded file will now be visible in left pane. Select it and click "Burn" icon at top).

Of note, Clamshell SE models have a DVD_ROM instead of CD-ROM, alternate version of Hardy Heron for Power PC install doesn't seem to like these. I never was able to get the installer to find optical drive despite all the suggestions found on these forums. Luckily, my SE had enough RAM to use the regular version, worked like a charm.

Thanks for all the help everyone.):P

---

