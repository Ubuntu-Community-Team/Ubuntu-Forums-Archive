---
title: "looking for way to inject synthetic keystrokes into in-focus application"
date: 2015-02-14
forum: Assistive Technology &amp; Accessibility
---

### Post by Eric_Johansson on 2015-02-14
I'm trying to use NaturallySpeaking on windows to drive an ubuntu system.  the windows system has an ssh connection to the ubuntu system. the ssh connection has window focus and NaturallySpeaking sends it's output to it.  the ubuntu side sees the NaturallySpeaking output as characters on stdin.  I need info on how to send stdin to the input queue  of the ubuntu system.  I've tried uinput but I can't find the kernel module.  

what are my options for injecting a character stream into the input queue?

thanks!
--- eric

---

### Post by TheFu on 2015-02-15
Most Linux programs accept piped input. That can be from a file or from an input stream.  This is part of the Unix design philosophy. You've probably seen this many times.

**ls /usr/bin | more**   is an example.

Of course, of the program receiving the input needs to accept it.
BTW, it is possible to redirect the stdout from 1 program lots of places - named pipes, fifos, stdin, or just a log file.  The "tee" program can replicate output to other locations if you need it in 2.

Or am I completely missing the point?

---

### Post by Eric_Johansson on 2015-02-15
I'm really sorry but you are completely missing the point. The simplest way to think of the request is how do you create synthetic keystrokes i.e. simulate being a keyboard) from a series of characters such as text accepted through standard in or a string.

---

### Post by TheFu on 2015-02-15
Something like expect?
or autohotkey?  

Perhaps something like this [http://alternativeto.net/software/autohotkey/?platform=linux](http://alternativeto.net/software/autohotkey/?platform=linux) ?  Be certain to use the widgetID, not an x,y location.  X/Windows testing tools have done this for decades.

---

### Post by Eric_Johansson on 2015-02-15
Auto hotkey looks like I may build a force it to work the way I need it. However I suspect using it would be roughly analogous to using the heat of your engine to cook a meal. I'll take a look at the source code and see what I can extract.

---

