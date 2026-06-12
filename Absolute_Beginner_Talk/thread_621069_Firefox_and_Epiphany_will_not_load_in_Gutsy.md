---
title: "Firefox and Epiphany will not load in Gutsy"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by markii on 2007-11-23
Problem started yesterday: neither Firefox or Epiphany will load. I attempt to load one of them and it looks as if it will load -a message in the status bar at bottom of screen says "Starting Firefox...", but then it shuts down. Same thing happens with Epiphany, though that gets a little further and asks if I want to resume previous session - then it shuts down. 

Did some updates prior to this problem, but I didn't pay attention what they were.

I'm a complete newbie and I've looked around for help on this and cannot find the answer.

Thanks

---

### Post by Arthur Archnix on 2007-11-23
Open a terminal and type in "firefox" without quotes. If it experiences a problem error messages should show up in the terminal. Those may help you figure out what the problem is. Or just post them here.

---

### Post by daengbo on 2007-11-23
Can you open a terminal, type in "epiphany" and let us know what the error messages are?

Thanks

---

### Post by markii on 2007-11-23
> **Arthur Archnix said:**
> Open a terminal and type in "firefox" without quotes. If it experiences a problem error messages should show up in the terminal. Those may help you figure out what the problem is. Or just post them here.

after typing in firefox in terminal I get the followong message:

Floating point exception (core dumped)
 
After typing in epiphany, the Epiphany Crash Recovery window opens telling me that the last session ended unexpectedly and giving me two options - recover last session or start new session. Whichever I choose it shuts down.

---

### Post by Arthur Archnix on 2007-11-23
[http://ubuntuforums.org/showthread.php?t=365150](http://ubuntuforums.org/showthread.php?t=365150)

Any luck with this link?

The more I read about it the more I think it's a font thing. Installed any new fonts lately?

---

### Post by markii on 2007-11-23
> **Arthur Archnix said:**
> [http://ubuntuforums.org/showthread.php?t=365150](http://ubuntuforums.org/showthread.php?t=365150)

Any luck with this link?

The more I read about it the more I think it's a font thing. Installed any new fonts lately?

I did install new TTF fonts yesterday, but I have no idea how to rectify the situation. I already looked at the link you sent, but cannot find corresponsing folders on my system.

Installed a lot of TTF fonts using KDE Control Module

---

### Post by Arthur Archnix on 2007-11-23
You may need to remove those fonts. Hopefully the instructions you followed told you to copy them to a directory in your home then regenerate the font cache. If so you can just reverse the directions, delete the fonts from your home dir that you copied in there, and then regenerate the fonts cache again. This should solve the problem.

To check if that's necessary you can hit Alt+F2 and type "firefox -P" without quotes. This tells firefox you want to create a brand new profile. Name it test profiles or something, make sure its selected then try and start it. If it works then following the advice in the link I sent you will probably work. If it still crashes then deleting pref.js probably won't help you need to get rid of those fonts. 

You can search for the file using "locate prefs.js". There's a few of them, but the one under discussion will be in your home folder.

---

### Post by markii on 2007-11-23
deleted the fonts using the program with which I installed them, and now I find OpenOffice will not open either
Synaptic Packet Manager will not open now either. 
Is it worth doing a completely new install?

---

### Post by Arthur Archnix on 2007-11-23
A program to install fonts? What program is that?

---

### Post by markii on 2007-11-23
Font installation program found at:

Applications - Other - Font Installer

I am a moron. I think I have deleted all my system fonts

---

### Post by asmiller-ke6seh on 2007-11-23
> **markii said:**
> Font installation program found at:

Applications - Other - Font Installer

I am a moron. I think I have deleted all my system fonts

You're not a moron ... you just made a mistake. I'm glad that you discovered your mistake. It proves that you are no moron.

Yeah, no system fonts can cause a problem.

Welcome to our world. It's great to have you here.

---

### Post by markii on 2007-11-23
Thanks to everyone who attempted to help me. Off to do a new install.

---

### Post by Arthur Archnix on 2007-11-23
Marki... what might be easier than a clean install, if you're thinking about such a dramatic step, is just to create a new user. Try it out. Create a new user, log in, see if it works. If it does you can copy over your files.

Edit: And I can't find any information about a graphical font installer that ships with ubuntu.

---

### Post by daengbo on 2007-11-23
He mentioned KDE, so it might be Kubuntu

---

