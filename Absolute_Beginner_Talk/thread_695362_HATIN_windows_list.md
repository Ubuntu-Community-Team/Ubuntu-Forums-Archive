---
title: "HATIN windows list"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Shrek X on 2008-02-12
So, I got everything happy, including myself with Ubuntu 7.10 (including a hotmail client, yeaaaa)... took some lifting because of my setup.  

but


I HATE the windows list, what can I do to change it.  

I operate with the task bar in a horizontal position on the left side, it is fine at 6 open items, but on the 7th it tries to stack in two columns and becomes useless with mouse clicks, seems like it tries to repaint to a single column and switches back ... again and again and again.  

Any help would be greatly appreciated, and please if you have a solution be fairly specific, as I am new to the environment.  

Thanks in advance.

---

### Post by spiderbatdad on 2008-02-13
It does have minimal preferences if you right click the marker. You could remove it entirely from the panel. Beyond that...changing the widget is a fairly difficult process involving gtkrc-2.0...and that has limitations too, unless your a software guru.

---

### Post by jordanmthomas on 2008-02-13
I see what you're saying, and that's certainly annoying at best (perhaps even bug-report-worthy?)
Unfortunately I don't think there's any solution so long as you're just using the gnome-panel and standard applets.

It takes two clicks to use instead of one, but you could add a window selector to your panel instead of the window list (right click panel and go to add item)

Sorry I don't really have a "real" solution for you.

---

### Post by oedha on 2008-02-13
mmm.....what if you add more panels.....
or...try to work in different workspace........
that's what i did.......:)

---

### Post by Shrek X on 2008-02-13
Reproducing the same panel, just reproduces the problem in several different places :lolflag:





Are there other applets that do the same thing?  (non standard?)  how do I get to them?

---

### Post by jordanmthomas on 2008-02-13
You could try to see if perhaps gimmie would work for you (I think it has a taskbar feature):
```
sudo apt-get install gimmie
``` (or look for it in synaptic package manager)

Also, it takes a little bit of setting up, but you could use pypanel as just a taskbar.  It's not an applet, and is a full panel in its own right though, I'm not sure how it would mess with the way you have things set up, you seem like you'd be interested in keeping to them.  :)

---

### Post by Shrek X on 2008-02-13
> **jordanmthomas said:**
> You could try to see if perhaps gimmie would work for you (I think it has a taskbar feature):
```
sudo apt-get install gimmie
``` (or look for it in synaptic package manager)

Also, it takes a little bit of setting up, but you could use pypanel as just a taskbar.  It's not an applet, and is a full panel in its own right though, I'm not sure how it would mess with the way you have things set up, you seem like you'd be interested in keeping to them.  :)

Looks like a cool app, but doesnt have the open applications.  

Thanks for the tip though!  :)

---

### Post by jordanmthomas on 2008-02-13
I think if you add an application to its application section if it's already running, it will switch to its window.  Probably not an ideal solution either.  :|

Maybe you can make pypanel work for you then?  Like make your gnome-panel go 1/3 of the way down, then use pypanel for a taskbar on the side?

---

### Post by Shrek X on 2008-02-13
well, that sucks :(

---

### Post by rfurman24 on 2008-02-13
Are you saying your window list will not adjust size as more windows are opened? Mine works fine. I believe there is a setting somewhere do change it. I will have to play around to find it.

---

### Post by Shrek X on 2008-02-13
> **rfurman24 said:**
> Are you saying your window list will not adjust size as more windows are opened? Mine works fine. I believe there is a setting somewhere do change it. I will have to play around to find it.

that would be a great summation, yes.

---

### Post by Shrek X on 2008-02-13
bump, just in case there is someone around now who may have an idea.  :)


Thanks again for all the suggestions.

---

### Post by emarkd on 2008-02-13
No answer to your problem, but I gave up on the Gnome Panel and installed Avant Window Navigator.  It requires a compositing agent, like Compiz, to work, but it uses icons instead of titled buttons, so you can fit lots more apps into the same space.

if you haven't seen it, check it out here:  [http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page) 

Good installation instructions there too, btw

---

### Post by Shrek X on 2008-02-13
> **emarkd said:**
> No answer to your problem, but I gave up on the Gnome Panel and installed Avant Window Navigator.  It requires a compositing agent, like Compiz, to work, but it uses icons instead of titled buttons, so you can fit lots more apps into the same space.

if you haven't seen it, check it out here:  [http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page) 

Good installation instructions there too, btw


That may have worked, but this little laptop is a brick, and doesn't meet the system requirements.  

Thanks for the suggestion though!

---

### Post by macogw on 2008-02-14
> **jordanmthomas said:**
> 
It takes two clicks to use instead of one, but you could add a window selector to your panel instead of the window list (right click panel and go to add item)

Sorry I don't really have a "real" solution for you.

OP, did you try this?

---

### Post by northern lights on 2008-02-14
One click - two clicks - why not no click?

I assume u're running Gutsy?! In that case it ships with compiz-fusion. Turn on scale, set the trigger to ur liking (mine's top right screen edge) and u can flip between windows without a single click (and/or keyboard shortcuts). Even if ur laptop's one old piece of junk, u certainly can use c-f - simply turn off all the flashy crap.

Few of my classmates, especially social science ppl, installed linux only for the flashy fx. Not the ideal reason for the switch, but hey - if a bit of eye candy can get for instance a history major to use linux, then it at least served a purpose, right?!

While that's not neccessarily what I got Ubuntu for, I was running Beryl since Edgy, for the sole purpose of having scale. Once u get used to switching ur windows this way, I personally can't come up with reason for the neccessity of any sort of panel. For the first week u'll keep minimizing windows and then questioning where they went - bring em back either with the above mentioned window selector or Alt+Tab/Super+Tab.

---

### Post by Shrek X on 2008-02-15
> **macogw said:**
> OP, did you try this?

yes, that would work, but it doesn't preserve the workspace I like and prefer.  Seeing what is open and being able to grab it, makes me happy... lol

---

### Post by Shrek X on 2008-02-29
So, I found a reasonable workaround for now, which is to move the tabs to the left column via FF plugin, not perfect but it works and I suppose it saves memory by not rendering more frames.  

But, I figure this is a bug, should I submit a but report, and how do I do that?

---

