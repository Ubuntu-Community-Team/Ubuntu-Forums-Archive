---
title: "Bonobo errors ..."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-31
"Nautilus can't be used now.  Unexpected error from Bonobo when attempting to register the file manager view server."

"The panel could not register with the bonobo activation server (error code: 3)"


I get these "bonobo" errors when I attempt to remote into my system using NXServer/FreeNX.  NX authenticates ok, but GNOME will not start - all I get is a black screen.

The NXServer website states that it is a GNOME issue associated with temporary files like gconf and DCOP.

Anyone have any insight into this?

Carl

---

### Post by candtalan on 2008-06-02
I have seen rather similar errors in a different context.

a specific posting of mine is
[http://ubuntuforums.org/showthread.php?t=732194](http://ubuntuforums.org/showthread.php?t=732194)

And although this post relates to the beta version, I get the same response from the released version 8.04 - in the hardware that is, it seems to be hardware related, and I believe something to do with xorg and the xserver, not sure though. I made a number of posts following the above and they also related to this hardware and live CD function. 

I know now that it is not just live CD related either. A normal install of 8.04 on that hardware (Inspiron 1100 laptop) will give a similar problem at start or re-start of the xserver: ctrl alt backspaace, and or log out , log in, or first run when booted. It happens only occasionally, only some occasions.

other possibly related (or not) posts:
[http://ubuntuforums.org/showthread.php?t=759899](http://ubuntuforums.org/showthread.php?t=759899)
[http://ubuntuforums.org/showthread.php?t=660339](http://ubuntuforums.org/showthread.php?t=660339)
[http://ubuntuforums.org/showthread.php?t=772209](http://ubuntuforums.org/showthread.php?t=772209)

Unfortunately I did not see any solution and found that replacing the entire xorg.conf file with one that worked in this machine from suse 10.1 days, gave reliable and acceptable results. So that is what I currently use, not the xorg.conf which is created using 8.04 :-(

hth?

---

