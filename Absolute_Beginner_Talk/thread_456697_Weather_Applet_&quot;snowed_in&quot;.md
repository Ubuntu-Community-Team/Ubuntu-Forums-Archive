---
title: "Weather Applet &quot;snowed in&quot;"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-05-28
I've noticed that the weather applet for gnome lets you change the update frequency all the way up to 1 minute, but on average, the weather it's retreaving is days out of data.  For example, it currently says the last update was 9 o'clock pm, on the 25th!  It's now the evening of the 27th, and this is of course out of date.  I've tryed clicking the update button, but it only gets this info.  My internet connection if working fine, so what's up?

Does anyone else have this problem too? (check, I bet lots do and don't realize it!)

---

### Post by freebird54 on 2007-05-28
There must be something wrong - it is doing this to me too.  The update workds fine, but not automatically).  I didn't notice because I run the adesklets 'weather forecast'  (which gives 3 days as well as current) so I hadn't actually LOOKED at it for days...

I think I read somewhere that it fails if the updates are TOO frequent - but mine have been 30 mins apart for a while now.  Guess we'll have to see if a guru happens upon this thread :)

At least you haven't lost your mind :) - and it doesn't seem to affect the clock/calendar functions in any way....

---

### Post by ryanVickers on 2007-05-28
Just noticed something - recently an hour went by (it went from 9 to 10 pm my time) and the weather applet changed it's last update display to say 25th but 22:00 instead of 21:00.  does this make anyone think something else?  maybe it's behind in days, but it knows the time.  or it's getting the old data but on time 0_o.  I don't know...

Just had another look at it, it's (again) exactly 2 days behind, and I don't know if the weather is actually right, or from the day it says.  I mean, if it's up to date and doesn't know, then it doesn't really matter, but if it's really 2 days old, then that's a problem!

---

### Post by ryanVickers on 2007-05-29
It's improving!  I looked just now and it's got the right date and the hour (has always been right) but it's right too!  it's 4:44 pm here now, and it's got it at 4:00pm.  and the weather info it's got seems to be about right~

---

### Post by ryanVickers on 2007-05-29
Ok, now it's almost 7 pm, and it's gone back to thinking/getting info from sunday (27th) but the hour is still close enough (correct, but only updates every hour).

---

### Post by homergreg on 2007-05-29
You might want to try the "Goodweather" Applet on this page: [http://gdesklets.zencomputer.ca/]("http://gdesklets.zencomputer.ca/")  It gets its weather from weather.com the others are using yahoo, and that combination hasn't been working right for some, or maybe all or all I know.

---

### Post by ryanVickers on 2007-05-29
I've noticed that the gdesklets application doesn't work either.  It used to, but I never really got into it.  Now that it looks interesting, it won't start!

---

### Post by freebird54 on 2007-05-30
Might be easier to run the adesklets version of weather (I use weatherforecast) as it pulls from weather.com (and makes a nice display on your desktop) without hogging resources that I haven't got to spare like the gdesklets seem to.

It certainly works better than the panel one does now!

---

### Post by ryanVickers on 2007-05-30
Ok, I'll try that.

It seems to have installed ok, but how would one start it?  There's no menu item, so I ran the name as a command, but nothing happened.

---

### Post by freebird54 on 2007-05-30
The 'README' file should explain it.  Just run it in test mode:

```
python weatherforecast.py
```

and (R)egister it, then

```
adesklets --nautilus
```

Should appear top left, then you can selct to move it wherever you want.  The config.txt file has all the settings you might want to change.  Go to weather.com to get the char code for your area.. (mine is  **CAXX0504** )  really easy, and really lightweight.  Enjoy!

---

### Post by ryanVickers on 2007-05-30
Sorry, I'm kind of slow with this, so in order, could you just list the things I need to do to get adesklets (have it) then install the weather thing, then add a menu item?

---

### Post by freebird54 on 2007-05-30
Well - first you go to the place where you donwloaded things to:  (mine was ~/Desklets/weatherforecast so 

```
cd ~/Desklets/weatherforecast
```

this puts you into the dorectory where the program files are.  A good time to enter the code you picked up for your city/area from weather.com  To do this you

```
gedit config.txt
```

and look for the line that reads similarly to

```
'location': 'CAXX0504',
```

and replace whatever is in place of **CAXX0504** with your own code entry.  Save, and exit then

```
python weatherforecast.py
```

choose (**R**) to register the application. then

```
adesklets --nautilus
```

this will test that it works and you want it :)  If you decide to keep it ...

Then right click on the Applications menu, choose Edit Menus, then Add Item, then fill it in (What you want the menu item to read, a comment, and the adesklets --nautilues command line).  When you close it - you will have a menu item you can call it up with any time.  

I just leave mine going, as it has no significant hit on resources, even while updating.  Hope this makes it clear!

---

