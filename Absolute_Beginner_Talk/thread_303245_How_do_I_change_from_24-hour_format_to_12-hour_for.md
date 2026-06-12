---
title: "How do I change from 24-hour format to 12-hour format?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-19
Okay, this is probably my most stupid question I've ever asked here.  For some reason, my clock decided to switch from 12-hour format to a 24-hour format.  How do I switch it back to 12-hour format?  I've tried adjusting the preferences and nothing has worked.  Oh, by the way, I'm using Dapper Drake.  Thanks!

---

### Post by Travisty on 2006-11-19
> **Antarctica said:**
> Okay, this is probably my most stupid question I've ever asked here.  For some reason, my clock decided to switch from 12-hour format to a 24-hour format.  How do I switch it back to 12-hour format?  I've tried adjusting the preferences and nothing has worked.  Oh, by the way, I'm using Dapper Drake.  Thanks!

Have you tried right clicking on the clock and selecting preferences?

---

### Post by Antarctica on 2006-11-19
I have three choices:  24 hour, UNIX time, and Internet time

---

### Post by aysiu on 2006-11-20
> **Antarctica said:**
> I have three choices:  24 hour, UNIX time, and Internet time
That's bizarre.

---

### Post by aysiu on 2006-11-20
What happens if you press Alt-F2 and type ```
gconf-editor
``` then go to Apps > Panel > Clock_Screen0 > Prefs?

Can you then manually change *format* to *12-hour*?

---

### Post by Antarctica on 2006-11-20
> **aysiu said:**
> What happens if you press Alt-F2 and type ```
gconf-editor
``` then go to Apps > Panel > Clock_Screen0 > Prefs?

Can you then manually change *format* to *12-hour*?

I tried changing it to 12-hour format and nothing happened.  Is there a way I can reinstall the clock?

---

### Post by Me! on 2006-11-20
Same problem, change your country from logon screen

---

### Post by aysiu on 2006-11-20
> **Antarctica said:**
> I tried changing it to 12-hour format and nothing happened.  Is there a way I can reinstall the clock?
When I made a change in *gconf-editor*, the change happened immediately.

Can you try this? ```
sudo chown -R antarctica:antarctica /home/antartica
``` and then making that change through *gconf-editor*?

Substitute in your actual username for *antarctica*, of course.

---

### Post by Antarctica on 2006-11-20
Nothing happened after doing sudo chown -R brett:brett /home/brett

(brett is my username btw)

---

### Post by aysiu on 2006-11-20
> **Antarctica said:**
> Nothing happened after doing sudo chown -R brett:brett /home/brett

(brett is my username btw)
So after doing that, you're still unable to change the time format through *gconf-editor*?

---

### Post by Antarctica on 2006-11-20
> **aysiu said:**
> So after doing that, you're still unable to change the time format through *gconf-editor*?

Still unable to change the clock from 24-hour to 12-hour format.  Will reinstalling the clock applet fix the problem?

---

### Post by aysiu on 2006-11-20
> **Antarctica said:**
> Still unable to change the clock from 24-hour to 12-hour format.  Will reinstalling the clock applet fix the problem?
Hm. I doubt it, but you can try.

Actually, another thing to try would be to set up a test user (one you can delete later) and see if the test user can change the clock preferences. If not, then it's a systemwide problem probably related to the clock applet. If so, it may be a permissions issue with your own account.

---

### Post by Antarctica on 2006-11-20
I don't know if this may help, but I downloaded the latest CVS of a game called Stepmania from their site (the Linux version) and ran it.  I did seem to have some issues with it, mostly graphic and keyboard issues.  I did quite frequently run the command > sudo /etc/init.d/gdm restart to terminate everything and return to the login screen.  Somewhere in all that, I noticed the clock changed.

---

### Post by steve.horsley on 2006-11-20
Probably a silly idea, but have you looked to see what time zone you are in? I wonded if some time zones have 12h disabled for some reason.

---

### Post by Antarctica on 2006-11-20
> **steve.horsley said:**
> Probably a silly idea, but have you looked to see what time zone you are in? I wonded if some time zones have 12h disabled for some reason.

My time zone is America/Chicago.  This is so weird.  I don't know why my time format can't be changed.

---

### Post by Antarctica on 2006-11-20
I'm thinking about upgrading to Edgy instead of dealing with Dapper.

---

