---
title: "Simple GUI designer"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-23
I'm looking for something very simple - just give me a window and let me drop a couple of very basic elements onto the page (text box, buttons, maybe select a file) and for each action (say, click a button) I want it to execute a command ((like a bash shell script) as if the program was just one big graphical shell script!) :)

so, very simple GUI designer, simple actions execute a shell command.  Simple enough, so, is there something like this? (don't say glade or QT :))

---

### Post by MrHippocampus on 2007-09-23
You could look into zenity, its not exactly what you want (its not a gui designer) but its along the right lines. Basically it allows you to create various gtk dialog boxes (and return information from them) just using shell commands, [this]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/") is a nice site which gives you an idea of how it works/what it can do.

---

### Post by kellemes on 2007-09-23
Not sure if this is what you want, but [Kommander]("http://kommander.kdewebdev.org/") is pretty cool.
For advanced applications if you wish but also very easy create small scripts/apps fast.

---

### Post by ryanVickers on 2007-09-23
Thanks for the tips!

The zenity was really helpful - check out my [Graphical RAR maker]("http://www.hotlinkfiles.com/files/408124_mv1j9/mkrar.sh.tar.gz")!  Just download, extract, and run!

You can also find the the "whole site" in my signature ;)

---

### Post by HermanAB on 2007-09-24
Hmm, it sounds like you want to do a ncurses application:
[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/tools.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/tools.html)

Cheers,

H.

---

