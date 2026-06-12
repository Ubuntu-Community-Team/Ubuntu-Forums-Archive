---
title: "Can I upgrade Ubuntu to 8.10 ?"
date: 2009-01-31
forum: Apple Hardware Users
---

### Post by fredscripts on 2009-01-31
Hi!

I have a macbook Santa Rosa with 8.04 and I would like to upgrade to 8.10. I'm kind of afraid because normally updating a macbook mess up keys and touchpad and other stuff.

Anyone knows if I can do it without any trouble?(upgrading from updatemanager, without liveCD)

Thanks!

---

### Post by DeadRobot on 2009-01-31
I have a Macbook Pro 1,1 from 2006.

I orginally installed 8.04 and then upgraded using the update manager to 8.10 with NO problems at all.  I would give it a shot if i were you.

---

### Post by fredscripts on 2009-01-31
I did it.

Quite a disaster. Touchpad not working. Anyone knows how to have the touchpad working with classical (two-fingers and push right button, scrolling with two fingers...) just how I had it in 8.04?

---

### Post by cyberdork33 on 2009-01-31
> **fredscripts said:**
> I did it.

Quite a disaster. Touchpad not working. Anyone knows how to have the touchpad working with classical (two-fingers and push right button, scrolling with two fingers...) just how I had it in 8.04?
Find the Documentation for your Mac here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by franki.macha on 2009-02-01
i did it on a santa rosa 3,1 macbook, it was fine, i did have use that touchpad fix above, and i had to stick with an old version of skype(possibly not related to the dist-upgrade), but other than that i can't think of anything(it was a few weeks ago) but it was definitely fairly painless :)

---

### Post by fredscripts on 2009-02-01
Thanks I followed that link and touchpad is working!

This isn't working (to change fn behaviour):

append /etc/modprobe.d/options:
 
options hid pb_fnmode=2

sudo update-initramfs -u -v -k `uname -r`


of AppleiSight([https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight))

after sudo apt-get install isight-firmware-tools

of course, 
```

sudo cp AppleUSBVideoSupport /lib/firmware/
```

is not working, there's no AppleUSBVideoSupport file ...


Any ideas?

---

### Post by franki.macha on 2009-02-01
[http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)

This link should work, otherwise just google 'appleusbvideosupport'.
I've taken to keeping a copy of it because i've needed to reload the firmware after a few updates and stuff.

---

### Post by cyberdork33 on 2009-02-01
> **fredscripts said:**
> This isn't working (to change fn behaviour):

append /etc/modprobe.d/options:
 
options hid pb_fnmode=2

sudo update-initramfs -u -v -k `uname -r`
Did you reboot?


> **fredscripts said:**
> 
```

sudo cp AppleUSBVideoSupport /lib/firmware/
```is not working, there's no AppleUSBVideoSupport file ...


Any ideas?
You have to get this file off your OSX partition as instructed. Please read the portion just above that.

---

### Post by fredscripts on 2009-02-01
> **cyberdork33 said:**
> Did you reboot?



Yep. :(



Thanks for pointing out that I had to find that file before running that command, I overlooked it!

---

### Post by cyberdork33 on 2009-02-01
> **fredscripts said:**
> Yep. :(
IDK what to tell you. Maybe need to recheck the /etc/modprobe.d/options file to make sure the option was added

---

