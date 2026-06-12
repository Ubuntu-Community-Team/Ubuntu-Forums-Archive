---
title: "Feisty w/w Beryl window issue"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by BuntuConversion on 2007-04-23
I just installed the latest Ubuntu using the WUBI, and then installed Beryl.  First off, NO PROBLEMS!  It was so smooth, and so easy.  I LOVE IT!  

Only issue I've encountered so far is that anytime a new window or dialogue box opens, I have to alt-tab to it or click on it--it isn't in focus right away.  Any idea how I can fix that?  If I hit ctrl-y in Firefox, I have to click on the Downloads window myself, instead of it coming up; if I start Terminal, I have to click it or alt-tab; when I bookmark a page, alt-tab, etc...

Any hint would be appreciated.  I've tried finding the fix in Beryl, but no luck.  This is so awesome.

Another hint I could use is making the visibility or clarity of the screen better--it's fuzzy when I look at it, so I have to refocus my eyes every now and again.  I have a Samsung SyncMaster 152a LCD monitor.

I Love Ubuntu!

:guitar:

---

### Post by Happy_Man on 2007-04-23
Well, somewhere in the beryl settings manager, there will be an option named "focus stealing prevention", set that to low or none. As for your monitor, are you talking about the fonts, or the screen itself?

---

### Post by BuntuConversion on 2007-04-23
> **Happy_Man said:**
> Well, somewhere in the beryl settings manager, there will be an option named "focus stealing prevention", set that to low or none. As for your monitor, are you talking about the fonts, or the screen itself?

Well, perhaps both.  The fonts are a bit blurry (legible, I'm just used to ClearType on MS).

As for the other fix, THANK YOU!

Hot dog I love Linux--just added it to my fiancee's and am gonna make a MythTV box out of my old machine.

You guys are great!
jb

---

### Post by Happy_Man on 2007-04-24
Install the package "msttcorefonts" through Synaptic or just put this into a terminal:

```
sudo apt-get install msttcorefonts
```

---

