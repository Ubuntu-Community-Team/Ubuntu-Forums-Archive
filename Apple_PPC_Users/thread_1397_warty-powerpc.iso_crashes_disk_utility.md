---
title: "warty-powerpc.iso crashes disk utility"
date: 2004-10-20
forum: Apple PPC Users
---

### Post by dspivey on 2004-10-20
I'm trying to burn the ISO, but Disk Utility keeps crashing!  Any ideas??

Thanks in advance!

---

### Post by Castaa on 2004-10-20
[quote=dspivey]I'm trying to burn the ISO, but Disk Utility keeps crashing!  Any ideas??

Thanks in advance![/quote]

So a MD5 check sum on the iso image?  It could be corrupt.  Or if you can't do that, re-download it and reburn it to a disk?

---

### Post by guido on 2004-10-21
[quote=dspivey]]I'm trying to burn the ISO, but Disk Utility keeps crashing!  Any ideas??
[/quote]

I had the same trouble but Toast Titanium burnt the image without problems.

---

### Post by diabolo on 2004-10-25
I'm having the same problem. I downloaded the .iso last night. It's making Disk Utility crash, here's what I get in the system.log:

Oct 25 09:48:08 localhost crashdump: Unable to determine task_t for pid: 369 name: Disk Utility Unable to determine CPSProcessSerNum pid: 369 name: Disk Utility

 :(

---

### Post by diabolo on 2004-10-25
Update: I got the iso image to burn with xcdroast on a Yellow Dog 3.0.1 system. It worked fine, no probs.

Unfortunately I have no idea why Disk Utility was crashing; the error stuff written to the log files makes no sense to me.

---

### Post by rono64 on 2004-10-30
I was having this problem and it was driving me nuts.
There is nothing wrong with the ppc iso, it's the apple disk utility.

I downloaded and installed a utility called YuBurner.

[http://hp.vector.co.jp/authors/VA027835/index_e.htm](http://hp.vector.co.jp/authors/VA027835/index_e.htm)

It worked fine, sometimes the verification says it does not work, but the disc is fine.

---

### Post by Huxley on 2004-11-04
Hi

I have the same problem with the warty-release-install-powerpc.iso.  Disk Utility crashes with the iso (I have a log if interested).  YuBurner will burn the iso but verification fails after burn.  Thanks for the link to this great app.

---

### Post by Mikel on 2004-11-04
I suggest you guys try this app out, its an excellent gui tool for many cd burning terminal commands, in fact its what i used to burn the ubuntu iso, but it looks pretty promising for other stuff too. A perfect companion for toast.

[http://www.versiontracker.com/dyn/moreinfo/macosx/16799](http://www.versiontracker.com/dyn/moreinfo/macosx/16799)

Now all I need is to get Ubuntu up and running on my 17 inch PowerBook to be fully happy hehe  ;-) Isnt there anyone here with one of these PowerBooks? Have fun!

---

### Post by daniels on 2004-11-04
It's a known problem with OS X's disk utility, and there's nothing we can do -- the only thing I can suggest is to use some of the apps suggested by others.

---

### Post by Huxley on 2004-11-04
Thanks.

Used the  MissingMediaBurner to burn the iso - no problems with generic mmc and Pioneer 107D.

Installed on my Powerbook G3.

---

### Post by iant on 2004-11-11
i had the same problem so used firestarter (this afternoon, in fact!).  it worked well.
[http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter)

---

### Post by dspivey on 2004-11-11
thanks for all your replies.  i used toast and it works fine for me.  it's very odd that i have never had a problem burning other iso's from disk utility.  i even burned the i386 warty iso from disk utility and it works fine.  the only iso i have ever had trouble burning is the ppc warty iso.  i've burned iso's from every major distribution (knoppix, mandrake, fedora, yellow dog, suse, mepis, and now ubuntu) for several platforms, and the ppc warty iso is the only one i've ever experienced this issue with.  seems odd that it's a "known issue" with disk utility in light of this info.  what's different about the warty ppc iso than say, the yellow dog iso's?

---

### Post by neomantra on 2005-04-08
the same problem seems to exist with ubuntu-5.04-live-powerpc.iso  (Hoary).

---

