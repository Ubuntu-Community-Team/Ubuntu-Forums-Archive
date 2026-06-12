---
title: "Data DVD??"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by xxix on 2007-08-08
Okay... so I'm REALLY new to this, but I love it!

I would just use Ubuntu, but I need XP for my Zune and Q. (Don't ask...)

Either way, I'm trying to load some stuff onto a DVD, but it always fails. I've use Gnomebaker and K3d as these were suggested my most.

Any ideas as to what could be the problem? It worked fine on Vista a week ago.

These are the errors I get from Gnomebaker:

> 
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p Christian Delfin -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-xxix/gnomebaker-WA7OWT | builtin_dd of=/dev/hdc obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/hdc: pre-formatting blank DVD+RW...
/dev/hdc: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=10h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

k3b tells me there is no medium present and then ejects...

Every time I pop it back in it tells me it's a blank DVD. Any help? Or is it just a hardware issue?

---

### Post by ramjet_1953 on 2007-08-09
Are you sure that you are using the correct media?

There are two types of DVD RW disks.  +RW and -RW

Some drives only work with one type.

Read-up on the capabilities of your particular drive.

The error messages tend to indicate that you may have this problem.

Regards,
Roger :cool:

---

### Post by xxix on 2007-08-09
I'm using DVD+RW. From the same pack that I used about a week ago. I never burnt an .iso or data onto a DVD so I'm figuring I'm doing something wrong in that aspect. I usually just burn videos.

And like I said before it worked a week ago on XP.

---

