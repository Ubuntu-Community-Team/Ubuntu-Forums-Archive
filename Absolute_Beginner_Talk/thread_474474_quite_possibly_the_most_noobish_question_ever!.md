---
title: "quite possibly the most noobish question ever!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Bleak Outlook on 2007-06-15
brand new linux user
i signed up ages ago but could never get online (speedtouch 330 usb modem) using ubuntu so gave up
i been using this for just over a week and well being a windows user 
(not the cool kind, i leant on xp so have very little knowledge of command lines or this thing called a terminal)

decided i need to broaden my vision a little (plus beryl looked kick ****)

OK so now you know my history i spose i should ask my question

Is there a way of taking certain updates off the list so the reminder doesn't continuously tell you they are there?

i have a radeonX1300 pro card and beryl doesn't support it but after sleepless nights and lots of reading swearing and reading some more ive got it to work perfectly (touch wood)

but the updates keep trying to up date everything beryl wise and i know from "ok lets see wot happens" that buggers it up

is there a way to stop the update thing from seeing them as an update option?


now for my proper noob question

ive seen some desktops with a giant home folder displayed on them
how does that work as the desktop is in the home folder ?
and getting it to display could possibly create some sort of spacial loop that might suck my computer and quite possibly you all into ..... well you get the picture


thanks for your help in advance :D

all the best and be lucky
bleak :(

---

### Post by ashz on 2007-06-15
You can drag a copy of your home folder from the Places menu onto your Desktop. Then right click on it. (There is some option there to resize!!)

Personally I would allow it to update, and I dont know a way of refusing to update...Sorry!!

Laters
Ash

---

### Post by Bleak Outlook on 2007-06-15
thanks for the quickness of your answer
i knew it would be something simple like that :---)

as ive said i have tried letting it update but i loose my title bar with my minimise, maximise and close buttons (they are still usable if mouse over them but i cant see them?)

oh well its no biggie just annoying to have to untick each one each time i update ](*,)

thanks again
be lucky
bleak:sad:

---

### Post by dreadlord_chris on 2007-06-15
> **Bleak Outlook said:**
> ive seen some desktops with a giant home folder displayed on them
how does that work as the desktop is in the home folder ?
and getting it to display could possibly create some sort of spacial loop that might suck my computer and quite possibly you all into ..... well you get the picture
(

This made my morning, thank you.....:lolflag: I had to put the coffee down before it came squirting out my nose....

Anyway, as to your update question - I'm assuming you're using Synaptic Package Manager? Click on the package you don't want to update, click Package (from top menu) > Lock Version
You will still be notified that updates are available for the packages - they just won't be automatically selected anymore.

---

### Post by zeeR on 2007-06-15
If you don't want to be notified, you can click "Force Version", on the Package dialog on Synaptic.

That's how I keep the 0.2.0 version of Beryl (the 0.2.1 isn't stable on ATI cards)

---

### Post by bodhi.zazen on 2007-06-15
I do not know if this is exactly what you are looking for, but I do essentially a very similar thing with wine.

I have a complex wine setup and I do not want wine to be updated, so put it on hold :

[http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold](http://doc.gwos.org/index.php/HowToWine#How_to_put_wine_on_hold)

use ```
sudo echo "xyz hold"|dpkg --set-selections
```

where xyz is the package you want to hold.

> sudo echo "wine hold"|dpkg --set-selections
[list][*]for wine[/list]

The link will give you examples and instructions on how to undo this. You will need to do this for each package as I do not think beryl is a meta package.

HTH

---

### Post by Bleak Outlook on 2007-06-20
thanks guys 
my brain hurts
but i think ive sussed it.

---

### Post by Golyadkin on 2007-06-20
Hey, this is a handy tip I was looking for. Thanks!

---

### Post by zidane2 on 2007-06-21
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) is the site i use to get online its easy even for a newbie like me
hope it helps

---

