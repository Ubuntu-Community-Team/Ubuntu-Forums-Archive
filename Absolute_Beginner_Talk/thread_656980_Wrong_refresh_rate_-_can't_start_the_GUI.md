---
title: "Wrong refresh rate - can't start the GUI"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by chopsuwe on 2008-01-03
I'm going pretty well. After 6 weeks trying to get Ubuntu installed I finally got it working this morning only to break it this afternoon. 

I am using a Viewsonic E70 17" CRT monitor on S3 Savage onboard graphics. This can easily do 85HZ @ 1024*768, which is what I want. 

Ubuntu was working but would only use a refresh a rate of 61Hz. 
I tried "sudo dpkg-reconfigure xserver-xorg" and left all the selections to their default but it didn't make any difference. 
I tried "sudo dpkg-reconfigure xserver-xorg" again and this time selected higher resolutions and changed the refresh rate to up to 60-120Hz. 
Now I can't get into Ubuntu as it brings up an error message saying that it can't start the graphical interface. 

How do I change the resolution and refresh back to something the monitor can handle?

---

### Post by yopnono on 2008-01-03
Have you tried.
sudo dpkg-reconfigure -phigh xserver-xorg

---

