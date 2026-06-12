---
title: "[SOLVED] Ubuntu 7.10 Freezes"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by aaguilar4 on 2008-02-12
I have a very weird problem with Ubuntu.  I have read some of the other problems, and the freeze is usually at logon or absolutely random.  My problem is different: Ubuntu will freeze when I try to drag something into an area where you can't drag.  In Windows, you would see the mouse turn into like a DONT black sign, but in Ubuntu it just remains the same.  After the freeze, the keyboard won't answer, and everything in the screen will remain still (like a picture) except for the mouse, which can move around but not click anywhere.  After this happens, the only thing I can do is to power off my computer with the power button because *nothing* else responds.  
An example of when this happens would be like if I tried to select this text and then drag it into another part of the website (not another form, but just like the edge of the screen or something like that).  This has been happening for a while, to the point where I'm used to NOT highlighting things with the mouse, I use the Shift key instead.   

I would greatly appreciate any help with this

---

### Post by jan quark on 2008-02-13
does this happen only in your webrowser? what is your webrowser?

or does this also happen in other text files like open office files?

or does this problem occur everywhere?

if you think this is a bug you can report it by creating an account at 

[launchpad]("https://launchpad.net/ubuntu")

---

### Post by aaguilar4 on 2008-02-13
Ohh it happens everywhere... 
My browser is firefox.  But, as an example, If I try to drag a shortcut or folder from the desktop to the top panel where the watch is (or anyplace where it's not allowed to be dropped for that matter), the whole thing will freeze on me without any chance of getting it back.  I just installed Ubuntu a couple months ago, but I can't recall if it was like that since the very beginning.  I just know it has been happening for a long time. 
By the way, this is my first post, so I don't know how to use launchpad or what it's for.

---

### Post by jan quark on 2008-02-13
launchpad is a service for reporting bugs

you can create a free account
and post your problems there
but only if you think your issue is unique and you cannot find a solution

if you post your problem in launchpad, it will be checked, by the ubuntu developers and perhaps confirmed and a solution will be searched

so coming back to your hang ups

can you please post the output of the following terminal commands

```
lspci
```
```

sudo lshw
```

it just to have a closer  look at your specs

---

### Post by PmDematagoda on 2008-02-13
Did you do the Memory Test by selecting the option from the GRUB menu?

If you haven't then do that and post if you get any errors.

---

### Post by aaguilar4 on 2008-02-13
> **jan quark said:**
> does this happen only in your webrowser? what is your webrowser?

or does this also happen in other text files like open office files?

or does this problem occur everywhere? 

Actually I was under the impression that it happened everywhere... but I just tested it right now with other text, and it did work (text boxes, office text); everything works except for Firefox.  My guess it's that the version of Firefox (2.0.0.12) has some kind of problem with dragging and GNOME just freaks out when this happens.  
I think I can just wait for an update on Firefox.  I tried it with IE (which I have running through wine) and it just didn't let me drag outside the window, but it didn't freeze up my system.  

Anyway, thank you for your help

---

### Post by jan quark on 2008-02-13
you are welcome

you can also try another web browser like 
opera or 
kazehakase, which I use, it's fast and stable

---

