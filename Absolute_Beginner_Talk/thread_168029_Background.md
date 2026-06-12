---
title: "Background"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-04-29
Greetings,

Using Ubuntu (gnome) is there a way to have different backgrounds for each desktop or having the backgrounds change/rotate?

it seems not, but maybe someone does know a way

Using breezy,

--
sophtpaw

---

### Post by Estariel on 2006-04-29
Howdy!
Gnome itself cannot do that. I know however that there is a hack around that will quickly change the background whenever you change the virtual desktop. This will create the illusion that each desktop has a different background.

I don't know though where to get this (I don't use it). I'd start looking at gnome-look.org

---

### Post by htinn on 2006-04-29
There's lots of little hacks that do some of those things, but this is the most complete project I've yet seen:

[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

---

### Post by Rinzwind on 2006-04-29
htinn: cool program

Took about 1/2 minute to install and configure :)

Now I have 3 desktops with 25 wallpapers cycling. cool

---

### Post by cilynx on 2006-04-29
It is a cool little ute...

Unfortunately, it's a little slow for my taste.  I do a lot of quickly switching around.  I was hoping it would switch the background while the switcher was still up instead of a second or two after landing on the desktop.  I'd like the background to be a quick way of IDing which desktop I'm on.  (Generally, I run a 5x2 or a 4x3 grid of desktops.)

All of my elitism aside, thanks for the link to the great app.

---

### Post by Rinzwind on 2006-04-29
I see some flaws.
Sometimes the original background shows before it switches to the random background.

And now the deamon seems to have gone dead on me

Hmm :(

---

### Post by sophtpaw on 2006-04-29
[QUOTE=htinn]There's lots of little hacks that do some of those things, but this is the most complete project I've yet seen:

[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)[/QUOTE]


Thx, for that. I've downloaded and unpacked it.
HOw to run it though? ./configure don't work and the README file does't tell me how to install it or does it?

any help?

--
sophtpaw

---

### Post by cilynx on 2006-04-29
You can 
```

sudo -s
./install

```
in the newly created directory or you can just run it as-is-where-is
```

~/wallpapoz-0.3/src/wallpapoz.py

```
Be sure to restart the daemon from inside the GUI

---

### Post by halitech on 2006-04-29
the readme doesn't but the install flie does. basically just extract the files, open terminal and change to that directory then run

sudo python install.py install

it then shows up in the Apps - accessories menu

---

### Post by sophtpaw on 2006-04-30
[QUOTE=halitech]the readme doesn't but the install flie does. basically just extract the files, open terminal and change to that directory then run

sudo python install.py install

it then shows up in the Apps - accessories menu[/QUOTE]

[COLOR="DarkOrange"]Thank you Halitech, that is what i needed to know. It didn't occur to me that the instructions would be in INSTALL(is it not usually in README?) Anyway, i'm glad to learn something everyday. It is nice to wake up to a solution on the forum waiting for me. Long Live Ubuntu Forums![/COLOR]

---

### Post by halitech on 2006-05-01
normally I've seen most things have a readme and then install was some kind of install script but in this case, the writer decided to put the install instuctions in the install file. Glad I could help as I learned something as well :)

---

### Post by sophtpaw on 2006-05-01
[QUOTE=halitech]normally I've seen most things have a readme and then install was some kind of install script but in this case, the writer decided to put the install instuctions in the install file. Glad I could help as I learned something as well :)[/QUOTE]

yes, thats right! :-k  Glad to hear i wan't the only one who assumed that to be normally the case.

As it happens, after all that, i'm not happy with how wallpapoz is performing on my system, so gonna have to scratch it :neutral: 

never mind,

thx again,
--
sophtpaw

---

