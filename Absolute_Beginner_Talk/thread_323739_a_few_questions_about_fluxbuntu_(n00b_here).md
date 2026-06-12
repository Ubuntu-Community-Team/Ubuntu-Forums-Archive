---
title: "a few questions about fluxbuntu (n00b here)"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-22
If I were to install fluxbuntu, would I install apps like xmms, mplayer, etc. by using sudo apt-get install or is there a different command.  Also is fluxbuntu just like ubuntu except with the fluxbox window manager?

---

### Post by Adrenal on 2006-12-22
You'd use apt-get like normal, and fluxbuntu is just ubuntu with fluxbox

---

### Post by bodhi.zazen on 2006-12-22
Fluxbuntu is *NOT* Ubuntu + fluxbox

Fluxbuntu is more like a server install + fluxbox. Many packages and servers have been removed.

Performance is better.

If you need/want more applications with Fluxbutnu, yes, just aptitude, apt=-get, or synaptic.

---

### Post by maxamillion on 2006-12-22
Fluxbuntu isn't actually "just ubuntu with fluxbox" the same way xubuntu isn't "just ubuntu with xfce" and kubuntu not "just ubuntu with kde" ..... I really don't mean to be rude, just annoyed with this misconception.

---

### Post by zetsumei on 2006-12-22
if i got a working ubuntu, but want fluxbox should i install fluxbuntu?

keep in mind that the fluxbox i installed in ubuntu is f**ked, it doesnt say any settings and ive followed the guides here...

---

### Post by bodhi.zazen on 2006-12-22
Fluxbuntu is a live CD.

If you like it, go ahead and install it. You will need to install it on to it's own partition rather then "on top" of Ubuntu.

If you want Ubuntu + fluxbox install fluxbox. Rox may also help (fluxbuntu runs Rox-desktop by default...  Rox will do backgrounds and icons).

If you would like help with Fluxbox, what problem are you having exactly ???

---

### Post by zetsumei on 2006-12-22
the main problem im having w/fluxbox is its not saving my wallpaper, and settings...

i have all the correct commands in the startup file but it just doesnt save them...

---

### Post by bodhi.zazen on 2006-12-22
What version of Fluxbox ?

```
fluxbox --version
```

And what modifications have you made to startup?

Just background, or themes as well ?

---

### Post by zetsumei on 2006-12-22
just backgrounds mostly and startup apps...im using the newest version of fluxbox...

heres my startup file

> 
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
fbsetbg -l
gnome-volume-manager &
xscreensaver -nosplash &
gdesklets &
gaim &

---

### Post by bodhi.zazen on 2006-12-22
For background you need to modify ~/.fluxbox/init

You can only have 1 "rootcommand" line in init.

Change your init line to:

> session.screen0.rootCommand:    fbsetbg -l

And install Eterm if you have not already (Eterm is yet another terminal)

If you have Fluxbox-1.0-RC2 backgrounds no longer change with theme changes....

See here for setting bachgrounds the "easy way":

[Set BG easy way](http://community.fluxbuntu.org/index.php?&topic=98.0)

And here: [Set BG image](http://community.fluxbuntu.org/index.php?&topic=41.0)

For startup issues post

~/.fluxbox/startup

and questions/problems

---

### Post by bodhi.zazen on 2006-12-22
> **zetsumei said:**
> just backgrounds mostly and startup apps...im using the newest version of fluxbox...

heres my startup file

Use the full path to your programs rather then program name.

Also I do not use exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

I think you should move fbsetbg -l to init as above

else you look fine :)

---

### Post by zetsumei on 2006-12-22
the set bg the easy way, what file do i need to edit?

what do you use instead of /usr/local/bin/fluxbox -log ~/.fluxbox/log?

---

### Post by bodhi.zazen on 2006-12-22
To set BG easy way edit

~/.fluxbox/menu

although most fluxbox users use a customized menu.

I use a short menu only with a terminal and programs I use daily. That "debian" menu is ugly, crowded, and I will launch that stuff from a terminal or a mini-command line ....

See this thread: [fluxbox menu](http://community.fluxbuntu.org/index.php?&topic=36.0)

For /usr/local/bin/fluxbox -log ~/.fluxbox/log, well what do you need a log for ? If you can not answer this question, don't run a log, I don't ....

---

### Post by zetsumei on 2006-12-22
the guide i followed had that in it -_- so its ok to take it out?

and i found the menu file...

---

### Post by bodhi.zazen on 2006-12-22
Yep, remove away.

Removing gunk is the first step to a cleaner, leaner system. :mrgreen:

for config files, including fluxbox, do not delete, comment out by adding  # at the start of a line.

Like this:

# exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

Same with your menu ;)

Lines commented out will not be run, but you can easily re-instate them if you like by removing the #

If you delete the line how will you remember what you have changed ? :-k

---

### Post by ciscosurfer on 2006-12-22
> **bodhi.zazen said:**
> [...]If you want Ubuntu + fluxbox install fluxbox. Rox may also help (fluxbuntu runs Rox-desktop by default...  Rox will do backgrounds and icons).[...]Nautilus can do backgrounds and icons as well. :D

---

### Post by bodhi.zazen on 2006-12-22
> **ciscosurfer said:**
> Nautilus can do backgrounds and icons as well. :D

Hey, thanks for the tip :)

---

### Post by zetsumei on 2006-12-22
wheres the screenshot for this forum?  i took out most of the stuff and just put in my apps and bgs

---

### Post by bodhi.zazen on 2006-12-22
You have to take a screen shot and post it yourself :)

I hope you are up and running with Fluxbox :D

I gotta go for now, I'll check in later.

---

### Post by zetsumei on 2006-12-22
thanks for the help and links...im set for now XD

---

### Post by ciscosurfer on 2006-12-22
> **bodhi.zazen said:**
> Hey, thanks for the tip I know this is a slight digression from the OP topic, but in case you were wondering, to modify Nautilus' settings (thoroughly), you can use gconftool or enter in the appropriate sections within gconf-editor (gconftool modifies settings within gconf-editor, aka Configuration Editor).  So, for example, if you want to see if you have advanced permissions set for the file property dialog, then you can issue:```
gconftool-2 -g /apps/nautilus/preferences/show_advanced_permissions
```If it is set, it will return True, otherwise it will return False.  Let's say you want advanced permissions enabled, you would issue:```
gconftool-2 -t bool -s /apps/nautilus/preferences/show_advanced_permissions true

***to revert***

gconftool-2 -t bool -s /apps/nautilus/preferences/show_advanced_permissions true
```Now let's say you want to modify the background in Nautilus windows, you would enter:```
gconftool -t bool -s /apps/nautilus/preferences/background_set false

***followed by the background that you'd like to set it with***

gconftool-2 -t string -s /apps/nautilus/preferences/background_filename /home/magic/wallpapers/Fly.Away.jpg

***or maybe you'd like to simply set a color (in hex) instead of picture (there must not already be a picture located in the background_filename key, disable it with a blank expression (i.e., no argument at the end) and you must have background_set enabled to true***

gconftool-2 -t string -s /apps/nautilus/preferences/background_color "#423423"
```There are also ***side_pane*** keys as well (side_pane_background_set, etc., etc.)  Of course, all of these manipulations can be done in the GUI (Configuration Editor), but this is the way to it from the command line.  You can also modify patterns, colors, and emblems in Nautilus under Edit > Backgrounds and Emblems (but you're a bit limited there, which is why the above info is useful).

This was probably way more than you cared to know, but here it is anyhow, in all its glory. Enjoy!

---

