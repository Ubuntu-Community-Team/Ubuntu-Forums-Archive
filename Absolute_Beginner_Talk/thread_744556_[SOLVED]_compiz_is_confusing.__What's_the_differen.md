---
title: "[SOLVED] compiz is confusing.  What's the difference between a workspace and a deskto"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Meph1st0 on 2008-04-03
This is fairly difficult problem to describe, so please bear with me.

I've somehow fallen into a new desktop black hole where there's nothing on my screen besides my wallpaper.  I was typing a very important document on "desktop1" and then for some reason I decided to move over to the workspace to my right using the workspace switcher at the bottom right corner of my screen.  When I clicked there, it flipped over and now I don't have any toolbars  on the top or bottom of my screen.  When I try Ctl+Alt and mouse 1 to see the cube, I don't see the original "desktop" I was working on that has my very important document.  If I press ctl+Alt Left or Right I just move to another blank desktop with only my wallpaper.

I've obviously  managed to open up firefox by pressing alt+f2 and typing in firefox.  But if I were to right click on the title bar and click move to workspace right or left my browser would disappear and go to that desktop, but I have no way of finding it again.  The cube shows nothing but four blank desktops.

In CCSM on the General options section on the desktop size tab I had:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 4

I just tried changing Number of Desktops to 1 and that didn't seem to help me.  I have basically a missing desktop with a very important document opened that I haven't saved yet.  Alt+Tab doesn't seem to show anything more than what I can currently see on my current desktop or workspace or whatever it's called.  Can someone please help me?

---

### Post by AdrianStrays on 2008-04-03
So I guess you're on Desktop....zero? lol.  Sorry, I'm not a tech guy, I just accidently clicked your post.

---

### Post by Victormd on 2008-04-03
This might be a long shot, but try CTRL+ALT+F2 (this will take you to a terminal tty2), then CTRL+ALT+F7 (this will bring you back to tty7 - desktop).  Don't worry, this will not act like CTRL+ALT+Backspace.

---

### Post by Doorslammer on 2008-04-03
Ctrl + Esc   that brings up the prosses window & you can kill ccsm

---

### Post by Meph1st0 on 2008-04-03
Doorslammer,
For some reason Ctl+Esc doesn't bring up the process window for me.  Although I'm sure that'd be very helpful to me.  If I could kill ccsm through the command line maybe that'd do it.  I've learned that Ctl+Alt+F2 takes me to the terminal (thanks Victormd).  

Victormd,
Doing Ctl+Alt+F2 and then F7 back to the desktop didn't do it for me.  It brought me right back to the current desktop that I'm on now.

Any other ideas?

---

### Post by Meph1st0 on 2008-04-03
I hate to bump too soon, but I'm still stuck in limbo.  

Another quick question though.  Am I supposed to be able to right-click on the desktop?  I think I am, but I can't at the moment.  No context menu's appear.

---

### Post by Victormd on 2008-04-03
Have you tried using "top" to see what's running? Just go to the terminal and type top and that will give you a list of all processes running. This is just to check if your document is still running. Then you can kill the aplications that may or may not be causing the problems... :)

Just a thought, have you tried killing compiz?

---

### Post by MountainX on 2008-04-03
It sounds like something in gnome (the panel?) may have crashed on you.

You can see all your desktops at once with the "super" key + E (the super key is labeled "windows" on my keyboard).

Try alt+tab to switch among running apps.

Try top to look for the running process. There ought to be some way to bring it to focus...

---

### Post by forrestcupp on 2008-04-03
Here's something you could try.  Get to a terminal and type
```
sudo apt-get install wmctrl
```
If you don't know how to get to a terminal, press alt-F2 and type **gnome-terminal**.

wmctrl is a program that lets you control windows and desktops with the command line.  Then in the terminal, you can type
```
wmctrl -s *desktopnumber*
```
substituting a number 0-3 to switch to that desktop.

I don't know if it will work, but it's worth a shot.

---

### Post by Meph1st0 on 2008-04-03
Alright, well, I think i've made it worse by killing compiz using top (actually I killed a process called compiz.real).  Now I can do even less.  The title bar on firefox has dissappeared and I can't move the window, nor can I press Alt+f2 anymore to able to open any new programs.  I'm still able to press Ctl+Alt+F2 to get to a terminal and I installed wmctrl, but without the ability to open a terminal by using Alt+F2 gnome-terminal I can't manipulate my desktops.  

I have tried Alt-Tab, Super-Tab, and Alt-E and none of them gave me the option of selecting my word processor again.

well...I guess I gotta just bite the bullet and hit ctl+alt+backspace.  I can type up my document again, it's not the end of the world.  Thanks again for all your help.  

It seems, however, that I need to fix my compiz configuration somehow so that this doesn't happen, otherwise, I won't want to use any additional desktops for fear of falling into this problem again.  

So is there a difference between a desktop and a workspace when it comes to Compiz?  Or am I just totally confused?

---

### Post by Victormd on 2008-04-03
you can still move the windows holding the ALT key as you click and drag... As for not being able to open the terminal, that's weird... the "run application" window might be opening behind your firefox window...

Hope you get this solved..

---

### Post by Meph1st0 on 2008-04-03
alright, well...I've done it.  In fact, after hitting Ctl+Alt+Backspace the screen just went blank and didn't come back.  I tried ctl+alt+f2, f1, f7 and nothing (that I know of) would work after that.  So...the power button got pushed. 

I'm back up and running now though, and I'll be sure to save often.  Thanks again everyone.

---

### Post by forrestcupp on 2008-04-04
You're better off in your compiz settings to leave the desktops set to 1 and the Horizontal Virtual Size set to 4.  Then for the sake of never having that happen again, use ctrl+alt+right/left to change work spaces instead of your workspace switcher.

---

### Post by MountainX on 2008-04-04
> **Meph1st0 said:**
> alright, well...I've done it.  In fact, after hitting Ctl+Alt+Backspace the screen just went blank and didn't come back.  I tried ctl+alt+f2, f1, f7 and nothing (that I know of) would work after that.  So...the power button got pushed. 

I'm back up and running now though, and I'll be sure to save often.  Thanks again everyone.

I'm sure you now understand that hitting Ctl+Alt+Backspace was not what you wanted to do. I thought I read earlier in this thread that people said not to do that. It restarts X and that results in loss of any unsaved data in a GUI application. Sorry to hear you lost your work. That is never fun.

---

