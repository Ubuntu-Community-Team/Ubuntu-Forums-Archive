---
title: "Just installed on new pc,  Very Low Sound"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-05-31
I can barely hear the sound.  The little speaker icon mouse over says "FRONT 100%"  My new system has Realtec ALC888 audio.  Anybody know how I can get sound to work right?  I'm playing through regular pair of pc speakers.

---

### Post by happy-and-lost on 2007-05-31
Open a terminal and launch *alsamixer*.

You can see what levels all of your audio channels are at, and modify them until one works!

From there, you can set the Default Mixer Track (the working one) in the System->Preferences->Sound config util.

---

### Post by seetho on 2007-05-31
Right mouse click on the speaker icon on the top right of your desktop.  Then select Open Volume Control.  You should see a Master volume control.  If not then use Edit->Preference to activate it.  Just play around with the various volume controls to see if it helps.

---

### Post by Atomic Dog on 2007-05-31
> **seetho said:**
> Right mouse click on the speaker icon on the top right of your desktop.  Then select Open Volume Control.  You should see a Master volume control.  If not then use Edit->Preference to activate it.  Just play around with the various volume controls to see if it helps.


This is how I solved my low volume issue.

---

### Post by seetho on 2007-05-31
While you are at it you may as well set your microphone or capture levels.  The default on a Feisty install is 0!!!  Lots of people in this forum have trouble using their microphones after install - including me.

---

