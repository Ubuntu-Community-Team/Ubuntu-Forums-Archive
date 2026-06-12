---
title: "Changing some thing in  the theme"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by CameronCalver on 2006-06-09
I have  couple of things that i would like

1: i downloaded a theme which i loved but the scroll bar is very blended in to everything because it is light grey on white
so can i modiy just that part of the theme so i can see the scroll bar properly

2:  i love it on some screen shots it has the hard drive icon which just goes to / on there hard drive so when i go places then computer can i change that icon to look like the macs icon

---

### Post by ahaslam on 2006-06-10
[QUOTE=CameronCalver]I have  couple of things that i would like

1: i downloaded a theme which i loved but the scroll bar is very blended in to everything because it is light grey on white
so can i modiy just that part of the theme so i can see the scroll bar properly

2:  i love it on some screen shots it has the hard drive icon which just goes to / on there hard drive so when i go places then computer can i change that icon to look like the macs icon[/QUOTE]
This is something that I found tricky a week or two ago, but I've just customised an entire theme quite easily.

If you go to your home directory and select 'show hidden files' under 'view', you will have a folder named '.themes'. Open this folder, select the theme to be modified. The files that you're interested in should be under the 'gtk-2.0' folder. Make a copy of the image to be modified and use GIMP to edit it to your needs. A 'killall gnome-panel' or restart will make use of your new file.

If your files are not there, try under /usr/share/themes/
If the theme folder can be located, but there is no '.png' files to be seen, only a 'gtkrc' file, things will be harder and a case of trial & error, by changing colours, thickneses, etc and by commenting things out.

If you have all the '.png' files, you're in luck and in for an enjoyable experience.

If you want to change the odd icon, they can be found in '.icons' in your home directory, or under /usr/share/icons/ 

I hope this helps,
Tony.

P.S. I've got a link that may help: [http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

---

