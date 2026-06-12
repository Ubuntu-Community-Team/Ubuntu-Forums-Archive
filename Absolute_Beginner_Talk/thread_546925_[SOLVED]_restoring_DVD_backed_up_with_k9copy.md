---
title: "[SOLVED] restoring DVD backed up with k9copy"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by michael37 on 2007-09-09
So, I backed up my DVDs using k9copy, and rightly so, just before my kid destroyed one of the original DVDs.  

Now, I have a dumbest question.  How do I burn them back?  I tried burning a DVD with GnomeBaker as "data DVD" (the only DVD option I have), but it doesn't play in my DVD player.  Maybe file order issue?

---

### Post by distroman on 2007-09-09
"Gnomebaker > Tools > Burn DVD Image" should do it.

---

### Post by michael37 on 2007-09-09
> **distroman said:**
> "Gnomebaker > Tools > Burn DVD Image" should do it.

That option looking for .iso files.  After k9copy, I have the VIDEO_TS and AUDIO_TS directories and a bunch of .VOB files.

---

### Post by distroman on 2007-09-10
Ohh well,,,don't know if gnomebaker can do .vob files.

You can do the following one of the two things and then some I imagine.
1.
> On-the-fly, one-step VIDEO burning - growisofs

Make sure that your dvd/ directory contains the VIDEO_TS directory and that it is written in UPPERCASE, otherwise it will not work.

Here's the command you need to run to create the dvd on-the-fly using growisofs:

$ growisofs -dvd-compat -Z <device> -dvd-video -V "<volumelabel>" dvd/

Replace <device> with your dvd device (for example /dev/dvd), <volumelabel> with the volume label you want on the disc and dvd/ with the actual name of the directory with the contents to burn. Note that the indicated directory will be the root directory of the dvd.

For more general information on writing data to DVD+RW, refer to the dvd+rw-tools web page.

2.

If you have a folder on your desktop called burn containing your VIDEO_TS and AUDIO_TS directories.

cd Desktop/burn
```
mkisofs -dvd-video -o dvd.iso dvd/
```
Creates a iso file ready for gnomebaker.

---

