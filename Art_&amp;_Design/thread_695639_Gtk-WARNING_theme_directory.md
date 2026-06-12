---
title: "Gtk-WARNING theme directory"
date: 2008-02-13
forum: Art &amp; Design
---

### Post by diskotek on 2008-02-13
i have a strange warning when i'm trying to open "gedit" as root from terminal. i downloaded and install ".deb" package of "gartoons" iconset via gnomelook. is it something easily fixable?

```
(gedit:6447): Gtk-WARNING **: Theme directory 22x22/places of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/status of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/document of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/form of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/generic of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/io of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/media of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/navigation of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/net of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 22x22/stock/text of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/actions of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/apps of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/categories of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/emblems of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/extras of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/filesystems of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/gnome-mime of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/gtk of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/mimetypes of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/places of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/status of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/document of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/form of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/generic of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/io of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/media of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/navigation of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/net of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 24x24/stock/text of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/actions of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/apps of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/categories of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/emblems of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/extras of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/filesystems of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/gnome-mime of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/gtk of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/mimetypes of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/places of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/status of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/document of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/form of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/generic of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/io of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/media of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/navigation of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/net of theme GartoonRedux has no size field


(gedit:6447): Gtk-WARNING **: Theme directory 32x32/stock/text of theme GartoonRedux has no size field
```

---

### Post by jrib on 2008-02-13
They are just warnings, so you can just ignore them.  If you want to fix the warnings, you need to give the theme what the warning says it is missing.  For example, "Theme directory 22x22/places of theme GartoonRedux has no size field".  You can:

1. Contact the author and see if he will fix it.

Or:

2. Do some research on themes ([http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://live.gnome.org/GnomeArt/Tutorials/IconThemes) maybe) and give everything the missing size field.  And then it would be great if you could contact the author and tell him about it.

---

### Post by diskotek on 2008-02-13
thank you for the reply, i couldn't figure it out throughthe second way. i think i'll contact with the author. i hope /he/she can help. actually, it's just annoying to see...not so important

---

### Post by hyperair on 2008-02-13
Well you're not supposed to start GTK apps from the command line are you? You're supposed to run them from the menu or something. So it doesn't really matter.

---

### Post by anasofiapaixao on 2008-10-15
:|

I can't discern whether it's a troll or just ignorance, so I'll just answer in a proper way even though anyone who has been on Linux for a while must have been through at least one of these situations: there are n reasons for starting an app from terminal, root or not. On my case:

- I can just run synaptic from a terminal, when searching for something through apt-cache just doesn't cut it and I don't feel like entering my password for the nth time on gksu when I still have the sudo token from the terminal for having recently sudo'ed something.

- Between vim and emacs I prefer gedit, and ANYONE who had to mess with any configuration file (that being anyone who has used linux for more than a week) was told here to sudo gedit something one way or the other.

- Sometimes I need to move/copy/rename several files/folders/bleh which I don't have permission to as a normal user. Some can use the command line  forever and always for the sake of being a purist (read: 1337), but I prefer to be practical: while a command line 'mv' can sometimes be quicker, others it's better to just sudo nautilus your way around.

- Killing and restarting NetworkManager.

Forgive me all for taking the bait to state the obvious, but I had to.

---

### Post by hyperair on 2008-10-19
> **anasofiapaixao said:**
> :|

I can't discern whether it's a troll or just ignorance, so I'll just answer in a proper way even though anyone who has been on Linux for a while must have been through at least one of these situations: there are n reasons for starting an app from terminal, root or not.
My bad. I didn't state what I meant properly. I meant that the general way of opening a GUI app is through the GUI, not through the terminal, but I didn't mean that you couldn't do it at all. My intention was not to troll, and I'd like to believe that I'm not ignorant enough to deserve the reply I just got.

> **anasofiapaixao said:**
> 
 On my case:

- I can just run synaptic from a terminal, when searching for something through apt-cache just doesn't cut it and I don't feel like entering my password for the nth time on gksu when I still have the sudo token from the terminal for having recently sudo'ed something.

Point taken, but I have personally never started Synaptic from terminal. I generally use GNOME Do, and if I've recently gksu'ed something, I don't have to re-type my password, and don't have to clutter my terminal with background tasks or disown Synaptic or lose the terminal for the entire time Synaptic's open

> **anasofiapaixao said:**
> 
- Between vim and emacs I prefer gedit, and ANYONE who had to mess with any configuration file (that being anyone who has used linux for more than a week) was told here to sudo gedit something one way or the other.
Correction: Not everyone has to mess around with configuration files due to Ubuntu's sensible defaults which cater for everyone except the fussiest of users, me included.

> **anasofiapaixao said:**
> 
- Sometimes I need to move/copy/rename several files/folders/bleh which I don't have permission to as a normal user. Some can use the command line  forever and always for the sake of being a purist (read: 1337), but I prefer to be practical: while a command line 'mv' can sometimes be quicker, others it's better to just sudo nautilus your way around.
If that was the case then it's better to use the nautilus-gksu plugin and just right click on a folder, and click 'Open as Administrator', in that case. Either way, if I wanted a root nautilus window, I'd Alt+F2 and do it (or have a launcher handy), not do it in the terminal.

> **anasofiapaixao said:**
> 
- Killing and restarting NetworkManager.

Now, this I don't understand. What I use is:
```
sudo NetworkManager restart
```
or if that didn't work, 
```
sudo killall -9 NetworkManager; sudo NetworkManager start
```
Exactly where does a GUI app come into play here?


> **anasofiapaixao said:**
> 
Forgive me all for taking the bait to state the obvious, but I had to.
Never! :twisted:  Heheh, just kidding. No hard feelings, okay?

---

### Post by mathfeel on 2009-01-17
> **diskotek said:**
> thank you for the reply, i couldn't figure it out throughthe second way. i think i'll contact with the author. i hope /he/she can help. actually, it's just annoying to see...not so important

check the index.theme file in /usr/share/icons/themename/. Make sure under each [16x16/apps] there is a line Size=16

---

### Post by alquirel on 2010-06-19
hi,
i got the same problem now, but i checked my theme index and although the lines you mentioned exist, my problem goes on the same way.

is there any other solution?

thanks.

---

### Post by wyth on 2011-03-10
Probably don't need to point this out, but just in case:

The warning says the "Theme directory" of some theme is missing a size field. Although it says theme, what you want to check is the index.theme file in /usr/share/icons/[your theme], and not the index.theme of /usr/share/themes/[your theme].

So even though it says "theme," you're really looking into the icon directory. The warning is just in regards to the index.theme file.

---

