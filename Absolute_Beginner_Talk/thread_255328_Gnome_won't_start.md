---
title: "Gnome won't start"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-11
I installed some themes today, and when I rebooted, gnome will not start, I just get a brown screen with the top and bottom bars going on and off all the time. I get the login screen but it is after gnome has loaded that I get the  problem.  I had previously installed the KDE as well, (that is not causing the problem as it has been there for a couple of weeks now) so at least I can start that up.  So what can I do to get gnome working again?  I still haven't been able to work out how to do a backup.  JUST MY LUCK!:( 

Please help me someone!

Russty.

---

### Post by monktbd on 2006-09-11
try to remove/rename the config files for gnome:

.gnome, .gnome2, .gconf, .gconfd

this will reset all the settings you already added though.
thats why maybe renaming them is the better option to see where the error comes from.

renaming in the terminal with:
> mv .gnome .gnomesav
e.g.

---

### Post by Russty of Oz on 2006-09-11
**OH THANK YOU SO MUCH!**

I really don't know how you guys know all these tricks, I am just so pleased that there is so much help available out there.  

This is probably the BIGGEST AND BEST part of switching to Ubuntu!  Try getting any help from MS for Windows!!  They don't want to know you!

So thanks again monktbd!  You saved the day!

NOW, I must get onto that backup I keep saying I will do.

Russty.

---

### Post by monktbd on 2006-09-11
you're welcome :)
glad it helped.

edit: oh and after a while you get to know the tricks, good thing with linux is that there is often a really easy trick since config files are just text files and easy editable :).

---

### Post by Russty of Oz on 2006-09-12
It has done it again :( 

At least now I know what did it.  But now I cant get it back, when I put in that code, it says it can't overwrite that directory

What now?

---

### Post by Najand on 2006-09-12
Move it to something else like
```

mv .gnome .gnomesav2

```

---

### Post by Russty of Oz on 2006-09-12
Ah!  I see, that sounds like it is worth a try.

I'll let you know what happens.

Russty.

---

### Post by Najand on 2006-09-12
Sure, take your time!

---

### Post by Russty of Oz on 2006-09-12
I had a bit of a problem with rebooting, but it has finally worked and I did what you suggested and YES, it works! I will have to keep away from those other themes!  I got one from art.gnome.org and it looked great, but obviously didn't like my computer.

Thanks for helping me out of that hole.  

Russty.

---

### Post by Najand on 2006-09-12
It is good you could make it... However, never give up when facing a problem in Linux... There are problems which help people to learn more... If I were in your shoes, I would try installing those themes again and again... Can you tell me how did you try installing those themes?

---

### Post by Russty of Oz on 2006-09-12
I just saved the theme, then dragged and dropped into the theme box.  Then I clicked Theme Details, and clicked on the theme I wanted.  The theme worked, well sort of, I got a couple of messages saying that the clock and something else had to stop working, but the overall theme showed.  The one I liked was called GreenHeart.  It is just that when I rebooted, I couldn't get gnome to work.  Thankfully I had installed the KDE as well. 

Russty.

---

