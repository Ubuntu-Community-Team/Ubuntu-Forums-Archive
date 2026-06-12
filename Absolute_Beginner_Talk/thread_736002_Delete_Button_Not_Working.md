---
title: "Delete Button Not Working"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-03-26
Hi Community,

My Delete button is not working in Hardy 8.04.  It was working in Gutsy 7.10, but I decided to run the Beta version.

Any idea's as to why this is happening??

I'm running an Acer Extensa 5220 if that helps.  I'm hoping it's only a bug in Hardy and it'll be fixed soon, but I thought I'd ask someone here since they might have a quick fix.

---

### Post by pedro_orange on 2008-03-26
I'm not up to date on the HH development so it may be something they may/may not be aware of. 

But have you tried looking at your key bindings? 
Try and bind an arbitary thing to the delete key itself and see if that works?

---

### Post by kolisikepu on 2008-03-26
> **pedro_orange said:**
> I'm not up to date on the HH development so it may be something they may/may not be aware of. 

But have you tried looking at your key bindings? 
Try and bind an arbitary thing to the delete key itself and see if that works?

Key bindings??  Where can that be found?

Thanking you in advance.

---

### Post by pedro_orange on 2008-03-26
I'm currently at work - so I can't remember offhand. 

But I presume it's in Preferences somewhere. 

Other things to have a look at: Your keyboard layout. Is this correct? It should allow you to test it on the GUI configurator.

---

### Post by kolisikepu on 2008-07-04
After many days of searching and applying different things and making changes, this problem still exists with my PC.  Gutsy keyboard works perfect.  Hardy, my delete is still not working.

I have given up the battle with this and now would like to log this case with the Hardy team as a major issue.

---

### Post by muslim_abu_tasneem on 2008-07-14
I have the same problem on my Acer Extensa 5210, my delete button doesn't work. Please can someone help us, I am lost without a delete button.

---

### Post by bobnutfield on 2008-07-14
Open a terminal and type:

> xev

This will start a program that identifies what happens when keys are pressed.  Press the Delete key and post the results back.  It may not be mapped correctly.  If that is the case, I will have to go back into some of my notes and recall how to map it correctly.

Bob

---

### Post by bobnutfield on 2008-07-14
Sorry, misread the post....my response was for mapping the "delete" key, not a button.  

Bob

---

