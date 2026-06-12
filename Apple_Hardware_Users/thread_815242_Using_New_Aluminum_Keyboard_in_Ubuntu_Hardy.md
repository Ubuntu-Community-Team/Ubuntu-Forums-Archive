---
title: "Using New Aluminum Keyboard in Ubuntu Hardy"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by frascelly on 2008-06-01
I am using the new mac keyboard, aluminum, wired, not bluetooth. Even with the keyboard layout set as US apple macintosh, none of the keys will type, except for the "uiopjkl;nm,." keys, and they don't type the right letters, they just type numbers, even though they are letter keys...

The weird thing is the eject and volume keys work, but they are the only keys that work properly.

How can I fix this?

---

### Post by cyberdork33 on 2008-06-01
do F6 twice to switch numlock off (which might actually be Fn+F6)... The kernel thinks you are using a Macbook Pro keyboard. This is a bug and a fix is in the works.

Please make sure to search before asking questions, there are plenty of posts related to this:
[http://ubuntuforums.org/showthread.php?t=798748](http://ubuntuforums.org/showthread.php?t=798748)
[http://ubuntuforums.org/showthread.php?t=771151](http://ubuntuforums.org/showthread.php?t=771151)
[http://ubuntuforums.org/showthread.php?t=780850](http://ubuntuforums.org/showthread.php?t=780850)

---

### Post by theolster on 2008-06-04
> **cyberdork33 said:**
> This is a bug and a fix is in the works.

I spotted this in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887").> Patch spotted in upstream kernel 2.5.26-rc4

[http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fincr%2Fpatch-2.6.26-rc3-rc4.bz2;z=276](http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Ftesting%2Fincr%2Fpatch-2.6.26-rc3-rc4.bz2;z=276)
Does anyone know how long a rc kernel takes to get into the Ubuntu repos?  I'm assuming we won't be seeing it for another six months or so.  If so is there a patch (or something) we can apply to get the correct functionality sooner?

---

### Post by cyberdork33 on 2008-06-04
> **theolster said:**
> I spotted this in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887").Does anyone know how long a rc kernel takes to get into the Ubuntu repos?  I'm assuming we won't be seeing it for another six months or so.  If so is there a patch (or something) we can apply to get the correct functionality sooner?Ubuntu is currently using 2.6.24 so it may be a long while. Maybe it will be in 8.10.

The bug report is the best way to communicate these issues. This is not a serious problem since you can easily switch modes by hitting F6, and thus will likely not warrant a change before 2.6.26

You will notice that the bug is marked as "triaged"

---

