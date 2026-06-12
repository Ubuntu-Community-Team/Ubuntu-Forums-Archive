---
title: "How to get the keyboard backlight working on the Macbook Air"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by kosumi68 on 2008-06-17
I already posted this in the archives, but with modifications it might be of interest to all MBA users, so here we go:

[http://ubuntuforums.org/showpost.php?p=5200983&postcount=46](http://ubuntuforums.org/showpost.php?p=5200983&postcount=46)

---

### Post by _alex_ on 2008-06-17
Would you mind submitting this as a bug report along with your fix to launchpad?
It'd be nice to see this make it into the next set of patches :)

---

### Post by kosumi68 on 2008-06-21
I have submitted two bugfixes upstream, one for the F5/F6 problem ([http://bugzilla.kernel.org/show_bug.cgi?id=10947](http://bugzilla.kernel.org/show_bug.cgi?id=10947)), and one for the MBA detection problem ([http://bugzilla.kernel.org/show_bug.cgi?id=10948](http://bugzilla.kernel.org/show_bug.cgi?id=10948)). I frankly do not know how to speed up the release loop by applying patches to the ubuntu kernel. Please advice. :-)

---

### Post by _alex_ on 2008-07-12
Hello Henrik,

You could file a bug report with the respective patches at launchapd. Then you can send an email to the kernel-team mailing list ([https://lists.ubuntu.com/](https://lists.ubuntu.com/)). I've had success there before, with the patch making it into the kernel in a couple of weeks!

Alex

---

### Post by kosumi68 on 2008-07-13
Ok, I created two launchpad bugzillas for this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248230](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248230) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248238).

---

### Post by cyberdork33 on 2008-07-15
I think those patches are most appropriate to the vanilla kernel. They will filter down eventually. I can't say that they are likely high enough priority to make it into the Ubuntu kernel very soon. 

Also, when filing specific Mactel-related bugs. Try to add the "mactel-support" project. This is just a generic project that will help us track open bugs.

---

