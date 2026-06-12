---
title: "Problems with installing programs"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by kane77 on 2005-10-14
I installed Ubuntu and I realy like it.
However I have couple of problems:
1. I downloaded a program for Linux (it was written it could be compiled for all versions). It looked stg like hamachi-version.tar.gz and when I opened there were bunch of files. I tried following the readme but even the first step failed... (
 "To install hamachi in /usr/bin run the following command from under the root account              make install" I´ve tried this and I got answer that make is not a command... What am I doing wrong. How could I install this program?
2. I have problem with Licq... I installed it... but it runs only in text version... How do I make it look something like windows´?
3. I have downloaded skypexxxxxx.deb. I used sudo dpkg skypexxxxx.deb, it starts installing but then just returns error, that I´m missing a file (or program) libqt3c102-mt how do I get this file (it´s not in package manager)
4. I installed some programs using the package manager but it didn´t create shortcuts for those installed programs. Is there any way to make those shortcuts automaticly? It was a lot of stuff I installed and I don´t even know where the installed programs are....

I have a lot of questions I know but if you know an answer to any of them please post it here... THX

---

### Post by LHZ on 2005-10-14
I can't anwser everything, but I'll share what I know (isn't Ubuntu all about sharing?):

1) In order to compile anything you need a compiler program like gcc (GNU C Compiler), which you probably don't have yet. Try installing gcc through Synaptic, or type this into the command line:

> sudo apt-get install build-essential

You should be able to use 'make' afterwards.

4) Not all programs add themselves unfortunately. You can find a tutorial [here]("http://www.ubuntuforums.org/showthread.php?t=32220")

on how to install a menu item which tracks all your installed software.

Hope this helps!

---

### Post by davmac on 2005-10-14
...and I'll have a go at answering question 3 and 4...

3. Have you seen the instructions for installing skype at [http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)? This should give you the info you need about adding the relevant repositories and installing libqt3c102-mt.

4. Not all programs get shortcuts created automatically. Even when they are created, you need to restart the gnome-panel. Do this by opening up a terminal and typing "killall gnome-panel".

If this doesn't to do then you'll need to add the shortcut yourself. Make sure you've got smeg installed "sudo apt-get install smeg". This will add a shortcut for you on Applications -> System Tools -> Application Menu Editor.

Hope this helps,

Dave MacLeod

---

### Post by kane77 on 2005-10-14
THX a lot... you helped a lot...
yes actualy Linux is about sharing with others and that is what appeals to me... (remember what mom said to you: "you have to share!"...) The thought that we together make a chomunity... Now I'm recieving, but I hope one day I'll be able to offer my advices...

Once again thanx a lot...

---

