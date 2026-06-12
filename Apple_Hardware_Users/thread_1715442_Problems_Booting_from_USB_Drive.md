---
title: "Problems Booting from USB Drive"
date: 2011-03-26
forum: Apple Hardware Users
---

### Post by jtruelove on 2011-03-26
I'm trying to create a bootable USB thumb drive with ubuntu, I followed the directions on this page [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I converted the iso to a dmg fine, then ran 

diskutil unmountDisk /dev/diskN
sudo dd if=ubuntu-10.10-desktop-i386.dmg  of=/dev/diskN bs=1m

all of which ran fine, but it doesn't show up when I reboot into Startup Manager. Also when I go into System Preferences -> Startup Disk it doesn't show either. I'm running OS X 10.6.7. The USB disk is an 8gb Sandisk. Thanks for any help.

---

### Post by catmanduo on 2011-04-10
10.10 has a flash disk creator program -- all you need is the iso
(if you're booting off of a live DVD I think you can use the same raw device).
It's called something like usb-creator-gtk.
This is what I used to create my successful live USB.
 
Cat

---

### Post by catmanduo on 2011-04-10
Tell me how you convert an .iso to a .dmg though -- 
maybe this would be useful to me (although it didn't seem to work for you).
I'm still learning about all this stuff, and am trying to put together
a safe, read-only, populated OS as the security kernel.
 
Cat

---

