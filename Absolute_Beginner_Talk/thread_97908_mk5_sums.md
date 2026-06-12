---
title: "mk5 sums"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by tay on 2005-12-01
Can someone give me a how to on how to check mk5sums on files downloaded.   My  breezy upgrade failed because i was missing some files, so i guess that that file was'nt all there.

---

### Post by jeffjanzen on 2005-12-02
you're writing "mk5 sums", but i think you're talking about m*d*5 sums, that is, MD5 Checksums.  you can check md5sums in windows with a small program that you can get from any one of these URLs:
[http://etree.org/cgi-bin/counter.cgi/software/md5sum.exe](http://etree.org/cgi-bin/counter.cgi/software/md5sum.exe)
[http://theopencd.sunsite.dk/md5sum.exe](http://theopencd.sunsite.dk/md5sum.exe)
[http://www.people.virginia.edu/~dpc2a/cdr/md5sum.exe](http://www.people.virginia.edu/~dpc2a/cdr/md5sum.exe)
[http://openwebmail.lagmonster.org/download/redhat/archive/md5sum/md5sum.exe](http://openwebmail.lagmonster.org/download/redhat/archive/md5sum/md5sum.exe)
[http://www.2bright.net/download/md5sum.exe](http://www.2bright.net/download/md5sum.exe)
[http://downloads.activestate.com/contrib/md5sum/Windows/md5sum.exe](http://downloads.activestate.com/contrib/md5sum/Windows/md5sum.exe)
you need to copy this executable to the directory where the iso image is located, then open a command line ("command prompt" or "MS-DOS prompt"), navigate to the folder where your ISO and the md5sum.exe program are, and type:
```
md5sum ubuntu-5.10-install-i386.iso
```
(or substitute the name of your iso in there, if it doesn't match.)
it might take a while to calculate the md5sums, a couple minutes, maybe.
if you're having trouble navigating the file system at the DOS command line, just let me know the exact locations of the files on your hard drive, and i can walk you through that, too.

edit: here's a howto that may be helpful, though it just says pretty much what i already wrote:
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)

---

### Post by aysiu on 2005-12-02
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by Psquared on 2005-12-06
I am having some of the same problems. md5sum checks out both on the download and on the CD, but the install fails.

I did notice something though. When I made my .iso CD it puts a bunch of files on the CD. I was under the impression that when you create an .iso you are creating an image and there should be only one file. I have 8 directories and 3 files.

.disk
dists
doc
install
isolinux
pics
pool
preseed
md5sum
readme
ubuntu

Is that correct?

---

### Post by john_c on 2005-12-06
I checked an older warty install disk (don't have a breezy one handy to look at) and it also has similar files and directories to the ones you mention.  The iso image contains all of these and they show up once burned on to the cd.

Good Luck,

John_c

---

### Post by Joe_CoT on 2005-12-06
[QUOTE=Psquared]I am having some of the same problems. md5sum checks out both on the download and on the CD, but the install fails.

I did notice something though. When I made my .iso CD it puts a bunch of files on the CD. I was under the impression that when you create an .iso you are creating an image and there should be only one file. I have 8 directories and 3 files.[/QUOTE]

As Leo Laporte once explained, an image file is like instant oatmeal. you wouldn't just put instant outmeal in a bowl and eat it, would you? It needs hot water.

That's what the cd burning program did to your Ubuntu disk. if it burned the file to the disk, it've been useless. An image file is a file that contains all the data exactly the way it's supposed to be burned (important in this case because it's a bootable cd; if you just put those files on a cd, it wouldn't be), a snapshot (that's why it's called an image) of the cd it was made from.

If your md5 sums are correct, then there shouldn't be a problem with the image. The problem could be 1) the disk (could it be scratched? have you tried it using a different cd-rom drive?), or 2) the install itself. when did the upgrade fail? did it fail when it restarted to install "additional packages"? did it fail when trying to update from the ubuntu repositories? or did it fail when the upgrade was simply copying files over?

---

### Post by Psquared on 2005-12-06
[QUOTE=bobfnordman]As Leo Laporte once explained, an image file is like instant oatmeal. you wouldn't just put instant outmeal in a bowl and eat it, would you? It needs hot water.

That's what the cd burning program did to your Ubuntu disk. if it burned the file to the disk, it've been useless. An image file is a file that contains all the data exactly the way it's supposed to be burned (important in this case because it's a bootable cd; if you just put those files on a cd, it wouldn't be), a snapshot (that's why it's called an image) of the cd it was made from.

If your md5 sums are correct, then there shouldn't be a problem with the image. The problem could be 1) the disk (could it be scratched? have you tried it using a different cd-rom drive?), or 2) the install itself. when did the upgrade fail? did it fail when it restarted to install "additional packages"? did it fail when trying to update from the ubuntu repositories? or did it fail when the upgrade was simply copying files over?[/QUOTE]

OK, I understand the ISO now.

My install fails when loading the base file system - just after the partitioning step. I get a red screen which just says that the install failed due to a corrupt file on the disk. It would allow me to continue, but what would be the point?? I would say it copies about 30% of the base file system before it fails. I have tried 3 times with the same disk (deleting and then creating new partitions each time) and it stops at the same point. I had no trouble installing Warty and I did a dist-upgrade to Hoary and then to Breezy. I fooled around with Breezy a little too much so I decided to do a fresh install. Now I can't.

---

### Post by Psquared on 2005-12-08
Interesting followup. I ran the disk check that is part of the installer and it told me something was wrong with the ISO.

I went back and downloaded it again and this time the download was much larger than before. Obviously my first download was corrupt.

I have not tried to install the new ISO yet as I have been fooling around with Mandrika - but I think it will work this time.

---

### Post by ed_d on 2005-12-08
Also, try writing at a slower speed too, that sometimes helps

---

