---
title: "grub loading error 16 after install"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by timbuktu on 2006-07-08
Short story: getting grub loading error 16 after installing 
ubuntu 6 on PII 400 mhz, 500 meg ram, 15 gig HD
Live cd seems to work fine.

Long story:
Installed ubuntu first time and installation crashed at 98%. 
Tried to boot anyway and got grub loading errror 18.
Tried installing again and this time it went all the way to 100% - no crash so I re-booted optimistically and got got grub loading errror 16.
](*,) 

Not much of an advert for LINUX. I've had W2K and winxp
working fine on this machine - microsoft and apple would have gone bust a long time ago if installing was this much bother.
Anyone got any solutions ?

---

### Post by shoot2kill on 2006-07-08
sorry, wrong error code, thought it was 15

---

### Post by tonyr on 2006-07-08
[Grub Error Messages]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html") says
> 
16 : Inconsistent filesystem structure
    This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.


Did you md5sum check your install CD?  This could be caused by a
bad cd, among other things.

---

### Post by timbuktu on 2006-07-08
Did you md5sum check your install CD?  This could be caused by a
bad cd, among other things.[/QUOTE]

Is the filesystem of the hard disk an issue at all?
The disk was previously formatted to NTFS.

"md5sum check" - how do I do this?

---

### Post by tonyr on 2006-07-08
Yes, the HD filesystem is an issue, but figuring out what to do about it
is the first problem.  During installation it should have told you
(or asked you?) about formatting the partitions, so if that appeared
to work successfully that should not be a problem.

If you are working from a Windows system, there is a utility
***md5summer*** you can get [here]("http://www.md5summer.org/") to verify the iso image.

If you are working from a linux system, the program is **md5sum**.

If you still have the iso image file, you can run in a terminal
```

md5sum <image-file-name>

```

At the cd download site there is a file named MD5SUMS.TXT that contains
the checksums for all of the CDs.  Your md5sum result should match one of those.

The other issue for corrupt CDs is CD burn speed. The common 
recommendation is to burn at not more than 4x or 8x.  I think
you can run md5sum on the raw cd, too, but I don;t remember exactly how
to do that.


[COLOR="DarkRed"]EDIT: In Linux, this should work in a terminal
to check the CD directly
```

dd if=/dev/hdc bs=2k|md5sum -

```
where /dev/hdc is the cdrom drive with the install CD in it.
You might want to verify that device name. Look in
/etc/fstab to find out.[/COLOR]

---

