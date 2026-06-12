---
title: "Long boot time, normal?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-01-28
I have a completely fresh instalation of ubuntu and everytime I turn on my computer the screen goes black for over 2min, then it goes to the login screen.  Now, I could live with this (I guess) but the worst part is that when my comp goes to hibernate or suspend, when I try and activate it again the screen goes black and stays black.  I have to restart my comp (improperly) to use it again.

I think it's worth mentioning that I have a "restricted driver" called "Atheros Hardware Access Layer (HAL)"  not sure what a restricted driver is but it sounds bad.


Any help?

---

### Post by spiderbatdad on 2008-01-28
for me the problem was in a file called /etc/usplash.conf```
gksu gedit /etc/usplash.conf
```
my max screen resolution is 1024x768, so I set x = 1024 and y = 768

save...reboot...problem solved.

---

### Post by h0ax on 2008-01-28
Alternatively, you can turn off the splash completely.
This is what I did.
```
sudo gedit /boot/grub/menu.lst
```
Then find the line that you boot from, toward the bottom and delete "splash" from the end of the line; or change it to "nosplash"
It worked for me w/ an 8800 GTX nVidia card.

---

### Post by Bruce H. McCosar on 2008-01-28
> **phoenix5002 said:**
> I think it's worth mentioning that I have a "restricted driver" called "Atheros Hardware Access Layer (HAL)"  not sure what a restricted driver is but it sounds bad.

Yeah, it does, doesn't it?  Sort of like it's R-rated.  "Loading module Sam Kinison..."

Anyway, it's nothing too bad.  It just means the driver is closed source.  The Ubuntu developers can't look inside and see what's wrong if something goes wrong.  So before you plunk some black box of software on your system, they point out they have no control over what the module does or doesn't do, and so can't be responsible if it acts goofy.

I've been going through the same thing for years, since my computer uses the proprietary NVIDIA driver.  On the other hand, I've only had once incident where the driver gave me a problem -- refusing to compile on my old Debian installation.

That's why I'm with Ubuntu.  I've compiled enough kernels and dug through enough module documentation to get things to work.  When building a working linux realtime kernel came along, I said forgetaboutit and switched over.  I'm content to let someone brilliant figure it out and download the working model.   :D

So no, I wouldn't necessarily blame the restricted driver, and that's where my expertise ends.  But it was probably good detective work to point it out, just in case.

---

### Post by phoenix5002 on 2008-01-28
My screen resolution is 1280x800, so I set it to x=1280 y=800 and rebooted and I still it's still exactly the same.

The worst part is that I can't let my computer go to susped or hibernate, meaning I can't close my laptop scree or I'll have to turn my comp off improperly to fix it.

---

### Post by erfahren on 2008-01-28
actually, there was a step missing in that earlier post about editing usplash.conf

see: [http://ubuntuforums.org/showpost.php?p=3741687&postcount=21](http://ubuntuforums.org/showpost.php?p=3741687&postcount=21)

---

### Post by spiderbatdad on 2008-01-28
yeah I've never had to update usplash-theme after changing the settings to solve my long boot time hang. There are some threads regarding your suspend hibernate issues...I haven't had those...luckily.  this link:[http://www.linux.com/feature/54610](http://www.linux.com/feature/54610)   looks a little intimidating, but I have seen easier fixes, reported to have worked. I would suggest google it: Ubuntu suspend hibernate <insert your model here>

---

### Post by spiderbatdad on 2008-01-28
please try 1024x768 and save...this will not affect your desktop display resolution after gdm starts...as far as i know...

---

### Post by SyCo123 on 2008-01-28
removing splash from /boot/grub/menu.lst as suggested also worked for me.

---

### Post by ubuntu-freak on 2008-01-28
I had this problem cos the disk check was really slow checking the windows partition. If you have a windows partition try my how-to
 
[http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214)
 
Nathan

---

