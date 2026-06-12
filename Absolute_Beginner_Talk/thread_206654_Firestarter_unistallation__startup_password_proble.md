---
title: "Firestarter unistallation / startup password problems"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by WhoDaBear on 2006-06-30
Hi folks.  

Linux very-Newbie (bet you've heard that before) in need of help.

The firestarter GUI was starting on startup (which I didn't like).  I removed it using add/remove programs, and yet it still asks me for a password for firestarter on startup, and then doesn't display the GUI.  I already removed its entry from the "sessions / startup" menu.

Have found relevent threads elsewhere, but the instructions there don't help!  Anyone out there had this problem?  Suggest a fix?

Thanks in advance.

WhoDaBear

---

### Post by ajgreeny on 2006-06-30
Do all the following in a terminal, one line at a time:-

sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo dpkg -P firestarter
sudo /etc/init.d/networking restart

I think all should be OK after that. This stops firestarter asking for the password on startup, returns iptables to their default, purges all the configuration of firestarter, and then restarts networking.

Good luck.

---

### Post by WhoDaBear on 2006-06-30
Hi there.

Thanks for replying to my previous post - I appreciate the help!

Unfortunately, no luck.

Followed the instructions, rebooted, and still asked for password for firestarter.

Any ideas?

Thanks.

---

### Post by ajgreeny on 2006-06-30
Just a thought - have you removed it from the startup programs list?  I'm afraid I can't remember where that is in gnome but I'm sure it is worth looking into.  If it is still listed, remove it and perhaps the pw request will disappear.

---

### Post by Apple 101 on 2006-07-01
If you don't want it, remove it.  Open Synaptic, search for *Firestarter*, and select the Completely Remove option.

---

### Post by WhoDaBear on 2006-07-01
Hmmm.

You would think it would work that way - I did too.

Synaptic now shows all options *greyed out* except for "mark for installation" and "properties".

If I'm doing something dumb, please tell me.  Otherwise, any other ideas?  Thanks.

WhoDaBear

---

### Post by Apple 101 on 2006-07-01
I'd suggest reinstalling it, and then using the Completely Remove option.

---

### Post by WhoDaBear on 2006-07-01
OK, so I was being dumb.  Now solved.  Solution here (for me!) in case others are searching forums for same.

System->prefs.->sessions  
Select the "Current Session" tab.
Click on any instances of firestarter and click remove.
Reboot.

Result - no password request for firestarter any more.

---

### Post by Apple 101 on 2006-07-01
Your solution looks fine to me... although users may want to check the Startup Programs tab as well.

Well done!

---

### Post by WhoDaBear on 2006-07-01
Thanks for the help.

WhoDaBear

---

