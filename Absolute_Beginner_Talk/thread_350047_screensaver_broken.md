---
title: "screensaver broken"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by jim h on 2007-01-31
I browsed through the screensaver choices and it locked up.  Now when I bring it up in the preferences menu it sits on the last selection (most of them stayed black) and doesn't respond at all, and I have to kill it.  So now I have no idea what it will do.  I guess it didn't like my old graphics board. but I just want to set it to "bllank".
  Due to a (now replaced) bad memory stick I have reloaded ubunto 4 times, please help, let me not have to do it yet again!
  Any suggestions?
  TIA.  Jim

---

### Post by PointSource on 2007-01-31
I don't know if this is any help, but I have also had a lockup of my screensaver when I chose a specific item. I don't know whether it was my video card not having enough memory, hardware compatibility issue or a fault/bug in the screensaver, but the application/process slowed down to an almost stop and I had to wait perhaps 1-2 minutes between each click before it responded.

Has it locked up completely or is it just real slow like mine was?

---

### Post by jim h on 2007-01-31
It acted as if the program had crashed leaving the window on screen.
  What I wanted to do was stop it from doing anything at all, as much as possible, since it doesn't seem to have any way of shutting down the monitor (though X or someone seems to know how to do this).  After all the other grief I am kind of scared to mess with it until I know more about it.

---

### Post by Apollo17 on 2007-03-29
Hey Jim H,

I loaded Ubuntu last Friday night (it is Thursday as I write) and I had not tried any of the screensavers, so I started through the list, testing them to see what they looked like. All were running great, but when I selected Molecules, it locked the computer. Nothing would work, keyboard, mouse, key combinations, the whole 9-yards...At least my power button shut it down.

But now, I have the same problem. The screensaver application is stuck on Molecules so whenever I try to bring up the screensavers it immediately locks my PC.

I am running an older ATI Rage Fury Pro card, and I have no idea if 3-D is enabled.

Did anyone get back with you on how to boot into Gnome safemode and change the screensaver to another one? If so, would you post that here.

Thank you,

Ross
Apollo17

---

### Post by Apollo17 on 2007-03-29
Jim H,

In searching the forum, I found this which helped me fix my system. (I had a similar problem...tried various screensavers, was going along fine, then when I chose "Molecules" it lock up completely - had to shut it off by holding the power button down for a few seconds.)

The posting said you could use The Terminal to go to an editor, and "deselect" the offending screen saver. Here's what I did:

You can fire up the terminal and type:  gconf-editor
The screensaver settings are under: apps > gnome-screensaver (i.e. double click on "Apps", then scroll down to gnome-screensaver and click on it, a window on the right will come up showing the value of various keys, scroll down in it till you see Themes.

Go to Themes and remove the offending one and change it to one that didn't lock up your system (I chose Cosmos), or change the "mode" from "single", to "blank-only". X out of the editor and your terminal window.

Then you should be able to go to Screensavers and choose another one or turn it off completely.

Yeah, I have an ATI Rage Fury Pro card on this old Athlon 900 Mhz PC that I'm using as a test bed for Ubuntu. So I guess the moral of the story is to be careful with Ubuntu and ATI video cards, or at least that is the impression I get from reading the forums.

Good luck,

Ross (Ubuntu newbie - going on 6 days now - wow!) :)

---

