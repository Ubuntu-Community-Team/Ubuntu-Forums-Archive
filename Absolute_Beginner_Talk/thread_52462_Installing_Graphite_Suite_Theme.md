---
title: "Installing Graphite Suite Theme"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by talkingwires on 2005-07-27
Alright, I must be missing something very obvious:
I'm trying to use [this theme](http://www.gnome-look.org/content/show.php?content=26757&forummode=2&forumpage=5&forumexplevel=2). I downloaded and installed the icons and the provided ClearLooks theme. However, the window decorations don't look a thing like the screenshots. A [post on Slashdot](http://linux.slashdot.org/article.pl?sid=05/07/27/1546233&tid=131&tid=106), where I heard about the theme, says that the screenshots are using the Industrial theme for the borders. A quick check in Synaptic shows that gtk2-engines-industrial is installed, and it appears in the Theme Manager under the Controls tabs, but not the Window Border tabs.

I don't fully understand the difference between GTK Themes and GTK Engines, so I'm a little confused. What am I doing wrong?

---

### Post by sapo on 2005-07-27
I think you are using the version 0.5 of the clearlooks theme...

Open a terminal and do it:

```
gedit ~/.themes/Clearlooks-graphite/gtk-2.0/gtkrc
```

Now find the line 51 and comment it like this:

```
#    menubarstyle      = 0       # 0 = flat, 1 = sunken, 2 = flat gradient
```

Now your theme should be fine  :grin:

---

### Post by talkingwires on 2005-07-28
No, I'm running the latest version. I guess I should have mentioned that I run Breezy. Any other ideas? I really like the look of the theme, but Gnome themes baffle me, which is why I posted in the Newbie Forum.  (Speaking of Breezy, I restarted X, and Gnome is fubar right now. So I'm giving lynx a whirl before I reboot into Windows. Heh.)

---

### Post by ow50 on 2005-07-28
From the theme's page at Gnome-Look:
Q
> Hi,
I'm missing the Metacity theme.
A
> This is the "Office" metacity theme.
link: [http://art.gnome.org/download/themes/metacity/710/MCity-Office_0.7.tar.bz2](http://art.gnome.org/download/themes/metacity/710/MCity-Office_0.7.tar.bz2)
Author:Gianluca Sartori

---

### Post by talkingwires on 2005-07-28
Perfect. Thank you!

---

