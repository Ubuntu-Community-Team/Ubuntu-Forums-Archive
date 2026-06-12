---
title: "OS fail and harddisk problems"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by infraK on 2008-02-09
i installed ubuntu on an 80 gb hard disk and used the default partitioner out of 2 + swap... it installed fine. After, I went to install windows xp and I booted from the windows cd.... but changed my mind and ddnt install windows. 

then I restarted and when I booted from the hard disk what it said was 'error:operating system couldnt load' or wasnt found or something. Then I tried to install windows but it said that there was an I/O error (this after i formatted in ntfs ofcourse).... does anyone kno anything bout this :S? any help appreciated

---

### Post by Paqman on 2008-02-09
If you install Windows second, it may have trashed your Ubuntu install, because the Windows installer does not play well with other operating systems. Then when you bailed out of the Win install you were left without a working OS.

I'd boot up into a LiveCD, run Gparted and wipe out everything and start from scratch. It might be heavy-handed but it only takes a few minutes to delete everything and reformat.

---

### Post by jan quark on 2008-02-09
you can try booting from the from the super grub disc and restore the linux grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

but I don't really know if that is enough in your case

but worth a try

---

### Post by infraK on 2008-02-09
thx... i just restarted and booted from ubuntu and it installed just fine....

btw... is there a difference between the format that the ubuntu installation did and the format that windows xp boot cd does? (apart from the no of partitions and system type)

---

