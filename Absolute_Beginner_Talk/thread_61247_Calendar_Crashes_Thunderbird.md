---
title: "Calendar Crashes Thunderbird"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by Mike-97470 on 2005-08-31
When I initially installed Thunderbird (Synaptic from its repo) it worked.  Then I installed the Calendar extension and it worked.  But at some point, whenever I try to open the Calendar, there is a click, click, beep, beep sound(s) and Thunderbird crashes (it's window disappears from the desktop).  Unfortunately, I don't know what change I made before this started occuring.  BTW, I've uninstalled both the Calendar and Thunderbird, rebooted and reinstalled them but T-Bird still crashes.

When I start T-Bird from the Terminal and try to open the Calendar, here's the result--

mike@MikesPavillion:~$ mozilla-thunderbird
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159: 11594 Segmentation fault    "$prog" ${1+"$@"}
mike@MikesPavillion:~$

---

### Post by Mike-97470 on 2005-08-31
What I forgot to ask is for some help in troubleshooting this problem--I want to fix it without reinstalling everything . . . 

For example, is there a way to run under a  "Trace" and record instruction by instruction?  Or is there an error log somewhere?

---

### Post by Mike-97470 on 2005-08-31
Well, it's nice when things start working!  Yup, Thunderbird Calendar is now working again!  When it started working,-- when I opened the Calendar, it made the same click, click, beep, beep sound that it did when it crashed Thunderbird, but it opened the Calendar window instead and everything was ok.  There were 2 appointment notices from last week and the first one beeped when I acknowledged it, not the second.  And no clicks or beeps since then, opening both T-bird and Calendar a couple of times.

So here's the last thing I did before it started working--
1.  Deleted the 2 386 entires in the GRUB menu. (from /boot/grub/menu.lst)   (I had switched the kernel to 686 earlier.)
2.  Installed various XMMS plugins and the Acrobat stuff for Firefox.
3.  Switched both BMP and XMMS to the eSound Plugin and both started working.

Th.th.that's all, I know that shouldn't be related, but it didn't start working all by itself.
And I'm not gonna complain!

---

