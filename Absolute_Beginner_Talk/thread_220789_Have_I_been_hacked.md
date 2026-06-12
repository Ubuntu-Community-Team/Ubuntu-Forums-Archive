---
title: "Have I been hacked?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by lucid on 2006-07-22
Hi,

I've found that when I move the Firefox launcher to the gdesklets launch bar the homepage is replaced with that of the University of Alberta, a web page I have not assigned and never visited. I am unable to change this. However, when I use the launcher from the applications menu Firefox launches with the correct web page. 

As this first happened a day after I installed Dapper I decided to be better safe than sorry and did a clean install again, wiping the drive and starting completely anew. But after setting up gdesklets I've had the same thing occur. What could be causing this? Can I get some advice on what the problem may be? Cheers.

---

### Post by hw-tph on 2006-07-22
I have seen this happen when bad parameters is passed to Firefox on startup, either a bad option or a malformed URL, I cannot really recall which. Check the launcher properties and see what arguments it passes to the firefox startup script.


Håkan

---

### Post by steve.horsley on 2006-07-22
hw-tph is right. Look at the launcher command. I seem to remember there is an errant %s on something similar that you need to remove.

You are not hacked. It's a mighty confusing thing to see happen though.

---

### Post by woedend on 2006-07-22
lol, it used to go to the uni of arizona...i guess alberta is the lucky one now.

---

### Post by hw-tph on 2006-07-22
> **woedend said:**
> lol, it used to go to the uni of arizona...i guess alberta is the lucky one now.

If the web admin is looking for hits then I guess Firefox made his day. :)

---

### Post by lucid on 2006-07-22
The starter command was firefox %u. I've removed the %u and it works fine (sorry to alberta, less hits for you!). Thanks for all the help, much appreciated.

---

### Post by Anduu on 2006-07-22
> **lucid said:**
> The starter command was firefox %u. I've removed the %u and it works fine (sorry to alberta, less hits for you!). Thanks for all the help, much appreciated.

But...but...

---

### Post by Skia_42 on 2006-07-22
> **Anduu said:**
> But...but...

Haha, you ever been to that University perhaps?:p

---

### Post by jarviser on 2006-11-17
LOL??? I don't see the funny side somehow. This has happened to me, but only in the last week (Nov 2006), and it was driving me nuts til I did a search on here. How on earth did I get %U in my Firefox launcher - was it always there? If so why cannot this be fixed with an update - we've had hundreds of them since launch!

---

### Post by jhenager on 2006-11-17
I am curious what the %u switch does. Maybe it stands for 'university' and it goes to the first one in the alphabet?

---

### Post by Spookster on 2006-11-17
Firefox automatically takes you to the first google result for a term you enter (whether on the command line or in the address bar). It appears that google.com expands 'u' to 'university' as this is a fairly common abbreviation (the % is ignored) - and alberta just happens to be the #1 result for 'university'.

---

### Post by jarviser on 2006-11-17
Well after all that, I'm still going there even with the %U taken out. My launcher command just says "Firefox" and I have rebooted since making the change - yet I have a tab on my workspace for Alberta Uni!!  HELP!!
EDIT - sorry I had Firefox %U as a startup program in my session settings!

---

