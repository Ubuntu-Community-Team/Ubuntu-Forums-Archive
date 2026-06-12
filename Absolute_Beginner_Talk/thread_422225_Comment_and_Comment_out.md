---
title: "Comment and Comment out"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by bodycoach2 on 2007-04-25
I've been using Linux for over a year now, and I still don't quite get how this "commenting" works. I read on the forums, "Comment out *such-and-such*. That's fine and dandy, if you already know what 'comment' means. 

Could someone explain what 'comment' is, what it does, and HOW to do it properly. If possible, so some before and after examples. 

This would be GREATLY appreciated. I've wrecked two systems by not understand the whole 'comment' thing.

---

### Post by machoo02 on 2007-04-25
"Comment" means to place a special character in front of a body of text in a file (e.g., /etc/X11/xorg.conf) that will be ignored by a program that acts on said file.  Open up xorg.conf...you should see a number of lines of text that are preceeded by '#' (without the quotes).  When the Xserver is parsing the configuration file to set up your X session, it skips over any line that contains #.  When someone suggests to comment out a line in a configuration file, placing # at the start of the line is generally what they mean.

hope this helps

---

### Post by Sef on 2007-04-25
To see some lines commented out, check your sources list:

Applications > Accessories > Terminal

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by nanotube on 2007-04-25
to give a more concrete example, as you ask, let's say this is an excerpt from your xorg.conf:
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

```

note that the lines starting with # just have some general text in them - they are there for the user to read, but not for the parser to actually do anything about. 

now, let's say someone says "comment out your inputdevice configured mouse line". what you would do is place a # in front of that line, so that your file would now look like this:
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
#        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

```

in effect, this is the same as just deleting this line, but this makes it easier to bring it back (simply by removing the #), whereas if you deleted it and wanted to bring it back, you would have to (1) remember where it goes (2) remember what it was (3) retype it by hand. so, commenting just beats deleting. :)

---

### Post by Drewski on 2007-04-25
A "comment" is a chunk of text that will be ignored, in this case by the operating system.

In programming, when you comment something out, you make that something invisible to the compiler, so that piece of code won't get compiled.

Commenting is a good way of taking things out without actually deleting them, so in case you need them back later down the road, you can just UNcomment them and there they are. Although commenting is typically done to do as its name implies: to add a comment. i.e. if you open up some configuration files in Linux you'll see some plain-text English at the top explaining what certain things in the file do. Now if this text wasn't commented, the OS would try to process it, which of course would result in an error.

---

### Post by BoneKracker on 2007-04-25
There should be some kind of medal for being able to use Linux for year without editing configuration files.  This is truly evidence that one can now just about run Linux entirely from a GUI.

---

### Post by blackened on 2007-04-25
Most programming languages give you the ability to add comments to your code. Comments can serve a few different functions: they can serve as quick reminders as to what a section of code is accomplishing, they can help clarify the purpose of sections of code when read by others, and they can be used to debug code by giving one the ability to keep select lines or sections from being parsed (this is what is referred to as commenting out).

Usually in configuration files comments are preceded by a hash symbol (or pound sign to some). Following are excerpts from /etc/apt/sources.list.

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
```

Now, because the first two lines are preceded by hash symbols, when the system reads the file, essentially all it will read is this:
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
```

Hope this clears things up a bit.

---

### Post by BoneKracker on 2007-04-25
Now you need to tell him what "parsed" means.
:)

---

### Post by bodycoach2 on 2007-04-25
> **BoneKracker said:**
> There should be some kind of medal for being able to use Linux for year without editing configuration files.  This is truly evidence that one can now just about run Linux entirely from a GUI.

Even better: My girlfriend has used Ubuntu for almost a year now. She's thinks a terminal is something at an airport, and The Command Line is a rarely seen audio animatronic show at the rarely open Wonders of Life at Epcot (we have Disney annual passes). She's never seen or had to use either on her machine. THAT says something about how far Linux has progressed.

[B]Everyone[B]: Thanks for your....comments (had to use that one). Makes MUCH more sense now. It really is as simple as putting a # in front of a line, it seems. This seems to be a big thing you need to master for some wireless issues.

I greatly appreciate the responses.

---

