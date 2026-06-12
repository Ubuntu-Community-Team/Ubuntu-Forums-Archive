---
title: "ps/2 mouse not working, no sound/video"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by J Snyder on 2006-09-09
hi- i installed the latest download release (6.06.1) on a Dell P2 Inspiron 7000. i love the interface and the look, but 2 problems have surfaced: i can no longer use a ps/2 mouse,  and i can't get any sound at all- no beeps,  no mp3's, no nothing.

I tried a couple of different methods for activating my mouse, but no go (the touchpad still works fine); i have the standard installation media player also (rythymbox), and I know i have good mp3 files, but still nothing. no movie files will play, either- not wmv or mpg.

I'm a complete newbie at changing codes and editing registry stuff, so please go easy on me!

Thanks for your help--

---

### Post by bodhi.zazen on 2006-09-09
One thing at at time. 

Sound may be as easy as unmuting (as silly as that sounds). Click on speaker icon on your panel and check volume levels & mute button.

In the program you are using (xmms?) make sure  output is enabled to sound card.

If that fails, in a terminal type
```
alsamixer
``` This should bring up your sound card. Check levels, capture (tab key moves to capture).
Press <escape> to exit.

For the mouse you likely need to edit xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```for backup.

```
gksudo /etc/X11/xorg.conf
```
look for the "Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"

Make sure this has in it like:
```
Section "InputDevice"
	Identifier	"Configured Mouse" **Do not change this line**
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
```

Or try this line:
```
Option		"Protocol" "Auto"
```

Restart X: Ctrl-Alt-Backspace.

Note: this will bring you to the log in screen.

If you misconfigured X you wll not have a gui.

In thes event, log in and:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm stop
sudo gdm
```

You will have your GUI back. Re-post at that point.

---

### Post by J Snyder on 2006-09-10
Okay- sound first.

I have the standard 'rythymbox' music player that comes with the basic installation (6.06.1); it comes up with no problem, but when I select an mp3 file I get a message saying it's not a valid audio stream.

I opened 'alsamixer' in a terminal, and moved the selection to 'capture'- no good. When I went back to it, it was right back on 'playback'. How do I save my selection, or is it supposed to do so on exit?

Also, when I try and open an mp3 file from a USB device, it comes up in the Totem Movie Player and- just as Rythymbox does- I get a message saying I'm missing a proper decoder.

As I said I'm a complete newbie at doing stuff in a terminal mode, so it's entirely possible I'm leaving out something simple I don't know about!

Once I get the sound working I'll start on the ps/2 mouse, but the touchpad is okay for now.

---

### Post by bodhi.zazen on 2006-09-10
> **J Snyder said:**
> I opened 'alsamixer' in a terminal, and moved the selection to 'capture'- no good. When I went back to it, it was right back on 'playback'. How do I save my selection, or is it supposed to do so on exit?

If alsamixer recognized your card you have a software problem.

It sounds as if you need to install some more stuff. See here:

[Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats)

He he he... Do not let the name fool you.

I use xmms so let me give a "walk through" if you sound does not work after you install some restricted formats.

All pull-down menus:
volume control:
```
File -change Device -> Select your sound card.
Click "switches" tab. Select (check box) any "digital/Analog" box. If in doubt, select them all for now.
```
xmms:
```
Preferances -> Click "output plugin" box -> Under "device settings" tab select your sound card. If you do not know, trial and error.
```

Rhythmbox will have a different set of menus, but you get the idea..... 8)

---

### Post by J Snyder on 2006-09-11
Sound/video problem solved- loaded Xmms for mp3's and Gxine for video. Now music from Xmmx and video works through Totem. Not as 'easy' a fix as Windows apps, but I'm still learning.

Now for the mouse...I'm still stuck.:( :(

---

### Post by bodhi.zazen on 2006-09-11
Congratulations. \\:D/

Now:[list=number]
[*]What type of mouse? 2-button, 3-button, etc.
[*]What have you tried to date?
[*]can you post the "Input Device" section of /etc/X11/xorg.conf for your mouse?[/list]
Also, have to ask the obvious, do you know your mouse is working? :)

---

