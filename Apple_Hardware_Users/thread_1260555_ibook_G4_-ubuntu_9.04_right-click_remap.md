---
title: "ibook G4 -ubuntu 9.04 right-click remap"
date: 2009-09-07
forum: Apple Hardware Users
---

### Post by itdoesnot on 2009-09-07
i've searched everywhere, but i can't find anything useful

this one in particular, sounded easy enough, but my /etc/sysctl.conf. file
only had settings about not forwarding packets and other routing stuff
[http://ubuntuforums.org/showthread.php?t=212373](http://ubuntuforums.org/showthread.php?t=212373)

i'm trying to get the right click remapped to something else,
if someone can point me in the right direction, that would really help
(i can find the keyboard codes, etc, i just need to know where to edit
or drivers to replace?... i have no clue) 

for some reason F12 does an eject, and Fn+F12 does the right-click
but that may be besides the point...?

---

### Post by itdoesnot on 2009-09-07
bump

---

### Post by rjcalifornia on 2009-09-07
I really prefer that configuration, I really don't know how to remap that... 

Use a mouse, perhaps?

---

### Post by itdoesnot on 2009-09-15
bump

---

### Post by gwydionwaters on 2009-09-16
i have set mine on my powerbookg4 to be ctrl click
it's uber easy. 
just edit /etc/default/mouseemu
there will be a number of lines commented out with #, remove the # on the line with right click, there are descriptions of which is what.
then restart, you could restart the mouseemu via command line but in my experiences it is easier to just reboot.

---

