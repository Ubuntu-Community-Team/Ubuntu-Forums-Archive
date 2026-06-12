---
title: "Forgotten Ubuntu 6.06 Password"
date: 2006-09-02
forum: Apple PPC Users
---

### Post by Lurcher on 2006-09-02
Is there a way to set a new password for Ubuntu 6.0.6?  I had a problem with Ubuntu 6.0.6, and so I was unable to log in for three or four weeks.  On and off though, I tried to fix the problem that started when I tried to uninstall Evolution (which I may have solved).

Now the thing is that I don't recall the password I used to log in because I have not used it in so long (all my attempts at repair were done using the command line).

Is there a way that I can reset it?  If I can't do that, I would like to reinstall and choose another.


Thank for the assist.

Btw, I forgot to mention that I am working with an iMac G3/500MHz.

---

### Post by cilynx on 2006-09-03
Boot into the LiveCD.  Fire up a console, get root, mount your real system somewhere, chroot to your real filesystem, set your password.
```

sudo -s
mount /dev/hda1 /mnt
chroot /mnt
passwd

```
Physical access is a security professional's worst nightmare.
Be sure to change things if necessary to reflect your setup.

Good Luck

---

### Post by Lurcher on 2006-09-03
When I try to boot into the CD I get this message: cd:2,/install/powerpc/vmlinux:  Unknown or corrupt filesystem.

Suggestions are so welcome:biggrin:

---

### Post by linear on 2006-09-03
See if you can boot from an alternate install CD. One of its features is "Rescue a broken system", which will allow you to chroot to your filesystem.

---

### Post by Lurcher on 2006-09-04
I have to try to get another (which kinda sucks because it seemed to take so long to get the one I do have).

Oh, well...

---

