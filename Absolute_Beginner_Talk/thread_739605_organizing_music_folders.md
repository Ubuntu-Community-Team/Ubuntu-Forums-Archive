---
title: "organizing music folders"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ericxhall on 2008-03-29
ok, so i know that there are threads that say this same thing.
but amarok wont organize my folders in my music.
i dont want to try to do it by terminal because i just dont have a handle on it yet.
but its totally bogus there isnt an app that can do it.
and while you are reading this...
why cant i enable visual effects?

---

### Post by ericxhall on 2008-03-29
bump.

---

### Post by jken146 on 2008-03-29
> **ericxhall said:**
> why cant i enable visual effects?

What have you tried?

---

### Post by ericxhall on 2008-03-29
well, i mean i installed compiz and then i thought i would be able to do it from the usual appearance menu, but it just wouldnt let me enable it

---

### Post by jken146 on 2008-03-29
> **ericxhall said:**
> well, i mean i installed compiz and then i thought i would be able to do it from the usual appearance menu, but it just wouldnt let me enable it

The usual steps are:

1. Enable the restricted driver for your graphics card, if applicable.

2. Install compizconfig-settings-manager

3. System -> Preferences -> Advanced Desktop Effects

---

### Post by saj0577 on 2008-03-29
Then run
compiz --replace

---

### Post by ericxhall on 2008-03-29
Ugh, this makes me look like such a friggin' idiot, but how do I enable it, if I don't know what it is, I haven't been using ubuntu long.

But one great thing that I have to say, is that all you guys on here are so helpful and don't look down on people who don't know their stuff.

---

### Post by ericxhall on 2008-03-29
> **ericxhall said:**
> Ugh, this makes me look like such a friggin' idiot, but how do I enable it, if I don't know what it is, I haven't been using ubuntu long.

But one great thing that I have to say, is that all you guys on here are so helpful and don't look down on people who don't know their stuff.

scratch that.

---

### Post by jken146 on 2008-03-29
Some more explanation:

> **jken146 said:**
> The usual steps are:

1. Enable the restricted driver for your graphics card, if applicable.
System -> Administration -> Restricted drivers manager

> 2. Install compizconfig-settings-manager
Search for that package in Synaptic (under System -> Administration) or type ```
 sudo aptitude install compizconfig-settings-manager
``` in a terminal.

> 3. System -> Preferences -> Advanced Desktop Effects

Then type ```
compiz --replace
``` in a terminal.

---

### Post by ericxhall on 2008-03-30
So I did that, then when i go into appearance preferences, and try to select one of the other radio buttons other than none, it says "The Composite extension is not available".

---

### Post by ericxhall on 2008-03-30
Bump!

---

### Post by prismpirate on 2008-03-30
Wonder why the topic changed to compiz, but to enable compiz, try opening the terminal
by going to


Applications > Accessories > Terminal


and paste:


```

SKIP_CHECKS=yes compiz

```



don't close the terminal window though

---

### Post by DMcA on 2008-03-30
> **ericxhall said:**
> So I did that, then when i go into appearance preferences, and try to select one of the other radio buttons other than none, it says "The Composite extension is not available".

What graphics card do you have? The same thing happens to me with my ATI mobility Radeon X700. To enable compiz I first have to enable the restricted fglrx driver. (System > Administration > restricted drivers manager) and then install xgl (which I think is as easy as sudo apt-get install xgl). I'm sure there's a tutorial around somewhere. 

As for organising your music directory, I'm sure this can be done with easytag or ex falso or various other tagging programs if, as I assume, you want to layout your directory using tags as folder names and file names.

---

### Post by ericxhall on 2008-03-30
So I am still stuck on organizing my folders.
I just want it to look like this
~/Music/Artist/Album
it cant be that hard.

---

### Post by DMcA on 2008-03-31
Did you even read my post? Organizing and tagging of a music collection can be done easily with a program such as easytag.

---

