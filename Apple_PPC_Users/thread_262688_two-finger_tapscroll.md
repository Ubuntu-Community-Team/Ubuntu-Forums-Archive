---
title: "two-finger tap/scroll?"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by vik4 on 2006-09-22
Hey,

I've just come across a G4 ibook, and want to use it for running ubuntu, but would _really_ like to get two-finger tap and scrolling happening like on the newer macbooks have in OSX. For OSX, there is iScroll2 which implements this functionality on ADB-type touchpads, as does "Free Focused Scroll". Has anyone had a go at implementing this in linux/x.org ? If not, where would one start? As I understand it, x.org uses the synaptics driver for the ibook trackpads, so would it go in there, or in code for the ADB protocol? (for that matter, I couldn't find any reference to ADB in the synaptics code). 

I'm sure macbook users would like similar functionality too...

ciao

vik

---

### Post by jasonmeansfriend on 2008-01-02
i came across this, hope it helps

this is the particular post with the final version deb package in it,  the defualt to insert into your xong file is:

Option          "MultiFingerButton"     "2"
Option          "MultiFingerLock"       "1"

to
 
Option          "MultiFingerButton"     "2"
Option          "MultiFingerLock"       "0"

[http://ubuntuforums.org/showthread.php?p=3860470#post3860470](http://ubuntuforums.org/showthread.php?p=3860470#post3860470)

but now that i think about it, it's only for synaptics touchpad, which mine is...

well, it worked for me! good luck!

---

### Post by guidop on 2008-01-02
If you have an ADB trackpad, see this thread - you will have to compile a patched kernel:

[http://ubuntuforums.org/showthread.php?t=380884](http://ubuntuforums.org/showthread.php?t=380884)

My post in that thread describes xorg setup steps after installing a patched kernel.
(You may also be able to use the qsynaptics GUI to configure a patched sytem.)

An updated url for the patches, and instructions is:

[http://adbsyn.crisidev.org/](http://adbsyn.crisidev.org/)


I don't think it supports two or three finger touch detection, though.
(At least that seems the case on my 2003 vintage 1GHz PowerBook.)

It does put the ADB trackpad into absolute position mode, however, so that the right and bottom sides can be defined as scroll areas, and the corners can be defined as mouse buttons of your choice.  

The trackpad functionality appears to be similar to the Raging Menace Sidetrack application on OS X, see:

[http://www.ragingmenace.com/software/sidetrack/](http://www.ragingmenace.com/software/sidetrack/)

---

### Post by robiouilliame on 2008-07-08
Hi !

I need some help. I'd kill to have scrolling on my ibookG4 touchpad under linux, that's why i keep using ageing macos 10.3. So i've tried the explainations above, i've patched a 2.6.24-19 kernel and compiled it (Ubuntu 08.04), and my "buggy" touchpad became useless. I tried with a 2.6.23 kernel, but i got the same result. I must have done something wrong, but i can't figure out what. So i keep using my unpatched 2.6.24-19 kernel with it's scrollingless and buggy touchpad.
I can send my .config if it can help.
If you can help another desperate iBookG4 under linux user, i'd be the happiest.

---

### Post by robiouilliame on 2008-07-08
Ooops ! Sorry I bothered you folks ! I was "sure" I had got rid of mouseemu before I came here crying... 
So, all I had to do was to uninstall mouseemu and all the touchpad applets included in Ubuntu.
No use to say I'm happy tonight !

---

