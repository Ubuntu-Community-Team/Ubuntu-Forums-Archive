---
title: "Beryl freezes after I meddled!"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mdurkin on 2007-03-17
All,
Beryl was working just great and I decided to try forcing it to use nvidia, then glx - anyway, nvidia worked fine, but when I selected glx it froze. Now whenever I start beryl it just freezes. How do I set beryl to use nvidia again? I can't start beryl to get at the settings menu (from the red diamond). I guess it must be somewhere in a file.
I did try removing and reinstalling but that didn't help. I guess the config file stayed.

Any help appreciated!
Matt

---

### Post by terdon on 2007-03-17
Well, the first thing you can do is log in to another desktop (say gnome) and then run "beryl-manager" This will bring up the diamond and you can change the settings. 

Otherwise, your settings files are in the directories $HOME/.beryl. If you delete that directory and reinstall you'll have a clean system.

---

