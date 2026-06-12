---
title: "rEFIt doesn't work~!"
date: 2009-02-09
forum: Apple Hardware Users
---

### Post by wxiluo on 2009-02-09
I installed rEFIt-0.12.dmg on my new Mac book M467(Intel Core 2 Duo 2.4GHz 2GB memory).
The version of my Mac OS X is 10.5.5

Everything went well,BUT I didn't see the rEFIt boot menu on the next restart. 

OS is not supported by rEFIt-0.12?:(

---

### Post by cyberdork33 on 2009-02-09
> **wxiluo said:**
> I installed rEFIt-0.12.dmg on my new Mac book M467(Intel Core 2 Duo 2.4GHz 2GB memory).
The version of my Mac OS X is 10.5.5

Everything went well,BUT I didn't see the rEFIt boot menu on the next restart. 

OS is not supported by rEFIt-0.12?:(
it isn't the OS that has to support it, but the hardware. and yes, it should support the latest macbook. Check the rEFIt website for help and docs:
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by gnabgibeht on 2009-02-09
did you try putting the efi folder in the root folder of your osx folder
go to terminal in utilities
type
cd /efi/refit (hit enter)
./enable.sh (hit enter)
then i think they ask you for password if you have one

it should work. the rEFit didn't load when i restarted at first too, after doin the steps listed above, works like a charm... and if you go into linux or windows if you triple booting and it doesn't load, try loading the partition tool on boot and it'll help you re-list the partition so all the OS's will work



-gnab.gib.eht

---

