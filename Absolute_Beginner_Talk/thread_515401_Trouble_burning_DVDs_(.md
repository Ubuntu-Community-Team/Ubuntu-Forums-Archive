---
title: "Trouble burning DVDs :("
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-08-01
Hey everyone~

I seem to be having trouble burning DVDs under linux.  When I put a blank DVD in it does get recognized and is put on the desktop.  When I use a program like Gnomebaker or k3b I get this out put:

```
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p henaro -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-henaro/gnomebaker-7K3VWT | builtin_dd of=/dev/hdc obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/hdc: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=4h/ASC=91h/ACQ=25h]: Input/output error
:-( write failed: Input/output error
```


Does anyone know what's up with this?  I'm trying to burn a ISO image.  My DVD burner is an AOpen DUW1616/AAR.  When I try to burn things with k3b and get the error the disks seem to be unusable afterwards.  I've gone through 6 DVDs.  :(

Thanks,
Henaro

---

### Post by wolfen69 on 2007-08-01
are you using IDE drives in a slave/master configuration?(cd burner and hard drive on same cable)

---

### Post by Genecks on 2007-08-01
Open terminal.
If you don't know how, do this:

1. hold alt and press F2.
2. type in "xterm" (no parentheses)
3. change the below part of "/media/dvd/" with where your dvd is mounted; make sure you point it to where the iso is.

```
growisofs -dvd-compat -Z /media/dvd=/home/ubuntu/Desktop/image.iso
```

Afterwards, use _your_ altered version of the code in terminal.

---

### Post by Henaro on 2007-08-02
> **wolfen69 said:**
> are you using IDE drives in a slave/master configuration?(cd burner and hard drive on same cable)
I believe that my CD burner and my DVD/CD burner are on the same cable, but I'm not sure about my HD.  


And I can't figure out where my DVDs are being mounted too.  In my media folder I have cdrom cdrom0 and cdrom1.  And when I click on the blank DVD icon on the desktop it brings me to burn://

---

### Post by jackmc on 2007-08-02
I had the same error, I think I solved my issue.

Have a look here:

[http://ubuntuforums.org/showthread.php?p=3119859#post3119859](http://ubuntuforums.org/showthread.php?p=3119859#post3119859)

---

### Post by Henaro on 2007-08-02
> **jackmc said:**
> I had the same error, I think I solved my issue.

Have a look here:

[http://ubuntuforums.org/showthread.php?p=3119859#post3119859](http://ubuntuforums.org/showthread.php?p=3119859#post3119859)

Thanks for the reply.  

I tried to do the solution above but it didn't seem to work out.  :(  It won't let me select DOA.  :confused:

---

