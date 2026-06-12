---
title: "I could bash ./install to death"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by GuiGuy on 2006-11-03
Many linux installation get you to download a tar file, unpack it, log into the directory as su and then

$./install

OK, I do this. AFAIK I have all the right permissions. But the command never works. I get 

./install [enter]
bash: ./install: /bin/bash: bad interpreter: Permission denied

I don't get it. I get the same response whenever I try this with an installation. Is there an explanation?

Thanks

---

### Post by podunk on 2006-11-03
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

:)

---

### Post by cantormath on 2006-11-03
> **GuiGuy said:**
> Many linux installation get you to download a tar file, unpack it, log into the directory as su and then

$./install

OK, I do this. AFAIK I have all the right permissions. But the command never works. I get 

./install [enter]
bash: ./install: /bin/bash: bad interpreter: Permission denied

I don't get it. I get the same response whenever I try this with an installation. Is there an explanation?

Thanks

did you sudo ./install?

---

### Post by GuiGuy on 2006-11-03
> **cantormath said:**
> did you sudo ./install?

Yes- same thing.

Thanks

---

### Post by GuiGuy on 2006-11-03
> **podunk said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

:)

These are not packaged software items I want to install. These are compressed .tar files. AFAIK they cannot be installed from the package  manager. But if I'm wrong correct me. I love GUIs :D

---

### Post by GuiGuy on 2006-11-03
> **GuiGuy said:**
> These are not packaged software items I want to install. These are compressed .tar files. AFAIK they cannot be installed from the package  manager. But if I'm wrong correct me. I love GUIs :D

OK, I'm wrong again. I'll wade through the stuff at the bottom of the page and will report back.:D

---

### Post by podunk on 2006-11-03
> **GuiGuy said:**
> OK, I'm wrong again. I'll wade through the stuff at the bottom of the page and will report back.:D

One of the instruction sets on that page is "Enable extra repositories" once you follow that bit use the package manager 
System>Administration>Synaptic Package manager

and it's search function to look for your software before you start downloading stuff off the net. Just about everything I've ever wanted is there - or a different program that works better.

Point and click heaven. :-D

---

### Post by GuiGuy on 2006-11-06
> **podunk said:**
> One of the instruction sets on that page is "Enable extra repositories" once you follow that bit use the package manager 
System>Administration>Synaptic Package manager
:-D

OK, I read all that and played around with a few options. More time wasted as nothing was learnt other than I am probably too stupid to be using Linux.

The tar I want to install needs to be started from a shell script. ./install - this reports I don't have permission, even as root.

I give up, but sincere thanks for the help.

all the best

---

### Post by steve.horsley on 2006-11-06
You probably didn't make the install script executable. You can see if it is executable or not with the command 
**ls -l ./install**
If it is executable, there will be 'x's on the left. If not, use
**chmod +x ./install**
to set the executable flag on the file.

In Linux (and other unix like OSs), executable is a file flag in the filesystem much like the read-only flag. It's a property that is set against a file, and is independent of the file contents.

---

### Post by po0f on 2006-11-06
GuiGuy,

Try:
```
$ sudo bash ./install
```
and if that doesn't work, try:
```
$ sudo sh ./install
```

---

### Post by podunk on 2006-11-06
What exactly are you trying to compile and what's the web page it came from?

Heck, I borked one machine so far in the last 24, might as well go for 2. :-) I'll try to compile it tonight.

---

### Post by GuiGuy on 2006-11-06
> **steve.horsley said:**
> You probably didn't make the install script executable. You can see if it is executable or not with the command 
**ls -l ./install**
If it is executable, there will be 'x's on the left. If not, use
**chmod +x ./install**
to set the executable flag on the file.


Thanks, but my knowledge of Linux is sufficient that I understand that. It was one of the first things I checked.

Regards

---

### Post by GuiGuy on 2006-11-06
> **po0f said:**
> GuiGuy,

Try:
```
$ sudo bash ./install
```
and if that doesn't work, try:
```
$ sudo sh ./install
```

Thank you so much. That worked. Just tried a few other programs I wanted to install and each worked a treat. 


regards

---

### Post by GuiGuy on 2006-11-06
> **podunk said:**
> What exactly are you trying to compile and what's the web page it came from?


It's a general thing- I run into this problem everytime I want to setup a program that is not 'packaged'. However, as you can see in this thread, someone has given me the solution.

Thanks

---

