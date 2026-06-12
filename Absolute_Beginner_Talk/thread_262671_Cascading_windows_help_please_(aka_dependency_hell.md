---
title: "Cascading windows help please (aka dependency hell)"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-09-22
I fairly new to all this – couple of months. I tend to get lots of windows open at the same time. When I did this in Windows from time to time i would click and chose either “Tile Windows” or “Cascade Windows” in order to keep myself organized.

As far as I can tell – cascade windows won't work on the default Ubuntu desktop out of the box.

I tried compiz and it didn't work with my Radeon 9200SE. I found the program expocity here:
[http://www.pycage.de/software_expocity.html](http://www.pycage.de/software_expocity.html)

It needs gtk+-2.12.0
gtk needs:
Glib

glib needs
cario
pango
gnu make

pango needs cario, and cario needs
freetype2

and I could go on because i am stuck in dependency hell here. Every time i try to ./configure something that something needs so I can compile what i want it kicks out an error saying I have yet another unmet dependency. 

I've been doing this for 5 hours now. :-)

Is there a little simpler way to cascade my open windows?

Thanks!

---

### Post by Metacarpal on 2006-09-22
Don't know about cascading windows, but I imagine if you were to install build-essential, that would solve a lot of your compiling woes.  Here's what to do:
Open a terminal (Applications menu > Accessories > Terminal) and type:
```
sudo aptitude install build-essential
```
then give it your login password when prompted.

If you already know how to use Terminal, or if you already have build-essential installed, I'm sorry to waste your time - just don't want to make any assumptions. :)

---

### Post by podunk on 2006-09-22
I've already got build-essential, I went down that road several weeks ago!

Thank you though!

---

### Post by 3rdalbum on 2006-09-22
Thanks for the tip, podunk - when I'm next in Windows I'll try looking around for a "cascade windows" or "tile windows" option. (I'm a bit of a Windows newbie)

I don't think there's much of a need for this kind of thing in Linux, because of the virtual desktops or workspaces. You can send windows from one space to another, keep a window on all spaces, and switch your view through keyboard shortcuts or the little pager to the left of the trash can.

When compiling, don't forget to install the *-dev packages (e.g if the configure script needs libsdl, you'd install libsdl and libsdl-dev).

That program that you're trying to compile - it is like the Mac OS X Expose function? If so, you could always try "skippy", which is available from repositories. After it's installed, hit alt-F2 and type skippy, then whenever you want the expose press F11.

---

### Post by podunk on 2006-09-22
Thanks 3rdalbum!
I tried skippy, but it wants Open GL which doesn't play nice with my vid card (I wrote a very nice letter to ATI explaining that I was buying a nvida card because they were Linux friendly) but what i did find that is almost as good is a program called 
kompose

It is in Synaptic Package manager. You install it then in a terminal type
kompose

the hot key <ctrl> <shift> <j> brings it up.

You have to open a new tab in terminal to do any commands because kompose locks that one for it's self.

---

