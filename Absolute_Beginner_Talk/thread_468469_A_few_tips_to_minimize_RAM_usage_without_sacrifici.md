---
title: "A few tips to minimize RAM usage without sacrificing anything!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-08
Tip #1
nautilus sucks up ram over time, and alot of it!  my quick fix (and a few other features):
-go into Applications > Add/Remove
-get something called gTweakUI - xxxxx (there are a few of them)
-you only really need the "nautilus" one, but it forces them all on you
-open gTweakUI - nautilus (System > Preferences > gTweakUI - nautilus)
-after a few hours of your computer being on, you may find yuor ram filling up, so do this!  unckeck "use nautilus to draw desktop" and then check it back on!  That should have shaved off about 200Mb of waste (assuing it was there to begin with!)
By the Way, you might find there are some other usefull features in this app!

Tip #2
firefox sucks up ram over time, but not nearly as bad.  My quick fix...
-close it and re-open it every now and then (of course, this may only be a problem if it is left open for hours at a time!)

Tip #3
don't use windows!  It consumes way more ram by default after a fresh install and just gets worse over time!  also, with every program you open, and then close, some of it's dynamic link libraries are left in ram for a quick start next time!  ubuntu does a similar thing, but not nearly as bad!

Well, there's my list!  If any one has any comments or something to add on, feel free!  I hope all you people with less than about 512Mb of ram are feeling faster already! :p

---

### Post by finer recliner on 2007-06-09
ahhh a nautilus memory leak fix! horray! i cant wait to try it.

---

### Post by ryanVickers on 2007-06-09
Yeah, I like it!  It doesn't really fix the leak, just collects the drips in a bucket then throws them out the window :p

But it works!  And there's lots of other cool features in it!  Use your home as desktop, put computer, home, or even trash icons on the desktop...

---

### Post by ryanVickers on 2007-06-13
oops, just an update on the poll, I meant to not say anything after the "4Gb+" of ram, I wa temporarily confused with 32 bit :p

---

### Post by NT4usB on 2007-06-20
> **ryanVickers said:**
> Tip #1
nautilus sucks up ram over time, and alot of it!  my quick fix (and a few other features):
-go into Applications > Add/Remove
-get something called gTweakUI - xxxxx (there are a few of them)
-you only really need the "nautilus" one, but it forces them all on you
-open gTweakUI - nautilus (System > Preferences > gTweakUI - nautilus)
-after a few hours of your computer being on, you may find yuor ram filling up, so do this!  unckeck "use nautilus to draw desktop" and then check it back on!  ...

Can't we just leave it unchecked? I don't (hardly ever) use nautilus anyway...

---

### Post by ryanVickers on 2007-06-20
> Can't we just leave it unchecked? I don't (hardly ever) use nautilus anyway...
Yes, this is perfectly fine, and also the actuall intent of the feature :p, but with it unchecked, you will have no desktop icons. Everything else will be normal, you can still store things in the /home/username/Desktop folder, they will just not be displayed on the desktop.

---

### Post by asleepfromtheday on 2007-08-06
Running E16 and thunar instead of nautilus is what i do, also i use balsa instead of thunderbird or evolution, i use sysv-rc-conf  to edit my boot services, i run no samba or any other uneeded servers, i explicitly mount and unmount my nfs shares and lastly i dont use background images :KS

---

### Post by ryanVickers on 2007-08-08
That's good - I want more people to post ideas here, but at the same time, don't you think your sacrificing just a little bit by doing all that!? :)

---

### Post by FuturePilot on 2007-08-08
I don't seem to have a memory issue with Nautilus. Been running for 4 hours Nautilus is only at 11MB.

---

### Post by wolfen69 on 2007-08-08
my computer will die of old age before i have to worry about RAM usage in linux.(i have 2 gigs.)

---

### Post by ryanVickers on 2007-08-08
> **wolfen69 said:**
> my computer will die of old age before i have to worry about RAM usage in linux.(i have 2 gigs.)

Very good! ;)  Unless you have Vista, which I recently took a quick look at - with nothing open it uses about 710Mb of ram!!!  And the effects are almost completely unnoticeable, and **sooo** not worth the performance decrease!  Where as in ubuntu, they're great, and you can turn them off for GPU consuming stuff!

---

### Post by ryanVickers on 2007-08-08
> **FuturePilot said:**
> I don't seem to have a memory issue with Nautilus. Been running for 4 hours Nautilus is only at 11MB.


Some times it's not a problem, but if you've been moving lots of files and had lots of windows open and stuff, it sometimes forgets to clear stuff out or something.  I don't know, just thought I'd put this up here so if it does happen, people know what to do!

[CENTER][FONT=Courier New][B][COLOR=Red]::ADDITION::
[/COLOR][/B][/FONT][LEFT][FONT=Courier New][COLOR=Black]Try running your virtual machines in an Xfce (xubuntu) session instead of KDE or GNOME!  To add it on as a session option, just type:
```

sudo apt-get install xubuntu-desktop

```

You may not notice anything different at first, but once your VM is booted up, you ram usage should not be very much more then running the VMOS natively!
[/COLOR][/FONT][/LEFT]
 [/CENTER]

---

### Post by RomeReactor on 2007-08-08
Yes, the Nautilus team still needs to address how to stop memory usage from ballooning up; if you're used to copying large files or a lot of files, deleting others, etc., it really blows up. I usually just kill Nautilus from the System Monitor, and that solves it for me.

---

### Post by ryanVickers on 2007-08-08
I don't seem to be able to find it here, but I received a email notification that someone had posted this:
> 
If you stop Nautilus from drawing the desktop won't all your icons disappear?
The answer is "yes" and I explained that earlier, but the person asking didn't seem to mind them being gone; they "never used it anyways".

---

### Post by Inxsible on 2007-08-08
i havent seen nautilus taking more than 11 mb, but most times i kill nautilus after i am done with what I wanted to do. That would seem to be easier than doing all the gTweaking ;)

and you can always use other file managers like thunar or konqueror or dolphin etc.

---

