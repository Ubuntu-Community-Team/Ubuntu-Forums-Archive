---
title: "Reverting to old version"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by covetous_kid on 2006-06-20
Hi,

I recently upgraded from ubuntu 5.04 to 5.10 but found that my crappy computer is too slow to run it productively. Can I revert to an old version? Would it be necessary to format my hard drive and re-install 5.04 from scratch? If so, how do I format my hard drive? Any help would be appreciated. Thanks in advance!

---

### Post by fritz_monroe on 2006-06-20
Have you tried installing XFCE?  It's supposed to be a little less hardware intensive than Gnome.  Might be worth a shot.

---

### Post by aysiu on 2006-06-20
I agree with fritz_monroe. 5.10 or 6.06 is not any more resource-intensive than 5.04.

It's all about your desktop environment and how many services you're running. ```
sudo aptitude update
sudo aptitude install xubuntu-desktop gksu bum
gksudo bum
``` Uncheck what you don't need. Log out. Session. XFCE. Log in.

---

### Post by covetous_kid on 2006-06-20
Thanks for the quick replies. I've never heard of XFCE before. How different is it from Gnome? 

From an educational point of view, I would still like to know how to format my hard drive and start over from scratch. Can someone provide instructions? Thanks!

---

### Post by aysiu on 2006-06-21
XFCE is a lighterweight desktop environment. It has fewer services and is ideal for computers with 128 MB of RAM or less. That's the main difference.

To start from scratch, just pop in the Ubuntu CD and select the "Erase entire hard drive" option.

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

Oh, if you're going to do a fresh reinstall, consider using the latest version: 6.06--Dapper.

---

