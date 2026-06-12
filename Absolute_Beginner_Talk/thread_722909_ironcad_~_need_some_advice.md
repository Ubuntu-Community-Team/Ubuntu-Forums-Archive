---
title: "ironcad ~ need some advice"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by thaltek on 2008-03-12
converted to 7.10 within the last week.


[http://www.ironcad.com/](http://www.ironcad.com/)

~requiered for school
~tech support says linux is unsupported (why wasn't i supprised?)
~have been poking around with wine to no avail 


its not critical to have ironcad running on my desktop. however, it would help me lots as the desktop is my "fast system" and ironcad being a cad system eats up cpu space and ram space...... 

:confused: any advise from people who would know would really help....

---

### Post by Hospadar on 2008-03-13
Well you really have two options to try and get this running.  One is wine, which I assume you've tried (And it doesn't work?).  The other option is to set up a windows virtual machine on your linux desktop.  This can be tricky and time consuming, but once you get it set up, you will probably be able to get your software working.  For a vm setup you'll probably use "vmware."  I would look in the community documentation (in my sig) for a tutorial on how to set that up.


Also, for wine, I imagine that cad software requires 3d acceleration, do you have 3d working on your machine?

The only other option would be to dual boot.  This is really pretty easy and safe.  Use gparted from the livecd to shrink your linux partition(s), Install windows to the free space, and then re-install grub from the livecd (If you google "ubuntu grub reinstall" I'm sure you'll find a guide for that, it's pretty easy)

If it were me, I would just make a little windows installation and go that route unless I needed a vm for more than one app.

---

### Post by thaltek on 2008-03-15
> **Hospadar said:**
> Well you really have two options to try and get this running.  One is wine, which I assume you've tried (And it doesn't work?).  The other option is to set up a windows virtual machine on your linux desktop.  This can be tricky and time consuming, but once you get it set up, you will probably be able to get your software working.  For a vm setup you'll probably use "vmware."  I would look in the community documentation (in my sig) for a tutorial on how to set that up.


Also, for wine, I imagine that cad software requires 3d acceleration, do you have 3d working on your machine?

The only other option would be to dual boot.  This is really pretty easy and safe.  Use gparted from the livecd to shrink your linux partition(s), Install windows to the free space, and then re-install grub from the livecd (If you google "ubuntu grub reinstall" I'm sure you'll find a guide for that, it's pretty easy)

If it were me, I would just make a little windows installation and go that route unless I needed a vm for more than one app.
i am still fairly green to this linux endevour .... i was able to get ironcad halfway through the install under wine but now that you mention the 3d accelerator that might be what halted the install... as for the whole virtual machine.....*hesitates* being somewhat new to how linux works i feel accomplished in saying i got compiz desktop working the way i wanted in 3 hours....... yes i have a cube of my own.....

image-> [http://i12.photobucket.com/albums/a241/thaltek/Screenshot-1.png](http://i12.photobucket.com/albums/a241/thaltek/Screenshot-1.png)

---

