---
title: "I want Jackfield!"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-04
Has anyone mastered an installation of [jackfield?]("http://www.kryogenix.org/code/jackfield/")
If so, please enlighten me on how to get it working.

---

### Post by amohanty on 2006-11-04
Although I havent installed it, what kind of problems are you running into?

AM

---

### Post by shanepardue on 2006-11-04
If you've read the website I linked on my post, it's a little complicated to
 install. One guy said he got it working on Edgy, but then people say it
doesn't work on edgy. The mention of a bug on the website throws me off and 
after I follow the instructions as best I can, widgets don't show up. This
is how they're supposed to be ran, I'm guessing...

"LD_LIBRARY_PATH=/usr/lib/firefox python Jackfield/Widget.py /path/to/widget"

I get the error message...

"/Widget.py /home/shane/Desktop/
Traceback (most recent call last):
  File "Jackfield/Widget.py", line 256, in ?
    w = Widget(pth)
  File "Jackfield/Widget.py", line 64, in __init__
    raise "Not a complete widget"
Not a complete widget"

---

### Post by amohanty on 2006-11-04
I did look at it, and well he does say that edgy compatibility is still in the works. I will see if I can much with it over the weekend and if I can find something (thats not already mentioned in the blog) I will post back.

AM

---

### Post by shanepardue on 2006-11-04
I've also tried pointing to different directories and getting different error
 messages, but I think the problem is in the installation or compatibility.
Thanks for your help!

---

### Post by bijoux on 2006-11-06
i got this working on edgy. you have to edit a file in jackfield dir called Control.py just make sure WIDGET_DIRS in that file is pointing to the correct path

> **shanepardue said:**
> I've also tried pointing to different directories and getting different error
 messages, but I think the problem is in the installation or compatibility.
Thanks for your help!

---

### Post by shanepardue on 2006-11-06
Once I've gotten the file edited, how do I run a widget? That's where I got confused!

What's the command?

---

### Post by shanepardue on 2006-11-06
One step away. How do I run that widget?

---

### Post by shanepardue on 2006-11-08
Bijoux or anybody, please provide a simple howto to get this going.
I've tried the method on the website and for the life of me, I
can't get it working!

---

