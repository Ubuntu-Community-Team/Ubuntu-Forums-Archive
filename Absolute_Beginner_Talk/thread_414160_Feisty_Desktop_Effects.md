---
title: "Feisty Desktop Effects"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-04-19
I was blissfully surprised to find the desktop effects that come with my newly installed Feisty Faun! Only problem is that the 3D desktop has stopped working.....

It was running fine, I rebooted to check changes to grub and now it won't run. The true transparencies and wobbly windows work, but it was more the 3D desktop I was after....

---

### Post by Fillibuster on 2007-04-19
I wanted to be able to use the other various effects of Beryl so I attempted to install Beryl and it is buggy as hell.  It ran perfectly for me on Edgy, but for some reason, even following the Feisty instructions on the Beryl page, it still doesn't work right.  And now even when I ctrl+alt+backspace, and run just the default effects, my 3D cube doesn't work...

---

### Post by Stickymaddness on 2007-04-20
I've installed Beryl, and for the most part it works, it seems smoother than in Edgy, but has a few problems. 

The ruby icon doesn't appear in the tray so I can't change between metacity and beryl. Also when I run Beryl, all my windows loose their borders (Close, Minimize, Maximize) 

I wouldn't of thought Beryl would run better in Edgy than in Feisty :(

---

### Post by rich.bradshaw on 2007-04-20
are you running

beryl-manager

?

That will get you the ruby in the tray so you can set it up. Remeber to install emerald as well so you have the borders...

sudo aptitude install beryl emerald

should do it.

---

### Post by Stickymaddness on 2007-04-20
> **rich.bradshaw said:**
> are you running

beryl-manager

?

Whoops! :P For some reason when I installed Beryl I didn't get beryl-manager, I installed it now and I have the ruby in the tray, problem one fixed!

> **rich.bradshaw said:**
> 
Remeber to install emerald as well so you have the borders...

sudo aptitude install beryl emerald

should do it.


Yep, that's what I installed Beryl with orginally. I can open the emerald manager, but not change anything, also I've just noticed that terminal opens as a plain white block, regardless of what profile I use....

---

### Post by pitbulls20 on 2007-04-20
I am having the exact same problem as stickymaddness so hopefully this will be fixed



Larry

---

### Post by Stickymaddness on 2007-04-20
> **pitbulls20 said:**
> I am having the exact same problem as stickymaddness so hopefully this will be fixed



Larry

Hmm I thought this was a feisty specific problem... 

I'm also having a problem, where I log in and my desktop area is larger than my screen res, so I have to "move" around my desktop by moving my mouse to the edge of the screen. If I run gksudo nvidia-settings and change to a different res, and then back to the res it was on, the problem is fixed. A bit of a mission to have to do this every time I log in...

Prehaps you have experienced a similar problem?

---

