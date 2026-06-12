---
title: "Removing Windows Dualboot"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-09-28
Ok, so now I'm sticking with Ubuntu (go me:P \\:D/), how do I remove windows from my 250 gig, remove it from grub then copy ubuntu from my 40 gig to my 250 gig?

---

### Post by gruffy-06 on 2006-09-28
It might work. But I cannot guarantee it.

---

### Post by Donnut on 2006-09-28
> **gruffy-06 said:**
> It might work. But I cannot guarantee it.

Like he said, I would back up stuff you don't want to lose.  I haven't done oe of these, any suggestions?

---

### Post by aysiu on 2006-09-28
Why do you have to copy Ubuntu to the 250 GB drive? Why not just use GParted to delete the Windows partition and reformat it as Ext3. Then you can mount that partition using [this tutorial](http://www.psychocats.net/ubuntu/mountlinux).

---

### Post by Josh1 on 2006-09-28
> **aysiu said:**
> Why do you have to copy Ubuntu to the 250 GB drive? Why not just use GParted to delete the Windows partition and reformat it as Ext3. Then you can mount that partition using [this tutorial](http://www.psychocats.net/ubuntu/mountlinux).

I've got Windows running on it, if I format it won't it then make my bootup go AWOL? :???:

---

### Post by aysiu on 2006-09-28
Are you using Windows' boot loader or Grub to manage your dual boot?

---

### Post by dca on 2006-09-28
...or just migrate all your important data someplace safe and reinstall from scratch off of liveCD?  You may have to re-tweak your custom settings and such...  Well, nevermind, I guess w/ having to copy bookmarks and all that jazz it may be easier to just re-partition...

---

### Post by Josh1 on 2006-09-28
> **aysiu said:**
> Are you using Windows' boot loader or Grub to manage your dual boot?

Using Grub.

> **dca said:**
> ...or just migrate all your important data someplace safe and reinstall from scratch off of liveCD?  You may have to re-tweak your custom settings and such...  Well, nevermind, I guess w/ having to copy bookmarks and all that jazz it may be easier to just re-partition...

No thanks, I have over 5 days worth of installing and I don't really feel like doing it again.. ;)

---

### Post by gruffy-06 on 2006-09-28
I think he/she means copy Ubuntu from the external 40GB disk to the internal 250GB one. Or is it the other way round?](*,)

---

### Post by aysiu on 2006-09-28
If Grub is on the MBR, I think you can safely delete the Windows partition and not mess up booting Ubuntu. As long as you have a live CD handy, it shouldn't be too hard to [reinstall Grub](http://doc.gwos.org/index.php/Restore_Grub)... or [move Ubuntu to the 250 GB drive.](http://www.psychocats.net/ubuntu/partimage)

---

