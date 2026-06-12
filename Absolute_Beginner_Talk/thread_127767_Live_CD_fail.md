---
title: "Live CD fail"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by R_MAC on 2006-02-09
My pc boots from the Live CD, goes thru all the screens, logo, hardware detection, etc, gets to a blue screen that says "Failed to start X server gui..." etc. 
and dumps me at a "ubuntu:~$" prompt. If I enter "startx" or "sudo startx"
(my limit at Unix commands) it cycles thru messages about the X server failing
etc and returns to prompt. What now???

---

### Post by taurus on 2006-02-09
What kind of video card and monitor do you have?  Perhaps you need to look in /var/log/Xorg.0.log (or /var/log/xorg.0.log) to see exactly what is the problem...  There is a problem either with your video card and/or monitor.

---

### Post by R_MAC on 2006-02-11
Video card W98se driver is nVidia GeForce2 MX/MX400, monitor is Sony CPD-100ES, Gateway "Essential" Desktop- 450/ PIII, 256mb, Seagate 20gb IDE, DSL  router/10/100 swt, Network Everywhere ethernet 10/100 card/cat5e, Creative Labs SoundBlaster. As per other threads here, tried "sudo dpkg-reconfigure xserver-xorg"  and took all defaults except graphics card=VESA, replied with "Dummy template for processing unavailable question [false---]... if you see this template, you have found a bug- file a report".  
Then entered:  "sudo startx",  
Msgs returned:
 "creating new auth file, 
creating new  /home/ubuntu/.serverauth .18763,  
creating new  /home/ubuntu/.xauthority (2 times), 
giving up, 
xinit:connection failed (errorno 111), 
xinit: no such process (errorno 3),
server error,
-$ prompt again
HELP!!!
How do I "look in /var/log/Xorg.0.log (or /var/log/xorg.0.log) to see exactly what is the problem" ?? (Please forgive, I am a newbie and know little of Linux commands)

---

### Post by R_MAC on 2006-02-11
Trouble is, I have no /var/log/Xorg.0.log file. There are other logs in the /var/log directory but none matching that name. Am using "nano [filename]" to view, "ls /var/log" to see contents of dir.- no file by that name.
HELP!!!

---

### Post by R_MAC on 2006-02-12
SUCCESS!!-- CD boot image was made on CDRW on 1 drive & booted on another.  Once booted from original burner drive, all worked like a charm- went right to desktop and I'm using it now to reply to this thread. Mouse is very ssslllooowww but workslThanks for all who tried to help.

---

