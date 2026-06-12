---
title: "How do I add new Python-Fu scripts to the Gimp?"
date: 2007-04-29
forum: Art &amp; Design
---

### Post by King_Critter on 2007-04-29
Ok... So I'm a relatively new Gimp user, and I wanted to add a new plug-in (_[this one]("http://students.washington.edu/jkivligh/gimp_rounded_corners/")_, specifically) but didn't know where to put it/how to install it. Any help would be *greatly *appreciated.

---

### Post by ComplexNumber on 2007-04-29
place it in ~/.gimp-2.2/plug-ins

---

### Post by bakermiller on 2007-04-29
...So I would copy the text and save it as gen_corners.py and copy it into ~/.gimp-2.2/plug-ins???

Is there another place to put the plug-ins? Because i seem to already  have a few plug-ins installed, but none show up in ~/.gimp-2.2/plug-ins???

---

### Post by ComplexNumber on 2007-04-29
> **bakermiller said:**
> ...So I would copy the text and save it as gen_corners.py and copy it into ~/.gimp-2.2/plug-ins???

Is there another place to put the plug-ins? Because i seem to already  have a few plug-ins installed, but none show up in ~/.gimp-2.2/plug-ins???
yes. but thats not necessary because its already called gen_corners.py.

you can also put them in the following too:
** /usr/lib/gimp/2.0/plug-ins**
i tend to put all the stuff that i downloaded myself in ~/.gimp-2.2/plug-ins so that i don't have to reinstall them all between linux upgrades.

---

### Post by King_Critter on 2007-04-29
Hmm... Didn't work. <_<

I tried putting the script in both directory's you suggested, but no luck. Is there any other option?

---

### Post by ComplexNumber on 2007-04-29
> **King_Critter said:**
> Hmm... Didn't work. <_<

I tried putting the script in both directory's you suggested, but no luck. Is there any other option?
what do you mean by "it didn't work"? they are where python scripts are meant to go.

---

### Post by King_Critter on 2007-04-29
Well, what I mean is: I put the script in ~/.gimp-2.2/plug-ins. It's there. But in the Gimp, I right-click, go down to Python-Fu -- it's not there. 

In case it will better help you diagnose my problem, I'm running Ubuntu Edgy with the Gimp version 2.2.13.

---

### Post by bakermiller on 2007-04-30
> **ComplexNumber said:**
> what do you mean by "it didn't work"? they are where python scripts are meant to go.

hmmmm.
i put the file in  both directories too.
/usr/lib/gimp/2.0/plug-ins
/home/****/.gimp-2.2/plug-ins

i also tried:
/usr/lib/gimp/2.0/python
and
/home/****/.gimp-2.2/scripts
just for fun and science!!
 But it still does not show-up in the gimp's xtns script-fu ( or python-fu).

...maybe something wrong with the script??

---

### Post by bakermiller on 2007-04-30
It now works and is under script-fu >> decor >>round corners. (if that's actually the one we installed, maybe this one was there all along!!!)

try putting it under >>
/home/****/.gimp-2.2/script 
or
/usr/lib/gimp/2.0/python. 
I was not very consistent, i think i put it in both folders :P

---

### Post by King_Critter on 2007-04-30
Actually, that was there all along. :P

---

### Post by ComplexNumber on 2007-04-30
strictly speaking, the scm files go in the 'scripts' directory.

---

### Post by graphguru on 2007-07-03
I've tried:

/usr/lib/gimp/2.0/plug-ins/python_fu_edgy.py
/usr/lib/gimp/2.0/python/python_fu_edgy.py
/home/nick/.gimp-2.2/plug-ins/python_fu_edgy.py
/home/nick/.gimp-2.2/scripts/python_fu_edgy.py

I still can't find them in GIMP.

Using Ubuntu 7.04

Thanks

---

### Post by danellisuk on 2008-11-20
You need to make the plugin file executable.  I placed the python-fu plugin in the following folder:-

```
$ cd /home/daniel/.gimp-2.4/plug-ins
$ ls -l
-rw-r--r-- 1 daniel daniel 5381 2008-11-20 21:49 save-layer.py
$
```

Then use chmod to make the file executable:-

```
$ chmod +x save-layer.py
$ ls -l
-rwxr-xr-x 1 daniel daniel 5381 2008-11-20 21:49 save-layer.py
$
```

The script will then load when you restart Gimp.

---

