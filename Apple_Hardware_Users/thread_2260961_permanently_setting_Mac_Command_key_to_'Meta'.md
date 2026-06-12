---
title: "permanently setting Mac Command key to 'Meta'"
date: 2015-01-15
forum: Apple Hardware Users
---

### Post by svref on 2015-01-15
I have lived a lifetime hitting the key just left of the spacebar, and thinking it'll be "meta", but now I find myself liking this old Mac keyboard, not a PC-104. And Ubuntu thinks the command key is 'alt', not 'meta'. This is driving me insane!

[IMG]http://i105.photobucket.com/albums/m235/dcmorse/IMG_20150115_110739_zps5552da85.jpg[/IMG]

I can temporarily fix the problem by running xmodmap on a file with the following:
```
clear Mod4
keycode 133 = Meta_L
```
(I discovered keycode 133 was the key I needed by using xev)

But this does not permanently affect things. It snaps back to the old behavior every time screen lock comes on. :(

This [thread]("http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04") indicates that xmodmap is not the way to do it anymore, and there is a "more powerful" way to do it with something called "xkb", that's like 50 pages of reading to understand. I don't want to read 50 pages just to get my keyboard working. Does anyone know how to do this?

---

### Post by slickymaster on 2015-01-15
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by svref on 2015-01-18
hm.

---

### Post by svref on 2015-01-19
get a program called "Gnome Tweak Tool"
start it
Under 'typing', Alt/Win key behavior, select "Alt is mapped to Win keys (a...".

---

### Post by svref on 2015-01-19
This page also looked promising:
[http://www.emacswiki.org/emacs/SettingMetaWithXKB](http://www.emacswiki.org/emacs/SettingMetaWithXKB)

---

