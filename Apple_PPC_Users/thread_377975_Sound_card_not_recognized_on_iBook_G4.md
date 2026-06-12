---
title: "Sound card not recognized on iBook G4"
date: 2007-03-06
forum: Apple PPC Users
---

### Post by snailofdeath on 2007-03-06
I'm new to linux installation, and I have run into an issue I have not been able to solve.  I am installing Ubuntu on an iBook G4, and for what ever reason, the sound card's not recognized.  Any ideas about how to get this working?

Thanks!

---

### Post by maggot_brain on 2007-03-06
What version of Ubuntu are you using?  If you installed via the 6.10 alternate cd then the snd-powermac module is not loaded by default.  Try this:

modprobe snd-powermac

and then log out of KDE / GNOME or whatever desktop you're using and log back in.  If this solves the problem the add the line (without quotes) "snd-powermac" to the end of he /etc/modules file.  This worked for me on an iBook G3 but it should be a similar setup for a G$

---

### Post by snailofdeath on 2007-03-06
> **maggot_brain said:**
> What version of Ubuntu are you using?  If you installed via the 6.10 alternate cd then the snd-powermac module is not loaded by default.  Try this:

modprobe snd-powermac

and then log out of KDE / GNOME or whatever desktop you're using and log back in.  If this solves the problem the add the line (without quotes) "snd-powermac" to the end of he /etc/modules file.  This worked for me on an iBook G3 but it should be a similar setup for a G$

I have the version you mentioned, and I did what you said -- and it works!  Thank you so much!

---

### Post by Quither on 2007-03-09
I have been having a similar problem with my Beige G3.  No sound at all under Ubuntu 6.10.  I tired the above suggestion and it didn't work.  got the following error:

**Could not load /lib/modules/2.6.17.11/modules.dep**


Also, if i try to adjust the system volume, it tells me it could not find GStreamer or a soundcard.  Any ideas?

---

### Post by maggot_brain on 2007-03-15
Try doing this as it can't find the module dependecies file

sudo depmod

Then reboot and try my method again.


> **Quither said:**
> I have been having a similar problem with my Beige G3.  No sound at all under Ubuntu 6.10.  I tired the above suggestion and it didn't work.  got the following error:

**Could not load /lib/modules/2.6.17.11/modules.dep**


Also, if i try to adjust the system volume, it tells me it could not find GStreamer or a soundcard.  Any ideas?

---

### Post by marcthenarc on 2007-04-29
Worked great for me too.  Thanks. :)

---

### Post by rwhitehair on 2008-03-28
wow! I've been researching this problem all day and couldn't seem to find anything and it was as simple as this. I feel like an idiot but a little smarter! Thanks for your help! it worked well for me!

---

