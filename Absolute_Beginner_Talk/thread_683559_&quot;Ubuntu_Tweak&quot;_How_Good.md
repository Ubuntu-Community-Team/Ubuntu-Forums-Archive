---
title: "&quot;Ubuntu Tweak&quot; How Good?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-01-31
HowtoForge has released another tutorial for Ubuntu users.  This one looks particularly interesting and allows one to tweak various settings via a GUI. 

[http://www.howtoforge.com/tweaking-hidden-ubuntu-settings-with-ubuntu-tweak](http://www.howtoforge.com/tweaking-hidden-ubuntu-settings-with-ubuntu-tweak)

Before I try this, I thought I'd ask if anyone on the forum has any experience with "Ubuntu Tweak", good or bad.

---

### Post by Siyfion on 2008-01-31
Looks quite good, but it's nothing you couldn't access otherwise from the System menu.

---

### Post by jflarm on 2008-01-31
"Where do I put the Computer and Trash icons on the desktop through the System menu?"
Edit:
...now I feel stupid...it was just a Drag&Drop from the menu....

---

### Post by derred on 2008-01-31
It looks to me like you could already do all those things form gconf-editor. I think the program just passes params to gconftool anyway. I think it works something like this(for the settings you pass to it, this being just an example):
gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 10"

So it should be safe to use if that's what you were wondering, but I still think you'd be better off opening gconf-editor and learning to use that, since it offers a lot more options and flexibility

---

### Post by Golem XIV on 2008-01-31
I agree with the previous posters, you can use gconf-editor.  If you don't like the command line, you can find it in the menu, but it is disabled by default - run the menu editor and enble it under "System Tools".  It does all that Ubuntu Tweak does and much more, but the downside is that the UI is not too friendly.

---

### Post by Aurora@FleetBuzz on 2008-01-31
Thank you all for your comments.

It seems to me that "Ubuntu Tweak" is definitely a step on the right direction in that most users (well, speaking for myself only!) prefer a GUI to the terminal.  Comparing Ubuntu to XP, how often does one go to the Windows command prompt to do anything?  In my experience, only to troubleshoot my cable modem connection or run "msconfig"; others will undoubtedly have more recourse.

---

### Post by philinux on 2008-01-31
For some of the most wanted tweaks I think it better(easier) to navigate for a new ubuntu user.

---

