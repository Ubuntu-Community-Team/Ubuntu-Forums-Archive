---
title: "Startup Shutdown Problems with Dapper"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by icelechi on 2006-07-08
Hello,
I have a Lenovo Thinkpad T22 and it runs on Windows 2000 pro and Ubuntu 5.10. I have tried several times to upgrade to a stable version of Dapper Drake, but every time I tried I would have problems starting up and shutting down. When I started it up, the machine would freeze and I would have to restart. When shutting it down, it would go through the normal shutdown process, but then it would simply stop midway. The list of shutdown operations would be on the screen but the computer would still be on.

Anyone know why this happened or how I can fix it?

---

### Post by shoot2kill on 2006-07-08
SORRY, NOT SURE ABOUT FIXING THE ERRO, OR WHATS WRONG WITH IT, WHATABOUT INSTALLING DAPPER FROM SCRATCH, NOT UPGRADE, OR IS THIS NOT PRACTICAL...

JUST A THOUGHT

SORRY I COULDNT HELP

(sorry bout CAPS, only just noticed :))

---

### Post by isharra on 2006-08-05
What worked for me was either to put "acpi=off apm=on" or "ec_intr=0" in the kopt line for /boot/grug/menu.lst. The former if I wanted to use APM for power management the latter if I wanted to use ACPI. I have the most recent bios for this T22 (2002) so acpi is the default when booting.

---

### Post by isharra on 2006-08-05
Almost forgot, if you still hang up when booting (solid underscore in upper left corner) then edit /etc/X11/xorg.conf and add the line 'VideoRam 8192' to the device section for the savage driver. If you'd rather not manually edit the file, 'sudo dpkg-reconfigure xserver-xorg'

---

### Post by paulvbrown on 2006-08-18
Hi - similar problem solution here: 

[http://www.ubuntuforums.org/showthread.php?t=225588](http://www.ubuntuforums.org/showthread.php?t=225588)

Although I'm also having the shutdown problems you mention occasionally.  Haven't tried troubleshooting them yet, though.

-paul

---

