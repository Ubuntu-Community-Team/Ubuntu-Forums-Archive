---
title: "Trouble installing v6,06"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Cipher Highwind on 2008-03-21
My apologies if this was redundant, but I did not see this regarding X-server as it pertains to installation.

I am installing v6,06 on a A205-S5803 Toshiba laptop, pre-installed with Vista (:()

The error message is as follows: 
Failed to start the X server (your GUI).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem? (Y/N)

X Windows Sys. V 7,0,0
Release date: 21 DEC 05
X Protocol V 11, Rev. 0, Rel, 7,0
Builed OS: Linux 2,7,15,7,i686
Current OS: Linux Ubuntu 2,6,14-26-386 #1 PREEMPT Thu 3 Aug 02:52:00 UTC 2006 i686
Build date: 16 MAR 06
&c
(default setting)	 log file: “/var/log/Xorg/0.log” ...
(default setting) 	Using config file “/etc/X11/xorg.conf”
(warning)		I810: No matching Device section for instance (BusID PCI:0:2:1) found
(error)			No devices detected.

Fatal server error: no screens found

X server now disabled; restart GDM when properly configured.
	
&#949;&#8016;&#967;&#940;&#961;&#953;&#963;&#964;&#959;&#962; &#949;&#7984;&#956;&#943; / Thanks

---

### Post by Vadi on 2008-03-21
Is there any reason as to why you're trying 6.06, and not 7.10? I would recommend that you install 7.10 - maybe the problem with your laptop was fixed in it already.

---

### Post by Cipher Highwind on 2008-03-21
I will try that ASAP and will get back to ye should the problem persist.

---

### Post by sumguy231 on 2008-03-21
From what I've seen, it has an Intel X3100 graphics chipset, right? I know that works under Ubuntu 7.10, so you might have more luck with that. If you still can't get it to work try starting in safe graphics mode.

---

### Post by Cipher Highwind on 2008-03-21
It worked; thanks :-D

---

### Post by Vadi on 2008-03-21
Sweet :)

Click on "Thread Tools" on top and "Mark Thread as solved". It'll help when people with the same problem will be looking for a solution after.

---

