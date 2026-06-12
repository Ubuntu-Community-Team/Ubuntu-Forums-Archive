---
title: "How to get NOR keyboard layout.."
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-02-06
Hi!  Im a fresh user in Linux, and therefor i need help to almost everything.
This time it\s about how to get a Norwegian keyboard layout. Right now i have to
use the English keyboard layout, something there is easy to see sometmes;) 
The reason for that i want the Norwegian keyboard layout is that I need the Norwegian special letters, that I can not write here. If you want to see how they look,
I\ve added a link at the bottom of my post. And yes, I have tried almost everything!

I said I would add a link... I might as well Copy And Paste those letters..
Didnt bother editing it ;) 

Here they are >   small  æøå  CAPITAL    ÆØÅ

---

### Post by s6dalane on 2006-02-06
Fire up the terminal and type

> sudo gedit /etc/X11/xorg.conf

Then find the following line

> Option "XkbLayout" "xx"

Change the xx's to 'no' and restart.
When you log in again, choose 'X settings' and you should have a working norwegian keyboard.
This worked for me, hopefully does for you too.

---

### Post by d4rk on 2006-02-06
Ill give it a try...   If it works Ill give a hint;)

---

### Post by d4rk on 2006-02-06
[QUOTE=s6dalane]Fire up the terminal and type



Then find the following line



Change the xx's to 'no' and restart.
When you log in again, choose 'X settings' and you should have a working norwegian keyboard.
This worked for me, hopefully does for you too.[/QUOTE]

It worked fine for me too! :D    Thank u realy much s6dalane for ur help.
All I have to say is    ÆÅØ!

---

### Post by s6dalane on 2006-02-06
You are welcome. :)
I'm glad it worked.

---

