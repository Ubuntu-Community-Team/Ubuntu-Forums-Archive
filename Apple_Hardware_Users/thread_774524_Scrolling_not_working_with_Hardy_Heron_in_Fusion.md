---
title: "Scrolling not working with Hardy Heron in Fusion"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by ozz314 on 2008-04-29
Hello!

I just installed Ubuntu Hardy Heron on my MacBook via VMware Fusion (1.1.2).  Everything seems to be working great except I can't scroll using the two-finger trackpad gesture nor by using an attached USB mouse with a scroll wheel.

This is a minor annoyance, but does anyone have a fix?  Any help would be appreciated.  Thanks!

---

### Post by rjpa on 2008-05-08
Yeha I would also like to know how to fix this annoying error?

- RJPA

---

### Post by cyberdork33 on 2008-05-08
did you install vmware tools? also you might check the [virtualization forum]("http://ubuntuforums.org/forumdisplay.php?f=308").

---

### Post by rjpa on 2008-05-08
> **cyberdork33 said:**
> did you install vmware tools? also you might check the [virtualization forum]("http://ubuntuforums.org/forumdisplay.php?f=308").

Yes I did install the VMWare Tools, but nothing works. Any one who knows how to get Shared Folders to work?

- RJPA

---

### Post by ozz314 on 2008-05-08
> **rjpa said:**
> Yeha I would also like to know how to fix this annoying error?

- RJPA

I didn't find the solution, but I do have a workaround.  Instead of using Fusion use [VirtualBox]("http://www.virtualbox.org/") which is open source.

After installing VirtualBox the scrolling worked.  However, my resolution was set to 800x600.  To fix that follow these instructions [here]("http://ozz314.wordpress.com/2008/05/06/ubuntu-resolution-fix-using-virtualbox-on-macbook/").

In regards to file sharing, I haven't figured that part out.  I think the simplest way is to create a samba share.  However, VirtualBox doesn't support bridged networking out of the box, so I'm not sure how to do that.  Anyone else able to setup a samba share from guest Ubuntu to Mac Host with VirtualBox?

---

