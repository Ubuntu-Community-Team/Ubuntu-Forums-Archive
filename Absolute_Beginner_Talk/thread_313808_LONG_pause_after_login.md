---
title: "LONG pause after login"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2006-12-06
After I log onto my computer, there is a long (~5 minutes) pause before the splash screen and my desktop loads up. Aside from this pause, everything seems to work more or less as it should. 

Any suggestions?

Also, I think this may be related to the problem I'm having with WINE, described [here]("http://ubuntuforums.org/showthread.php?t=312635").

Thanks.

---

### Post by wpshooter on 2006-12-06
How much memory does your machine have & did you create a separate swap partition ?

---

### Post by sunexplodes on 2006-12-06
1.5 gb of memory, and yes, there is a 1.54GB swap partition.

I should have mentioned that this problem has only been happening for a few days, and I've been using this ubuntu install for a couple months.

---

### Post by taurus on 2006-12-06
What are the output of these two commands from a terminal?

```
df -h
free
```

---

### Post by sunexplodes on 2006-12-06
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  9.0G   25G  27% /
varrun                506M  180K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  144K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-28-386/volatile
/dev/hdd1              76G   21G   52G  29% /ddrive

```

```
 total       used       free     shared    buffers     cached
Mem:       1036088     901224     134864          0      23544     634840
-/+ buffers/cache:     242840     793248
Swap:      1614492          0    1614492

```

---

### Post by taurus on 2006-12-06
Everything looks to be normal to me!  What kind of filesystem do you use for /dev/hda1, /, anyway?

---

### Post by sunexplodes on 2006-12-06
ext3.

I actually have a feeling this is somehow related to networking. When I first started using ubuntu, I had similar (but shorter) pauses after login, and it turned out I had the wrong domain/workgroup name, and it was timing out trying to figure out the network. But I fixed that, it went back to normal.. Until now. I checked those settings, and they haven't changed.

---

### Post by sunexplodes on 2006-12-09
Bumping this because it is still happening.

---

### Post by taurus on 2006-12-09
So, you try to mount network files from /etc/fstab?  What if you put a # in front of those lines in /etc/fstab to comment them out and see if the problem's still there...

---

### Post by darco on 2006-12-09
My system slowed to a crawl and I couldnt figure out why. I had made two changes (installing xorg.edit and editing out network interfaces). I reverted back but still slow as a snail..from reading this post and commenting out my network files, everything is back to normal!!>.thxs

dr

---

### Post by sunexplodes on 2006-12-09
Which lines should i comment out? I wasn't aware any of those were network files.

---

### Post by sunexplodes on 2006-12-11
anybody?

---

### Post by taurus on 2006-12-11
A copy of your /etc/fstab would be nice!

```
cat /etc/fstab
```

---

### Post by sunexplodes on 2006-12-11
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /ddrive ext3 defaults 0 0

```

---

### Post by lumpki on 2006-12-11
Did you install a bunch of new fonts recently? You might try
```
sudo fc-cache -f
```
to force (-f) a rebuild of your font cache. It won't hurt anything, and it might help.

"fc-cache scans the font directories on the system and builds font information cache files for applications using fontconfig for their font handling"

---

### Post by sunexplodes on 2006-12-11
I don't think I've installed any fonts, but what the hell, i'll give it a shot.

---

### Post by sunexplodes on 2006-12-11
Yeah, sadly that one didn't do the trick. Thanks though.

---

