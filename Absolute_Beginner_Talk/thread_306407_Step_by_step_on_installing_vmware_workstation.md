---
title: "Step by step on installing vmware workstation?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by RideP2 on 2006-11-24
Hi, does anyone have a steb by step on how to install Vmware Workstation on Ubuntu 6.06?

---

### Post by RideP2 on 2006-11-24
I think I messed up something trying to run vmware-install.pl because now I cant run it anymore. this is the error. 

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.

Failure

Execution aborted.


I cant even delete the vmware folder in usr/bin because i dont have the rights.

---

### Post by taurus on 2006-11-24
If you want to delete it, use the sudo command!!!

```
sudo rm -rf /usr/bin/vmware
```
***  Better make sure that is what you want to remove because if you remove the wrong directory, you can crash your machine and I _[COLOR="Red"]will not[/COLOR]_ take any responsibility for it...

---

### Post by RideP2 on 2006-11-24
I deleted it, but it's still giving me the same error, what do i do to make it think i havent "started" doing another install.. cause i was just trying to install it but it never did nothing.

---

### Post by taurus on 2006-11-24
Maybe a reboot would help!!!

---

### Post by RideP2 on 2006-11-24
Ah! Possible.

---

### Post by RideP2 on 2006-11-24
Darn.. It's still giving me the same error.

---

### Post by tjk on 2006-11-26
> **RideP2 said:**
> Darn.. It's still giving me the same error.

I have to interject, because I'm having exactly the same problem -- so I hope that a solution will be posted...

---

### Post by Shay Stephens on 2006-11-26
My problem with vmplayer is that it insists on reconfiguring network stuff everytime a program is installed or updated, and stops to ask me half a dozen times if I want to do that.  I bugs me so much that I never load vmware anymore.

Does anyone have a fix for that?!?!

---

### Post by LLRNR on 2006-11-26
My guess:
```
sudo rm -R /etc/vmware
```
from [here](http://ubuntuforums.org/showthread.php?t=183209)...

---

### Post by ashmew2 on 2006-12-29
Thanks !!! LLRNR!! the command did the job :D

---

