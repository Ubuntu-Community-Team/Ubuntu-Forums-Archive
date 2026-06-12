---
title: "Can only boot into Gnome Failsafe"
date: 2011-05-26
forum: Any Other OS
---

### Post by Infamshxr on 2011-05-26
Yesterday, I decided to further "pimp" my Gnome Desktop. I was looking into window transparency and found out about gtk2-module-rgba after I installed nautilus elementary and found the transparency option. My idea was to get eveerything to look like that. 

Well, I followed the directions, and installed the rgba package and when I logout and log back in to get the changes to occur, nothing happened. Once, I logged out, I got stuck on a black screen. So, I assumed something froze, or whatever, so I hit the power button and restarted my laptop. 

Now what it does is just sits there during the Linux Mint 10loading thing before I get to the login screen. Although, I can go into recovery mode and boot into Gnome failsafe or low-graphics mode. Whichever it's called. That works fine, except of course the low graphics, but everything works fine.

So, I'm basically stuck. I googled around a bit and haven't found anything related closely enough to my problem. One thing I found was to try removing gtkrgba.sh from /etc/profile.d but I'm not totally sure what that means and haven't tried it yet.

Here's the links to the info I found.

[http://ubuntuforums.org/archive/inde...t-1412052.html](http://ubuntuforums.org/archive/inde...t-1412052.html)

[https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA](https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA)

EDIT: I got it to go past the loading screen, but gets stuck on a blank screen and does nothing. Also tried to startx from the command line but that didn't work either. Just did the same thing as booting normally except with the command line up top. If I hit tab or esc during a normal boot I get a black screen with this error at the top:
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

Then just sits there til I turn off the laptop. So, now idk if I'm more screwed than I was originally, but this is way beyond my knowledge.

---

