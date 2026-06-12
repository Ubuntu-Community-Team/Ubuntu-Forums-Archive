---
title: "gyach"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by shadowtroopers on 2007-10-27
hi.
 i just started using ubuntu. Can anyone help me on how to install gyach?. I prefer step by step guide. Thanks

---

### Post by por100pre1 on 2007-10-27
**If using Gutsy** get this first and install it right clicking it:

[http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1](http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1)

Download Gyachi and install it right clicking it:

[http://prdownloads.sourceforge.net/gyachi/gyachi_1.0.5-1_edgy_i386.deb?download](http://prdownloads.sourceforge.net/gyachi/gyachi_1.0.5-1_edgy_i386.deb?download)

That's the way I installed it. Hope it works fine. :)

**EDIT: [Here's]("http://ubuntuforums.org/showpost.php?p=3601344&postcount=3") is another method.**

---

### Post by shadowtroopers on 2007-10-27
ok..it's done..as it said, the package installed. Ermm..but when i search at the application menu, it doesn't there..ive searched everywhere, then repeatedly reinstall the programme, but still getting the same thing "it doesn't there". Am i missed something out here? :confused:

---

### Post by por100pre1 on 2007-10-27
Right click Aplications and click edit menus or use this command:

```
alacarte
```

and create a new launcher. The command should be:

```
gyachi
```


**1[COLOR="RoyalBlue"]777[/COLOR]**

---

### Post by shadowtroopers on 2007-10-27
ok..it's done..thanks bro..i do really appreciated your help. :)

---

### Post by por100pre1 on 2007-10-27
Glad to help. Please mark the thread as [SOLVED] so it can benefit others. :)

---

### Post by shadowtroopers on 2007-10-28
it's installed and run properly, but whenever i want to go to room, it just stop there. There's not even a captcha window comes out.

---

### Post by por100pre1 on 2007-10-28
I just realized that Yahoo Chat is now using a CAPTCHA window. Unfortunately, that is not addressed in the installed package, I don't have any idea if there's a version that fixes the issue, sorry. :(

---

### Post by shadowtroopers on 2007-10-28
i see, i thought i missed something again. Gosh..luckily wine solved my problem. Is just that i want to use pure linux programme.

---

### Post by loell on 2007-10-28
1.0.5 is a very old package, there will be a new one in a day or two

this is a recent cvs gutsy package [http://www.mediafire.com/?avyn4kzjxmy]("http://www.mediafire.com/?avyn4kzjxmy")

it resolves the captcha better than pidgin imho ;)

---

