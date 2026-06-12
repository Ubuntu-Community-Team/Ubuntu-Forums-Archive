---
title: "[SOLVED] running programs"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-09-08
Having a small issue here How do I run a program that is not available on my applications menu? i searched for it under system>preferences>main menu and looked everywhere for it i tried running the program name with run application it just opens the file that i downloaded and i see a bunch of files. ive downloaded 2 programs one from synaptic and another from add / remove and they are missing!

 help is much appreciated thanx!

V

---

### Post by forestpixie on 2007-09-08
Have you tried runnin them from the terminal - 

which programs are they

---

### Post by Vic! on 2007-09-08
one was a virus scanner and the other was a doom game

---

### Post by Vic! on 2007-09-08
by the way i deleted them both now using synaptic since i couldnt find them . but just in case i want to download something in the future and it happens again how would i go about doing this.  i dont know how to run an application from the terminal by hand

---

### Post by njknight on 2007-09-08
If this is a program you have installed then open a terminal and type the following 
which (program name)

eg, typing 'which gimp' returns the path /usr/bin/gimp

to run a program use the Alt key + F2 which will open up a run application window - then type the full path of the application you wish to run into the window an hit enter - that's it.

If it's a program that you want to run frequently you can edit the main menu and add the program into it and you can also create an new 'application launcher' eg on the desktop.

---

### Post by forestpixie on 2007-09-08
If you install a program with synaptic, add/remove, apt-get or aptitude (both of which you'll get to know) - a menu item will be added if it's needed.

As njknight has said it's easy to either add to the menu or add a launcher to either the panel or the desktop if you want to.

When you're looking for the file to run they'll usually be in /usr/bin.

And to run a program in the terminal (Apps >accesories >Terminal)
 you can use the program name - ie typing ```
gimp &
``` would run it and allow you to use terminal again. That's not much different than using the command prompt in win .

---

### Post by Vic! on 2007-09-08
i just went back got the virus scanner again and did the 

which aegis-virus-scanner

it told me 

/usr/bin/aegis-virus-scanner

i typed it in the alt + f2 run application hit eneter and absolutely nothing happened ??

what can i do now?

---

### Post by Vic! on 2007-09-08
i tried 
aegis-virus-scanner &
 and i didnt even get the prompt back
  ie
user@linuxthingy$

---

### Post by forestpixie on 2007-09-08
I'm sure that someone will challenge this if there's good reason but you might be better off running another av (if you feel you need to) - have a look at this [page]("http://jodrell.net/journal/article/jgjgge.html")

aparently the version in the repos is broken

---

### Post by Vic! on 2007-09-08
yea its cool frost thanx anyways guys  i will find a diff scanner program :) thx for the link frost!


:)

---

### Post by forestpixie on 2007-09-08
I believe people use clamav - but I have no idea how to use it :D

Edit - new thing to learn :) - if you go to thread tools you can mark thread as solved

---

### Post by 3rdalbum on 2007-09-08
There's a link to a Youtube video in my signature which answers your question.

---

### Post by Vic! on 2007-09-09
Thanks third that video was handy. thanks frost will do :) !

---

