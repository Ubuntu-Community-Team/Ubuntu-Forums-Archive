---
title: "Error message"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Lars Hjalte on 2007-02-06
I've been running DOS on my computer for almost fifteen years but lately decided to try out linux and was told that Ubuntu was supposed to be "beginner friendly". Therefore I read litteraly tons of guides and then downloaded the 6.10 version iso from ubuntu's home page.

After burning it onto a CD I tried to boot  from it. No matter which menu option I choose the computer loads approximatly 37% of the linux kernel and then declares an I/O error and displays the followning text:

isolinux: Disk error 80, AX=4280, drive AC

I haven't been able to figure this message out and are really beginning to become quite frustrated. Even tried downloading the 6.06 version with the same result. Perhaps it's notable that my computer is not brad new. 450 MHz processor and 3x128 Mb of RAM. The CD-reader seems operational as can read all files on disc from dos mode. Unfortuantely the installationprogram is unexecutable from DOS.

---

### Post by ghandi69_ on 2007-02-06
Well it definitely sounds like a disc error, but since you've tried two different installs on two different discs, thats not it either.

There is a "check disc for errors" option before boot, have you tried that?

---

### Post by Lars Hjalte on 2007-02-06
Yep, tried it. Turns out you need to load the linux kernel in order to check the disc and that's when disaster strikes.

---

### Post by Brunellus on 2007-02-06
Burn the ISO at the slowest possible speed.  IF all else fails, contact your local Linux User Group--someone will be able to sling you a known-good Ubuntu CD.

If that doesn't work, you might need to investigate some of the more exotic installation options:

[https://help.ubuntu.com/community/Installation?highlight=%28install%29](https://help.ubuntu.com/community/Installation?highlight=%28install%29)

---

### Post by Lars Hjalte on 2007-02-06
I've already written three cds. 1 edgy at 52x, one dapper drake at 52x and one edgy at 8x. That's as slow as will go. I'll start asking around for a working cd first thing tomorrow. Thanks for the replies and I hope I won't have to go too deep into advanced linux usage just yet.

---

### Post by Lars Hjalte on 2007-02-07
Ut would seem as if the problem is in the hardware. All discs are readable from a multitude of other computers. Is there perhaps an installation method excluding removable media?

---

### Post by Brunellus on 2007-02-07
> **Lars Hjalte said:**
> Ut would seem as if the problem is in the hardware. All discs are readable from a multitude of other computers. Is there perhaps an installation method excluding removable media?
You'll have to resort to one of the more exotic install options in the link I posted above.  At least one should allow you to install via floppies and an active internet connection.  Another is a netboot install method.  Both require some other computer to host the installation data.

---

### Post by Lars Hjalte on 2007-02-08
Ok. Finaly got this to work. Apparently only the master outof my two cdds was defect and the slave was perfectly fine but not able to boot. So I did parts of the floppy installation routine and booted from the slave cd-drive instead. Worked like a charm. To bad I ran into other difficulties. Anyhow that's another subject. Problem solved.:)

---

