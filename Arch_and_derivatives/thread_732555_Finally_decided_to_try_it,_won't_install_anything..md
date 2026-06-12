---
title: "Finally decided to try it, won't install anything..."
date: 2008-03-23
forum: Arch and derivatives
---

### Post by Ripfox on 2008-03-23
Tried the Arch Core cd just now, stuck in an infinite loop saying it cannot install any of the packages after partitioning because it cannot find the DVD drive (that it booted from?)

Oh well, :lolflag:

---

### Post by eljoeb on 2008-03-23
The last time I had that problem the CD was a bad burn.  Have you tried another CD?

---

### Post by Ripfox on 2008-03-23
No I'm saying it PHYSICALLY will not find my optical drive. During initial boot process, it kept looping some error over and over again where it could not recognize the drive it booted from. The disk was working, must be some hardware detection problem...proboably some boot option I could stick in there but, meh...if a distro does something like this right off the bat I usually junk it :lolflag:

---

### Post by drcranium on 2008-03-23
...But did you check the MD5sum of your burn?

Probably isn't for you anyways.

---

### Post by Pogeymanz on 2008-03-23
This is going to sound silly because I'm no pro at Arch, or any other Linux...

Do you have two Cd-drives? Did you make sure to choose the right one when asked where to install stuff from?

What kind of disc are you using? CD-R? CD-RW? DVD? I always have the best luck with CD-R's. I bet if you're using a DVD, that could be causing some issues...

Or, like drcranium said, the disc might be f'd up. Try checking the MD5SUM or burning a new disc at a much slower speed.

---

### Post by Ripfox on 2008-03-24
I have tried several disks now and am quite familiar with the burn process (I burn my isos at 4x) I am a distro-hopper so it's necessary :lolflag:

Also: just one drive (it's a cdrw/dvdrom)

The problem occurs wayyy before it asks which medium to install from. It spits out an error in a continuous loop:

> ata2: port is slow to respond, please be patient
ata2: port failed to respond (30 secs)
ata2: SRST failed (status 0xFF)
ata2: SRST failed (err_mask=0x100)
ata2: softreset failed, retrying in 5 secs
ata2: SRST failed (status 0xFF)
ata2: SRST failed (err_mask=0x100)
ata2: softreset failed, retrying in 5 secs
ata2: SRST failed (status 0xFF)
ata2: SRST failed (err_mask=0x100)
ata2: reset failed, giving up

And about it "not being for me"

the only reason for that would be that it may not work on the particular computer I am trying to install it on...:popcorn:

---

### Post by fwojciec on 2008-03-24
New ISOs have just been released for testing -- maybe they would work better on your hardware (since the kernel on the new ISOs is more recent):

For more info and download links see this: [http://bbs.archlinux.org/viewtopic.php?id=45897]("http://bbs.archlinux.org/viewtopic.php?id=45897")

---

### Post by MONODA on 2008-03-24
arch rocks, go to the forum, it's pretty good, post the same problem there.

---

