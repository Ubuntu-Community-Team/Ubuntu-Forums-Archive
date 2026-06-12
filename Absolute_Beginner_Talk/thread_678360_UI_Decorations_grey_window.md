---
title: "UI Decorations grey window"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by simocusi on 2008-01-25
Installing ProEngineer in my laptop using ./setup a grey window titled UI Decorations appears and nothing else happens. Any clue on how to fix this?

Thanks

---

### Post by nowshining on 2008-01-26
try sudo

sudo ./setup

insert ur pw - don't worry it won't show up as u type it out - :) that's normal, just type it out as normally and press enter.

---

### Post by simocusi on 2008-01-26
I get the same problem. Sudo doesn't make any difference. The grey window still appears.

I dont know what you mean with:

insert ur pw - don't worry it won't show up as u type it out -  that's normal, just type it out as normally and press enter.

Thanks for your time!

---

### Post by nowshining on 2008-01-26
when u issue a sudo command ur asked to enter ur password :) to continue of course.

so u see no text at all?

---

### Post by simocusi on 2008-01-27
No, Just the gray window. It happened to me before with Matlab (not when installing but when running the program). It was a Java issue, do you think it can be the same now with this installation window?

---

### Post by nowshining on 2008-01-27
can u do a screenie :)

poing mouse cursor over the grey windows

press alt + print on the computer & save the screenshot - then when replying - full advanced mode - go advanced on ubuntuforums.org & from there attach it.

---

### Post by simocusi on 2008-01-28
here it is

---

### Post by nowshining on 2008-01-29
where did u download this ./setup file can u link me?

---

### Post by jordanmthomas on 2008-01-29
1.  Try disabling compiz.  If it works after that, you can 
2.  Try running this before your setup program:
```
export AWT_TOOLKIT=MToolkit 
```

Hopefully one of these two things will help you out.

---

### Post by jordanmthomas on 2008-01-29
> **nowshining said:**
> where did u download this ./setup file can u link me?

It looks like it's on a CD...and if it's for engineering it's likely not free.

---

### Post by simocusi on 2008-01-29
It's not a free cd.

The export AWT_TOOLKIT=MToolkit command does not work..

How do I disable compiz?

Thanks!

---

### Post by jordanmthomas on 2008-01-29
System -- preferences -- desktop effects (i think, I don't use Ubuntu)
If exporting AWT_TOOLKIT didn't work, it's possible that compiz wasn't the problem anyway or (more likely) that it's not a java program.

---

### Post by simocusi on 2008-01-29
Yes, it's a bought cd

the "export AWT_TOOLKIT=MToolkit" command doesn't make any difference.

how do I disable compiz?

---

### Post by simocusi on 2008-01-30
I don't see any desktop effects on preferences..
 Have any other idea?

thanks so much

---

### Post by jordanmthomas on 2008-01-30
I think it might be system --> preferences --> Appearance --> Desktop Effects maybe?

Just look around, it shouldn't be THAT hard to find.

---

### Post by simocusi on 2008-01-31
Thanks!

Disbling Compiz at System-Preferences-Appearance worked out!

Just one thing: how do I find the command to execute it?

---

