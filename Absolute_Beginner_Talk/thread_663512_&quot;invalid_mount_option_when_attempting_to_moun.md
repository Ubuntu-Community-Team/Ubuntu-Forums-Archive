---
title: "&quot;invalid mount option when attempting to mount the volume 'UDFVolume' &quot;"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by vamsibethapudy on 2008-01-10
this is what i get when i try to automount a dvd burnt in vista.
someone please help!!
this is what i get in system log.
[15379.292000] UDF-fs: No VRS found
[15380.900000] Unable to identify CD-ROM format.

---

### Post by JohnLM_the_Ghost on 2008-01-12
There must be something fishy about the way Vista burns DVDs.
There could be some non-standard UDF format maybe.

Anyways you would want to try to mount it manually:
```
sudo mount -r -t udf /dev/cdrom /media/cdrom
```

Only be sure it is really an UDF DVD not ISO9880

also you may want to change /dev/cdrom if you have more than one CD-ROM (to /dev/scd0 perhaps) and /media/cdrom for custom mount folder.

I really don't know if this will help, cause automount should probably do the same thing.

refer to ```
man mount
``` for more info about the MOUNT command

---------------

I had just stumbled on some UDF tool while browsing internet.
It is probably nothing Ubuntu doesn't already have, but you may want to take a look if you cant sort it out.
[http://sourceforge.net/projects/linux-udf/](http://sourceforge.net/projects/linux-udf/)

be warned however, I'm just giving you link. I haven't tried it and don't recommend you to try unless you are really sure.
It claims to patch the kernel and that makes it extra dangerous.

---

### Post by rkd on 2008-01-14
Some quick Google searching turns up some claims that Vista writes DVDs using UDF 2.5 format, and XP can't read them. It could be that Ubuntu also is not yet able to recognize UDF 2.5. I saw some pages talking about patches for Linux on the PS3 to support UDF 2.5, but nothing for Linux on the PC. I didn't look very long, though.

If you can burn a replacement DVD, try looking for some setting in the Vista application that will let you tell it not to use UDF 2.5.

If you can't burn a replacement DVD, look for instructions to add UDF 2.5 support to Ubuntu. There may be an easy way to do that, but I don't know anything about it.

I should emphasize that I have no proof that this is the explanation of the problem you are having. It just seems like a likely case. There might be something completely different that is preventing Ubuntu from recognizing your DVD.

---

### Post by vamsibethapudy on 2008-01-18
thanks guys for ur valuable suggestions & research:)

---

