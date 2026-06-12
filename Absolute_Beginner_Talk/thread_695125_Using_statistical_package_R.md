---
title: "Using statistical package R"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by kmir on 2008-02-12
I would like to use the statistical package R in ubuntu.
Through posts in other forums
( [http://ubuntuforums.org/archive/index.php/t-565526.html](http://ubuntuforums.org/archive/index.php/t-565526.html) ), 
I have managed to install it (I believe).
When I type

sudo apt-get install r-base

it tells me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
r-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

(same for r-recommended).
Now. Where is it? This might sound silly, but I can't get it started. And if I want a graphical user interface, do I need something extra like wxMaxima for Maxima?

Thanks for any help,

kmir

---

### Post by rufius on 2008-02-12
There isn't really a good GUI for R on linux. The way to use R though is from command line type as follows:

```

user@localhost:~$ R

```

As you can see, its simply the capital letter R, not lowercase, it must be capital.

I think there might be a Tcl/Tk interface to R for linux but I recall it not being anything special. I use R at work but I use it on Mac OS X which has a good R GUI. 

On my linux laptop, I just use the command line. Never really had any problems like that. It can still do all the graph/plots etc.

Hope that helps :)

---

### Post by kmir on 2008-02-12
Thank you!

Oh man - *capital* R... haha.

Too bad there is not a good GUI. Actually, in the search option for the forum, you cannot search for a single letter (e.g. "R"), right?

---

