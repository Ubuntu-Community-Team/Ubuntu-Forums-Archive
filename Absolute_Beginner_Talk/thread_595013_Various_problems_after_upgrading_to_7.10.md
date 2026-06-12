---
title: "Various problems after upgrading to 7.10"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-10-28
First, my network device stopped working for some bizarre reason, and nothing I tried got it working again.  Then, I tried to go into my system settings to see if I could do anything these, but I got an error message that said:

"The application System Settings (systemseeings) crashed and caused the signal (SISEGV)."

After that, I tried to go into my hard drive with Konqueror (I use KDE), but I got a message that said, "Feature only available with HAL."  (Even if I had HAL, he would probably just tell me, "I'm sorry Dave, I can't do that." :) )

Anyone have an idea of what I need to do to fix these issues.  Upgrading to a new version of Ubuntu always seems to cause weird problems like these.  (Whenever a new version comes out, it would probably be a good idea to put it on a CD and test it before installing,)

---

### Post by philinux on 2007-10-28
Short of booting in recovery mode I have a look through /var/log/messages to try and track down any boot errors.

---

### Post by CodeDragon on 2007-12-21
I don't know if you still need the help but I ran into very similar problems after upgrading my girlfriend's Kubuntu from 7.04 to 7.10.  Just yesterday, I managed to fix the issue with the System Settings, and found this thread as I was looking for something for the HAL problem.  I also had an issue where she couldn't get into her Adept to do anything.

I tried to install something via aptitude on the command line, but it couldn't.  However, it suggested to try running "sudo dpkg --configure -a" to fix it.  I did so, and it ran for several minutes.  After it was done, not only did aptitude and Adept start working, but so did her System Settings.  Unfortunately, the HAL issue hasn't gone away.

If any one knows what to do about the "Feature only available with HAL" issue, I would greatly appreciate it.  Thanks.

---

### Post by pana.corbului on 2007-12-24
Hi, I had exacly the same problem as you, on a laptop toshiba l40-14f. In my search for tuneup tips for my kde desktop [7.10] I've modified /etc/init.d/rc from CONCURRENCY=none to CONCURRENCY=shell [in case of a dual core proc. the whole system would load faster] and noticed that guidance-power-manager [that systray icon for managing battery] dissapeared, system settings caught a 11 signal and in konqueror on media storage link,hdd's where gibrishing someting like error communicating to hal althought I had hal install.

After modifying to CONCURRENCY=none in the above file everything returned to normal. Hope it works for you too. Merry Christmas:popcorn:

---

