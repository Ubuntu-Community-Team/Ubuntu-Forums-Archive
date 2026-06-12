---
title: "Lost  Trash can icon"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-23
Help - I installed CPU-frequency-scaling monitor and all I got was the CPU speed, Thats ok but I lost
5 other applets. Things like Trash, Battery.



Below are the error pop-ups I get when I try to add to panel.

"The panel encountered a problem while loading
Do you want to delete the applet from your configuration?"

and I get following pop-ups

1 - oafiid:gnome_panel_TrashApplet
2 - oafiid:gnome_MultiLoadApplet
3 - oafiid:gnome_MixerApplet
4 - oafiid:gnome_Panel_wirelessApplet
5 - oafiid:gnome_BattstatApplet

How do I get these back ?
what happens if I delete them?

---

### Post by kent41 on 2006-10-23
Update:

When I try to add or delete to the panel I get the messages.

Is there anyway to go back to the configuration before I installed the CPU-FREQ program like in windoz?

---

### Post by jslwyd on 2006-12-11
When I try to add or delete to the panel I get the messages.

The panel encountered a problem while loading...

"OAFIID:GNOME_MixerApplet".

                                

                                         can you help me !

---

### Post by wlx on 2007-05-09
have you tried this:
sudo apt-get install --reinstall gnome-applets

---

### Post by Emeriz on 2007-05-11
I was having the OAFIID:GNOME_Panel_TrashApplet  issue when logging in and reinstalling gnome-applets didn't clear it up.  But when I reinstalled gnome-applets-data as well, everything started working.

Hope that helps.

Em

---

### Post by Emeriz on 2007-05-15
Sigh, now it looks like after several reboots the issue is back.  Reinstalling and restarting GDM still resolved the immediate problem for a few reboots, but it keeps coming back for some reason....

Any ideas?

Em

---

### Post by distortedstar on 2007-11-30
I'm having similar issues. I wonder if it's related to xserver-xgl? Seemed to happen after I installed that. But that fixed another problem I was having. *Sigh*. Wish I was having the great gutsy experience everyone else is.

---

### Post by distortedstar on 2007-11-30
Uninstalling xserver-xgl solved the applet problem...but now my other problem is back...a crashing gdm on every logout.

---

### Post by buzznot1012 on 2008-05-26
> **wlx said:**
> have you tried this:
sudo apt-get install --reinstall gnome-applets

Worked like a charm for me!  Thanks!

---

### Post by Gavin Coles on 2008-05-27
> **wlx said:**
> have you tried this:
sudo apt-get install --reinstall gnome-applets
Hi WLX,

Just to say thanks for the tip, solved my problem completely.  Plus thanks to all the contributors on this forum I'm learning a hell of a lot.

---

