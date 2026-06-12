---
title: "Bad day! power out just killed Ubuntu"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-03-20
Hi, 
I'm having one megga bad day, really bad....

1) I try to update 6.06 to 6.10, (psychocats) - Failed due to code 2 error.

2) Decide to deinstall kde, which i added alongside Gnome to try out. followed (psychocats) guide.  

```
sudo aptitude remove kubuntu-desktop
```

3) 16 month  old daughter starts to press all the buttons on the dishwasher simultaneously, causing a power out in the entire house. Run to rescue daughter, rescued the dishwasher and reset the fusebox.

4) Notice amongst all the other things that have reset due to  power out that my laptop turned off in the chaos.  Restarted laptop, now i come no further than the console, no Gnome and no desktop.

5) I've no idea how far the sudo apt remove had gotten to, so i  don't know if the problem is due to that process being interupted or due to laptop losing power.
Am now back in windows and looking for some help please.

Anyone willing to make my day just a little bit brighter?

---

### Post by stoer on 2007-03-20
Ok,
Just made my own day brighter... :)

No idea if this was the way to go, but i tried the following.

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure gdm

I've got my desktop back, now to find out why i lost it? and if it's damaged...

Anyone know if the above was the right way to go? or could i have done something better?
Appreciate your feedback.

---

### Post by buuntuu! on 2007-03-20
well, it's not THAT bad after all,

saved your daughter, saved the dishwasher, lost (maybe) your install...
thats
you 2 : life 1
;)

sorry for that...
if it's only about saving your data, given the fact that you wanted edgy, why don't you just put in the live cd, migrate your valuable data and then install from scratch? i know, it takes some tweaking getting everything to run properly, but you'll get to know your system better doing it :)
you could install the window manager you always wanted or the apps you wanted to try out but didn't dare to 'cause you were afraid to mess up your install...

sorry for all the smileys and for being an optimist nag, but you wanted someone to brighten up your day :KS 

do it like monty python's flying circus:
always look at the bright side of life... :grin:

Edit: see? you brightened up your day all by yourself!
you 3 : life 0

---

### Post by stoer on 2007-03-20
"....Give a little whistle....look on the briiiight, siiiide of life!...."

I'm feeling better already, 
except,
Now i've got to go to work :(

"hey-ho, hey-ho....it's off to work i go....":) 

Cheers!

---

### Post by xyz on 2007-03-20
Glad to hear you're OK after all!

One way to have this not happen again is to keep the laptop battery in despite AC power.
Of course, the disadvantage is that it'll use the battery for nothing most of the time!

---

