---
title: "quick/easy/short grub mapping question"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by magnethead on 2007-06-18
here's the XP chunk of my menu.lst:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title Windows NT/2000/XP (loader)
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 

now, that covers it for XP home (even though it doesnt work). For XP Pro, which is on the first recognized drive by linux, do i need to do this?

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title Windows NT/2000/XP (loader)
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 

title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
map (hd0) (hd0)
map (hd0) (hd0)
chainloader +1 


and is the map block even needed sinceXP pro is on the only partition on the hd0 drive?

---

### Post by suhanduman on 2007-06-18
You don't have to "map" lines for the drive 0.
(I assume Ubuntu and grub is on that drive too.)

---

### Post by magnethead on 2007-06-18
no, ubuntu is on drive hd1.

I have XP home on hd2, XP pro on hd0, and ubuntu on hd1.

---

### Post by ckempo on 2007-06-18
Hi,

Look here: [http://ubuntuforums.org/showthread.php?t=474734]("http://ubuntuforums.org/showthread.php?t=474734")

Hopefully that contains all the info you will need.

---

### Post by magnethead on 2007-06-18
thanks. 

now, due to readin another post, i changed my menu.lst and my devices.map to show for my ubuntu drive to be hd0, XP Pro to hd1, and XP home to hd2. That still holds, right?

so i perform 

root (hd0,0)

setup (hd2)

right? the windows pair boot off the boot.ini of the XP Home as it's the dell install.

will this solve my in-ability to access grub from my boot override to secondary slave (ubuntu drive)?

edit- what i proposed returns cannot mount selected partition, same result with setup hd1. I assume it's wrong then?

---

