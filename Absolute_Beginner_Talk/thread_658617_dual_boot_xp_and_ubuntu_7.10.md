---
title: "dual boot xp and ubuntu 7.10"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by mjheagle8 on 2008-01-04
I am looking to install ubuntu 7.10 via the cd.  I use the option of manually editing the partion tables.  I was confused by gpart in 7.10 (it worked fine for me in 6.06).  If I want the system to be dual boot with xp, do i assign linux to make the partitions /windows, do not use, or what?

---

### Post by iris-n on 2008-01-04
To do that, you just don't mess with the windows partitions. I'm assuming it is previously installed. If not, do it, windows has a bad habit of screwing grub.

/windows would be a mount point, that is, a location in your ubuntu file tree where you can view windows's files, if you set it to that, it doesn't affects the setting windows use for itself.

---

### Post by overdrank on 2008-01-04
> **mjheagle8 said:**
> I am looking to install ubuntu 7.10 via the cd.  I use the option of manually editing the partion tables.  I was confused by gpart in 7.10 (it worked fine for me in 6.06).  If I want the system to be dual boot with xp, do i assign linux to make the partitions /windows, do not use, or what?

Hi and this link may help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Good luck!

---

### Post by eternicode on 2008-01-04
> **mjheagle8 said:**
> If I want the system to be dual boot with xp, do i assign linux to make the partitions /windows, do not use, or what?

If you want to access your windows files from within linux, assign it a mount point (such as /media/windows or /windows).

If you just want to dual-boot, without worrying about cross-platform-access (which I believe is very rare among dual-booters), then tell linux not to mount it ("no mount point")

Whatever you do, ***don't check the "format" checkbox*** for your windows partition!

---

### Post by rcsarver on 2008-01-04
yes, definitely install windows first if you haven't.

you can leave the windows as /windows and you will have easy access to the windows files from ubuntu

OR

you can edit the table so the mount point has nothing in it and you will have slightly less easy access to windows files from ubuntu. this is probably more secure, but either way is fine

---

