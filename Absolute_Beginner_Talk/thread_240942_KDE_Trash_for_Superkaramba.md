---
title: "KDE Trash for Superkaramba"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by papuaoshi on 2006-08-21
I have superKaramba 0.4 compiled from sources. When I downloaded KDE Trash 2 plugin - only white blinking rectangle appears in the left bottom corner. What's wrong? ](*,) 

PS: Other plugins such as Aero AIO, Crystal Clock work fine. And I, of course, tried superKaramba 0.39 from repositories. And Trash 1.0.

---

### Post by TFX360 on 2006-08-21
Dear papuaoshi,


Could you try with an apt-get or aptitude command and add the command --fix-missing

Like so:

```
aptitude install applicationname --fix-missing
```


Kind regards,


TFX

---

### Post by papuaoshi on 2006-08-21
> **TFX360 said:**
> Dear papuaoshi,


Could you try with an apt-get or aptitude command and add the command --fix-missing

Like so:

```
aptitude install applicationname --fix-missing
```


Kind regards,


TFX

Apt-get: The newest version of superkaramba has already been installed.

I suspect there's no problem in superKaramba.

---

### Post by TFX360 on 2006-08-21
> **papuaoshi said:**
> Apt-get: The newest version of superkaramba has already been installed.

I suspect there's no problem in superKaramba.
Did you try aptitude? Aptitude handels dependancies better than apt-get. Remove the application and reinstall with aptitude. See if that helps! Backup where nessecary (how do you spell that?:))


Kind regards,


TFX

---

### Post by papuaoshi on 2006-08-21
It's magic! It works!

It seems aptitude is better then apt-get and adept.

Is there some gui for aptitude or I should use synaptic?


PS: necessary ;)

---

### Post by papuaoshi on 2006-08-21
Anyway... BIG tankx for help!
:) :) :)

---

### Post by TFX360 on 2006-08-21
> **papuaoshi said:**
> It's magic! It works!

It seems aptitude is better then apt-get and adept.

Is there some gui for aptitude or I should use synaptic?


PS: necessary ;)

Thanks! Uhm, just use aptitude, it works.


> **papuaoshi said:**
> Anyway... BIG tankx for help!
:) :) :)

Your quite welcome. What is Trash for SuperKaramba anyways. I use gnome.


Kind regards,


TFX

---

### Post by TFX360 on 2006-08-21
Actually,


I don't use Synaptic at all unless really _necessary_ :D. Install apt-file so you can look for missing files when compiling. 

```
sudo aptitude install apt-file
```

And I think you can standard use:

```
sudo apt-cache search searchpackagehere
```


Could help in the future!


Kind regards,


TFX

---

