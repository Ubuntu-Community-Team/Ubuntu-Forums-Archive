---
title: "[SOLVED] How can I save my desktop manager settings?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-24
I'm using Xfce, but want to try Gnome, IceWM and pretty much any I can find, but I have my stuff the way I like it. Is there a way to save all my toolbar icons and colors and splash screen, etc.

---

### Post by pjkoczan on 2007-12-24
> **EmosSuck777 said:**
> I'm using Xfce, but want to try Gnome, IceWM and pretty much any I can find, but I have my stuff the way I like it. Is there a way to save all my toolbar icons and colors and splash screen, etc.

Xfce settings should be stored in your home directory, something like /home/<username>/.xfce/, but I don't use Xfce, so I couldn't tell you where those settings exactly are (note that a dot preceding the filename makes it "hidden" so you either have to view hidden files in a file browser or add the -a option to ls if you're using a terminal).

You should be able to use Gnome and anything else without affecting your xfce settings, since gnome uses a different set of settings (and are stored under ~/.gnome, among others). I'm not quite sure what you mean by a "splash screen" (background image, maybe?), but that should remain unaffected.

Long story short, use them, your Xfce settings will be safe if you ever want to go back. If you're paranoid, make a backup of the settings (copy whatever .xfce folder you can to a safe place).

---

### Post by urukrama on 2007-12-27
> **pjkoczan said:**
> Xfce settings should be stored in your home directory, something like /home/<username>/.xfce/, but I don't use Xfce, so I couldn't tell you where those settings exactly are 

In case you are looking for them, all Xfce's settings are stored in /home/USERNAME/.config/xfce4/ except for the settings of Xfce-sessions which are stored in /home/USERNAME/.config/xfce4-session/

---

