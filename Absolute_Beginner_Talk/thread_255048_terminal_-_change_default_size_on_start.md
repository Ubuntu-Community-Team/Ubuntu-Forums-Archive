---
title: "terminal - change default size on start ?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-09-10
is it possible to change the default size of terminal window when i start it?
if so how?

thnx in advance

---

### Post by aysiu on 2006-09-10
Try something like this: ```
gnome-terminal --geometry 1024x768
```

---

### Post by jordanmthomas on 2006-09-10
heh, I was trying to figure it out and I did this:
```

gnome-terminal --geometry=1024x768

```
...dang java making me put equal signs everywhere

Anyway, this crashed my X Session (I have compiz, maybe that has to do with it...I don't know)
Any ideas why this would rape my computer so hard?

---

### Post by zekopeko on 2006-09-10
no good. i type that in terminal and it just opens a new terminal and expands it over the edge of the screen(even with smaller resolution(i'm using xgl/compiz if that has anything to do with this strange behavior)).

i know putty has a setting so that it always opens in size specified by me.

i have a background picture and it doesn't do it justice if the terminal opens in 320x240 or whatever the default resolution is.

---

### Post by jordanmthomas on 2006-09-10
try this maybe?
```
gnome-terminal --geometry 1024x768+0+0
```
According to man X (7)
this is what the geometry should look like.

**edit**
arrrgg, that made me crash too.

---

### Post by zekopeko on 2006-09-10
> **edit**
arrrgg, that made me crash too.

:-D LOL!!!

---

### Post by Bill_MI on 2006-09-10
Bravo!  Been wanting to do this when I get a chance.  I found the problem - the geometry is *character* based, not pixel.

```
gnome-terminal --geometry 120x50
```

This makes a nice size on my 1600x1200 desktop.  I'm sure actual size depends on font setting.

Notice when you drag a terminal corner the character size is displayed - a good way to determine the size you want.

---

### Post by Najand on 2006-09-10
If it is  just terminal size
```
setterm
```
with some options would be enough.

---

### Post by jordanmthomas on 2006-09-10
Character based...that makes sense.  It also makes sense as to why that would break too.
I forgot the terminal told you how big it was when you resized it because it doesn't do it in compiz (which I have been using for some time now)

---

### Post by zekopeko on 2006-09-11
ok so i have:

gnome-terminal --geometry 125x33

but how do i make it always open in that size?

is there some config file for gnome terminal that i could edit?

EDIT:

so i remembered that i could set terminal commands for my icons/app launchers but i would like some kind of a global setting for all of my gnome-settings

---

### Post by Bill_MI on 2006-09-11
> **zekopeko said:**
> ... but i would like some kind of a global setting for all of my gnome-settingsThe "default" configuration for gnome-terminal for a user appears to be in:

(home)/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml

Perhaps editing this file would work?  Before I hose something, can someone confirm an entry would work or... is that asking for trouble to manually edit this file?

Also, I've been trying to understand exactly why gnome-terminal goes here to get the config?  Hardcoded in the executable?

EDIT: I tried adding this:
```
        <entry name="geometry" mtime="1156703958" type="string">
                <stringvalue>125X60</stringvalue>
        </entry>
```... but no dice. ](*,)

---

### Post by jordanmthomas on 2006-09-11
Bill_MI, try running this
```

gconf-editor /apps/gnome-terminal

```

It's going here to load its settings.  The only settings it has are here as far as I know.

---

### Post by Bill_MI on 2006-09-12
Thanks, Jordan.  I do want to understand beyond gnome-terminal a bit.  These configuration keys are a big jump.  I see they're not implicit files, but a pseudo-structure.

Now, if there's a key entry to change gnome-terminal default geometry of 80x24 - this would be a good place to put it.

---

### Post by moore.bryan on 2006-09-12
*the simple way i found was to make a .Xdefaults file in the home dir and specify everything in there.  for a while i was using aterm and that's the way you're "supposed" to do it with them, but then changed back to xterm and the same thing works.  in the .Xdefaults file, put ```
xterm*vt100.geometry:WxH+h+v
``` where W=width, H=height, h=horizontal position, v=vertical position.  running openbox and pypanel, i find 0,0 positioning places the terminal under pypanel, so you may need to play around with it.*

---

### Post by argie on 2006-09-12
I use devilspie, it has simple rules to set window size and other stuff. For example, on my fourth workspace I have a terminal which is always 700x900.

Maybe that maybe unnecessary if this is already implemented by default. But devilspie is a nice little thing anyway. It's in the repos and there's a HowTo somewhere here.

---

### Post by Bill_MI on 2006-09-13
> **moore.bryan said:**
> the simple way i found was to make a .Xdefaults file in the home dir and specify everything in there.Excellent solution for xterm!

Do I understand correctly that xterm, the executable, seeks .Xdefaults for global settings and gnome-terminal, the executable, probably does not?

It appears a lot of programs use settings in .Xdefaults.  I tried a few formats to see if I could influence gnome-terminal from .Xdefaults but nothing found.

Thanks, Argie, devilspie looks like something I'll be investigating in general.

---

### Post by moore.bryan on 2006-09-13
*not a fan of gnome-terminal... i had a really ancient pc before, running breezy and with almost no ram, and g-t locked it up.  that's when i switched to xterm.  the idea for the .Xdefaults file i took from an aterm forum about making it pseudo-transparent.  i figured if it worked for one simple text editor, it should work for another; luckily i was right.  maybe we should start a list of all the programs one can control with an .Xdefaults file?  ;-)*

---

### Post by mejrum on 2006-09-20
To change general startup size

program/system tools/configuration editor
(this menu may need to be activated in alacarte)

go to desktop/gnome/applications/terminal 
edit the value "exec" from 
"gnome-terminal" 
to
"gnome-terminal --geometry=80x50"

---

### Post by Anthem on 2007-09-26
Hmm, my old bug report got merged with your new one.  Regardless, this has once again been ruled "not a bug."  It's a feature!



I know what you're thinking, and you're right.

---

### Post by kbchoi on 2007-12-18
On Gutsy,

System -> Preferred Applications -> System(tab)

There choose Custom and type in

Command: gnome-terminal --geometry=120x30

---

### Post by Shin2010 on 2008-03-12
> **jordanmthomas said:**
> heh, I was trying to figure it out and I did this:
```

gnome-terminal --geometry=1024x768

```
...dang java making me put equal signs everywhere

Anyway, this crashed my X Session (I have compiz, maybe that has to do with it...I don't know)
Any ideas why this would rape my computer so hard?

There is a easy way, it is by making a short cut on your desktop or panel. Then Right clicking it, go down to properties then you put the" --geometry=1024x768 " in the command so it will look like " gnome-terminal --geometry=1024x768 ". So far it has worked for me. :)

---

### Post by mantat on 2008-03-21
goto
System -> Preferred Applications 
Inthe System tab, it let u edit the terminal, just put 
gnome-terminal --geometry=1024x768

mantat

---

