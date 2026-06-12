---
title: "Hosed my Gnome"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Jackrum on 2007-11-23
After a week of not using my computer, I returned to find after logging into gnome, my session would hang after about 15-20 seconds. I could use the keyboard to navigate my desktop icons, and could move the mouse around, buty could not access the menu bar, or click anything with my mouse. Opening folders by navigating with the keyboard was OK.  After launching in failsafe terminal and poking around on the forums I moved the contents of my home folder to a temporary folder, the moved them back once gnome launched in its default configuration, leaving out any .gnome or .gtk or similar files. It's working fine now, but I would LOVE to be able to reimport my settings again. ( I had done a LOT of Compiz tweaking). I don't REMEMBER changing anything specific the day I last used the PC< but you know how that goes.  So my question is this:
Is there a log file that will tell me EXACTLY what gnome was trying to do when it hung? Or, alternately, can anyone suggest what it might have been loading at that point? It was enough time to open a firefox window and navigate to a web site, or to access a file several directories deep on my secondary hard drive, all with no issues. The issue occurs at a preset time - it locks up whether I touch nothing, or whether I am running an application, so it doesn't seem to be anything being called by an application or the window manager. 
The naughty file lives in one of the following:
.gconf
.gconfd
.gnome
.gnome2
.gnome2_private
settings.ini
.gtkrc-1.2-gnome2
.profile

as these are the only files I left out to get it back up and running. Any ideas would be appreciated.

---

### Post by spiderbatdad on 2007-11-23
sounds like you're in a gnome session with comipz windows manager but no emerald theme.
maybe
try Alt+f2 then enter metacity --replace
and reboot your system
just my thoughts.and probably not the answer you're looking for?

---

### Post by Jackrum on 2007-11-27
Well, I successfully moved .gconf and .gconfd back over, can still log in, and have all the woders of Compiz back and making my Winders friends jealous. I guess whatever broke I can live without.

---

