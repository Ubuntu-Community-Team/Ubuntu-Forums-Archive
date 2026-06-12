---
title: "Update Broke My X"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-22
I updated today (first time in a long while, had 93-ish updates) and re-booted, only to find out that it wouldn't work. I've read some other threads, but so far nothing's working for me. Quick facts:

-GDM loads fine. I can log in just fine. Splash screen shows, background image shows, gnome-panels show (but no buttons or anything, just the blank panel) and then the screen goes black for a little bit and brings me back to GDM.

-I have Beryl load by default and have proprietary nVidia drivers. But, when I pick the Failsafe GNOME session (which, I'm assuming wouldn't load Beryl), it does the exact same thing.

-When I boot into recovery mode and "startx" no errors show up and everything goes smoothly. I'm typing from recovery mode right now. Plus, it shows the nVidia boot screen, so I'm assuming that's not the issue.

-My xorg.conf file hasn't been edited since January 9th (when I was getting Beryl set up, IIRC), if that could be an issue.

Do I need to post any log files? I'm not sure where to go from here.

I was thinking about wiping clean and re-installing with i386 instead of AMD64 anyways, so maybe this is a sign. :) Still, I'd like to be able to find out what's going wrong so that I can backup before reinstalling (and for future reference - I'm sure this won't be the first time).

EDIT: Problem solved. I had tried re-installing the nVIDIA drivers like I had before without avail. For some reason, this worked:

-Editing xorg.conf and using "nv" instead of "nvidia"
-Deleting the beryl.desktop file to prevent it from loading (because of nv driver)
-Booting into normal user account.
-Installing / using envy to get nVIDIA drivers.

---

