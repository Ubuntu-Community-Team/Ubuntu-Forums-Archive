---
title: "Slow ubuntu--how to return to initial setup?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-09-21
Installed ubuntu (Dapper) on my son's 2nd partition (XP on other) which went fine but after unsuccesfully trying to access home wireless network (WPA encrypted D-link router attached to my dual-boot desktop which runs Dapper most of time), I've done something (not sure what!) such that now Dapper runs as slow as if I were still running the live CD (which I'm not).  My son's machine is a home build with AMD Athlon64 3700, 1 GB RAM, 250 GB drive so speed of machine shouldn't be an issue & runs fine on XP.

Question--is there a simple command to reset ubuntu to its 'native' settings/state just after install so I can try again?  Should I reinstall?  Any guess how I might have done this?!

Much obliged.

---

### Post by Brunellus on 2006-09-21
what, in general, have you been doing, and what guides have you been following?

---

### Post by james_san on 2006-09-21
Don't know how you did this - but...
If the problem is only in the Ubuntu gui, you can reset it by deleting everything in /home/yourname.
However, if the problem is in the core of Ubuntu (for example starting up and shutting down are slower as well), then you will probably need to reformat to get it back to normal.

Don't think of this as a cop-out. I muck things up all the time and need to reformat. It is usually easier than spending days trying to figure out what went wrong. (Same thing happens to me in Windows as well)

---

### Post by flyingsolo on 2006-09-21
In general, I was just trying to get his Ubuntu to access internet so I could get packages etc. and tweak it similar to mine but couldn't seem to access via eth0.  Can't say I was following any specific guide since I've done this before setting my own machine up and getting internet access was trivial--not so this time!  My IT knowledge base is slim but I've run Ubuntu successfully for myself for ~1 year now.
Is the WPA encryption a problem for Ubuntu? (I think I've read posts regarding this in past)

---

### Post by Brunellus on 2006-09-22
WPA encryption may be the problem, depending on what driver you're using to make it work.

---

### Post by flyingsolo on 2006-09-22
Could you elaborate about the drivers for WPA?  The router is a common D-link (524 I think; I'm at work now) and the WPA encryption is set up on it with password given to home users to access it.  What I don't know is where one sets the WPA password in Ubuntu--there is a request for *WEP* password but no obvious input for **WPA** that I can see.

Thanks (sorry, delay in responding 'cause it was late last night when I started this!)

---

