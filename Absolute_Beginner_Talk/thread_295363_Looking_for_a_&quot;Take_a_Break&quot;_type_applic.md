---
title: "Looking for a &quot;Take a Break&quot; type application"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Mr. Matt on 2006-11-07
I hope this is the correct place for my question.

When I used Windows, one of my favourite programs was "Take a Break" which would allow me to set a specified time to use the computer before it would remind me to take a break (which I could also set a time for).  Could anyone point out a similar program for Ubuntu?

I noticed in Gnome Ubuntu that there was something similar to this under the Keyboard settings however I would prefer something else because a) I installed KDE which I like much better and can't find the equivalent option and b) it was missing some features that I would like (such as restarting the timer).

Thanks for your help

Matt
4th day Ubuntu user!

---

### Post by John.Michael.Kane on 2006-11-07
These may be of use,and you should be able to find them through a search with your package manager.

1)rsibreak
2)Workrave
3)xwrits

---

### Post by Mr. Matt on 2006-11-08
Thanks!  Looks to be exactly what I'm looking for.

---

### Post by madmetal on 2006-11-08
i use workrave and its really good!

---

### Post by alexmoon on 2007-01-15
I heard about workrave on the "go open" show, and was curious about it. Went to the workrave site and downloaded the workrave_1.8.3_i386.deb package, which I then tried to open with "gnome-open". 

It then tells me:

"Error: Dependency is not satisfiable: 
libgnomemm-2.6-1c2"

I'm using Ubuntu 6.10.

No idea what to do next - I'm still very new to Ubuntu, and linux generally, and would appreciate any suggestions.

Thank you!

---

### Post by ThrobbingBrain66 on 2007-01-15
> **alexmoon said:**
> I heard about workrave on the "go open" show, and was curious about it. Went to the workrave site and downloaded the workrave_1.8.3_i386.deb package, which I then tried to open with "gnome-open". 

It then tells me:

"Error: Dependency is not satisfiable: 
libgnomemm-2.6-1c2"

I'm using Ubuntu 6.10.

No idea what to do next - I'm still very new to Ubuntu, and linux generally, and would appreciate any suggestions.

Thank you!

There are about 10 dependencies for workrave, but the good news is that it's available in the repos.  Installing it from there will be much easier.
Fire up a terminal and type:
```
sudo aptitude install workrave
```

---

### Post by rockprincess on 2007-01-20
Help!

I can only start WorkRave through the terminal.....which is no problem at all, but I hate having the terminal window open all the time.....when I close the terminal window, WorkRave closes automatically as well..

Is there a work around for that?

Please help me!

---

### Post by wildkarde on 2007-01-20
Actually there is one included.

Go to the System, and go to the keyboard settings.  You will find it there....

EDIT::  hehe, but you already know that.. never mind.  yeah workrave

---

### Post by another_sam on 2008-02-14
After one day using Typing Monitor, I realized that I *need* this ****. It's definitely nerdgonomic.

---

