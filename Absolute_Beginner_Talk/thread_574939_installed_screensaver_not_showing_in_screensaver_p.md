---
title: "installed screensaver not showing in screensaver preferences"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-10-13
I just downloaded two screensavers with Synaptic but when I open the screensaver preferences menu they are not listed... any ideas?

---

### Post by Pumalite on 2007-10-13
At the Terminal:

xscreensaver

---

### Post by autocrosser on 2007-10-13
If you are using Feisty--the default is Gnome screensaver. It still is not working the way I like (such as your problem) & so I install Xscreensaver.....

There is a good HowTo in the HowTo Forum to convert--you will need to do a bit of terminal work----but it is WELL worth it--Xscreensaver allows config of all your screensavers & is still a better app--Gnome Screensaver is still a "work-in-progress"--sad that it is now the default, but the reason is that Xscreensaver allows too many options----------

---

### Post by mchnhed on 2007-10-20
OK great. I installed xscreensaver and ran "xscreensaver-demo" and enabled the deamon. However, the screensaver that I installed through Synaptic still doesn't show up in the list of available screen savers. I even tried reinstalling it.

Two other questions:

1. Do I always have to run xscreensaver from the terminal to access it? If not, how can I make it my default screensaver manipulation program? (or at least easier to access)

2. How do I make it so that this xscreensaver daemon is always running and/or always has control of my screen saver selection?


THANKS IN ADVANCE.

---

### Post by Pumalite on 2007-10-20
I run it from the Terminal.

---

### Post by autocrosser on 2007-10-20
To run Xscreensaver as a "regular" program & auto-start the daemon:
Menu>System>Preferences>Sessions

Goto the tab:  Startup Programs------Add a new program

Name it whatever you want & then--Command is:

xscreensaver -no-splash

Make the comment whatever you want. OK the edit & close Sessions

Logout & Login & Xscreensaver will start as your default screensaver if you have followed the rest of the HowTo....

To create a HotCorner for your screensaver: Open up Synaptic & search for brightside. After it is installed: Configurable actions--make a custom action & ON entering region: xscreensaver-command -activate (note the space between command & -activate)

On leaving region: Run another command: sleep 5 ; xscreensaver-command -deactivate ( again note the space)...

The only bummer is that you need to uncheck/recheck the command one at the start of your session---brightside is not remembering configs right now.

brightside shows up as Screen Actions in your Preferences menu.

---

