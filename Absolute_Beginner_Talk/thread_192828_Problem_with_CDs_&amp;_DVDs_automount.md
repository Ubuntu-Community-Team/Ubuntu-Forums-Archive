---
title: "Problem with CDs &amp; DVDs automount"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by xcarol on 2006-06-09
Some time ago, I had the next problem: when I inserted a CD or DVD on the reader the led started to blink as usual. Next Konqueror started up and tried to show me the media://hdc contents. But instead the disc contents there was this message: 
"An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist."
If I tried to mount the disc from the command line as: "mount /dev/hdc /media/cdrom" there was no problem.
So I started to look up around a solution for that problem. Finding lot of people with same or similar problems but no solution.
It could sound silly, but the other day (don't know why) I went to "System settings -> Kde Components -> Service Manager", then stoped and started again the "KDED Media Manager".
That was! Now CDs and DVDs are mounted by the system and show the Desktop icon as the first day.

Hope it helps.

---

### Post by mindwarp on 2006-06-14
Good to hear someone got that fixed and posted a solution

---

### Post by vayde on 2006-06-21
I had the same problem jump out of nowhere tonight.  Fixed it with the following:

sudo /etc/init.d/udev restart

---

### Post by martux on 2006-07-07
this exactly was my problem as well and just restarting udev has solved it. thanks!

---

