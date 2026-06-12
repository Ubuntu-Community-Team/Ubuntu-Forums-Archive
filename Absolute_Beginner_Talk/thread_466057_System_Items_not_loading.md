---
title: "System Items not loading"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-06-06
Today I was fiddling with my computer and I think I may have messed something up. System items (such as Add/Remove... and others) attempt to load, but the tray prompt that indicates that they are starting, close before they even open. Any ideas?

---

### Post by greenstar on 2007-06-06
Your description of the problem is a bit... spartan. I'm going to have to take a guess as to what is actually going on. Let's see, if I understand you correctly then:

1. Ubuntu boots to the desktop normally
2. When you attempt to start an application, you see the mouse pointer change into the wait swirly (Gnome).
3. The application never actually opens.

Is this correct?

If so, how much physical memory do you have in that PC?

How big is the swap partition?

Greenstar

---

### Post by srt4play on 2007-06-06
Start Add/Remove from a terminal to see if there are any error messages that will give a clue as to what is wrong.

Applications --> Accessories --> Terminal

```
sudo gnome-app-install
```

---

### Post by wcbardwell on 2007-06-06
All of the programs (that I have tried) are loading fine except for Add/remove... and Main Menu (under preferences)... When I try to open them, the window on the stsyem tray says "starting (instert name here)..." The "working" (circle with dots) cursor appears and then the window in the tray closes without the item actually starting. Ubuntu and all other programs are loading fine and the system seems to be running without a hitch.

---

### Post by srt4play on 2007-06-06
Ok, did you try running the command above?  It should give a clue as to why you are seeing this behavior.

---

### Post by greenstar on 2007-06-06
Try sr14play's suggestion. Let us know what the terminal says.

I'm suspecting insufficient RAM/swap so far. I've seen this behavior before. I'm not sure about Add/Remove because I never use that, preferring aptitude at terminal and then synaptic when I need more info. I do know that the menu editor, alacarte,  aka 'Main Menu' has always been a hog. Low memory PC's often refuse to load alacarte, and slow CPU PC's take a loooooong time to load it. This might also be true of Add/Remove, but again I'm not sure about that.

Greenstar

---

### Post by wcbardwell on 2007-06-07
I honestly don't think it's the RAM. I have 2 GB. This is the message it gives me for the command above:

> Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 312, in <module>
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 30, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libX11.so.6: undefined symbol: XdmcpWrap

PLEASE HELP!!!!

---

### Post by greenstar on 2007-06-07
OK, you've got plenty of RAM.

Maybe those 2 apps have been broken. Try reinstalling alacarte (Main Menu):

```
sudo aptitude update
sudo aptitude purge alacarte
sudo aptitude install alacarte
```Now see if alacarte works - test from menu & terminal. If this works, do the same with gnome-app-install (Add/Remove). If this has no effect, then we'll know to look elsewhere for the problem.

Greenstar

---

### Post by wcbardwell on 2007-06-08
That just dug me into a deeper hole! Not only is the "Main Menu" not listed now, but it seems that several others are too. In addition to that, my terminal isn't working either > Failed to execute child process "gnome-terminal" (No such file or directory), CD/DVD creator isn't working> Failed to execute child process "nautilus" (No such file or directory), many other items in the System Preferences aren't working now > Failed to execute child process "gnome-background-properties" (No such file or directory) > Failed to execute child process "gnome-ui-properties" (No such file or directory) , and I am at a total loss for words! That's only what I found in a minute or so. Any Ideas?

---

### Post by srt4play on 2007-06-08
You said in the first post that this happened after "doing some fiddling."  What exactly did you do?

---

### Post by wcbardwell on 2007-06-08
I was trying to install a program called kdenlive (a video editing program). I never got it installed, so i gave up.

---

### Post by greenstar on 2007-06-08
> **srt4play said:**
> You said in the first post that this happened after "doing some fiddling."  What exactly did you do?

I'm positive he was asking for *far* more detail, such as:

What set of instructions were you following?

Where did you find these instructions? Please provide link.

What steps did you take while 'fiddling'? Be specific.

The answer likely lies within.

Greenstar

---

