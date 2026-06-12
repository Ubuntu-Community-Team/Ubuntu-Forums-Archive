---
title: "Attack of the tooltips"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2006-02-06
If I had three wishes from a genie, I'd use them ALL to never have to see a tooltip again!! He'd probably need three tries anyway just to get it done :rolleyes: 

How do I get rid of these pesky things.  I've gone into gconf-editor, did a find for tooltip, got a couple dozen entries, and set them all to value 0

There were a couple that seemed pretty important like:

/schemas/apps/panel/global/tooltips_enabled

But when I try and edit it I'm told:
> Currently pairs and schemas can't be edited. This will be changed in a later version.

I've unset the key, but it comes back each time I restart X and Gnome

Help!!!

---

### Post by aysiu on 2006-02-06
This probably isn't the answer you're looking for, but if they bother you that much, you can use KDE. It's very easy to turn the tooltips off in KDE.

---

### Post by Pragmatist on 2006-02-08
Thanks for replying.  Your right, that wasn't really what I was looking for.  On the other hand, I'm not wedded to GNOME.

I've been trying out KDE and it wasn't hard to stop the tooltips (although, I had to do it in a few different places).  However, now I have this bouncing icon mouse trailing thing.  Every time I fire an app from an icon I get a mini version of the icon moving like a bouncing ball along with my mouse.  Try as I might I can't seem to get rid of this!  Out of the fire and into the frying pan!!  

Why can't they make it easy to disable functions.  I know that KDE/GNOME are catering to a wide audience and try to be user friendly.  I know they are Desktop Environments which, by definition, are trying to create a uniform look & feel, and are meant to be less configurable than just a window manager.  Still, they give many options for individuals to tweak their own environmentis. Is it really so technically difficult to allow people to turn these features off!

---

### Post by xtacocorex on 2006-02-08
[QUOTE=Pragmatist]However, now I have this bouncing icon mouse trailing thing.[/QUOTE]

This is KDE's launch feedback to let you know that its opening your program or doing a task. Linux is fast at multi-tasking and sometimes the notifications help.

To change it's settings, in kcontrol (KDE's Control Center) under the "Appearance & Themes" there is a section called "Launch Feedback."

---

### Post by Pragmatist on 2006-02-09
Thanks. When I run it in a terminal by typing kcontrol, or running it from Debian-->Apps-->System  or running by left-clicking to the right of the K menu, my choices aren't saved.  This is true even if I log out AND even if I run kcontrol as root!  When I login as root, I can make the changes and get them to stick.  How do I make the changes stay for my regular user account.  Thank you.

---

