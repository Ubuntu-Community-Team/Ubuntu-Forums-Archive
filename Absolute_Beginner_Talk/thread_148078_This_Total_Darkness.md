---
title: "This Total Darkness"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by ububaba on 2006-03-21
I was almost proud that finally I was in control of my Breeze Badger. It soured up 
when I updated the nVidia driver to the latest, and did a re-start. All went according 
to the script, after the brown and then black start-up screens, I could hear the jungle 
drums....and then the screen turned dark. (I have mentioned about this catastrophic 
problem somewhere else too.) I simply cannot see the login screen anymore.

I have tried to work around the problem, by finding a way to "repair". The best offer 
I get, is to wipe everything off the harddisk. No need to say that I am not all that 
enthusiastic about it.

Will somebody much higher on the food-chain give some hint, how can I get out 
of this total darkness and hug my Badger again. Plenty of thanks in anticipation.:-k

---

### Post by Perfect Storm on 2006-03-21
Boot into failsafe (hitting esc when it count down 3-2-1).
Log in with your username, enter password.

```
sudo nano /etc/X11/xorg.conf
```
(you might read up on how to use nano if you havn't tried it before)

Move down to Section "Device"
and changee Driver "nvidia" to Driver "nv"
(remember linux is case sensitive).

Save and exit
reboot

---

### Post by Brunellus on 2006-03-21
note that the above solution will not give you hardware acceleration.  Pooh.

---

### Post by Perfect Storm on 2006-03-21
Aye, I should have mention that. :p

---

### Post by ububaba on 2006-03-21
[QUOTE=Artificial Intelligence]Boot into failsafe (hitting esc when it count down 3-2-1).
Log in with your username, enter password.

```
sudo nano /etc/X11/xorg.conf
```
(you might read up on how to use nano if you havn't tried it before)

Move down to Section "Device"
and changee Driver "nvidia" to Driver "nv"
(remember linux is case sensitive).

Save and exit
reboot[/QUOTE]

I should have said, the dark screen in fact is apparently the login screen but
somehow due to improper configuration nVidia overrides the default screen.
Just a guess. Any way I will try your recommendation. Thanks

---

### Post by ububaba on 2006-03-21
[QUOTE=Artificial Intelligence]Boot into failsafe (hitting esc when it count down 3-2-1).
Log in with your username, enter password.

```
sudo nano /etc/X11/xorg.conf
```
(you might read up on how to use nano if you havn't tried it before)

Move down to Section "Device"
and changee Driver "nvidia" to Driver "nv"
(remember linux is case sensitive).

Save and exit
reboot[/QUOTE]

I followed the instructions provided by**Artificial Intelligence **but 
unforunately the situation was not any different from ealier. The 
machine did not reach the point where the login screen appears. 
It became blue black after the drums. No failsafe boot for me.
Some other tricks in the bag?

---

### Post by Brunellus on 2006-03-21
replace "nv" with "vesa" and live with that until you can find a better solution.

---

### Post by ububaba on 2006-03-21
[QUOTE=Brunellus]replace "nv" with "vesa" and live with that until you can find a better solution.[/QUOTE]
Sorry **Brunellus** I cannot login. There is a stop before that as the login
screen is not visible. There is no way for me to write anything!!!

---

### Post by Brunellus on 2006-03-21
can you see anything at all when it starts up--the textmode stuff?

or rather

what happens when you hit CTRL+ALT+F1

that should get you a textmode console unaffected by your xorg problems.  all text, all the time, and enough to get stuff fixed.

---

### Post by manicka on 2006-03-21
You could also try just reconfiguring X by running

```
sudo dpkg-reconfigure xserver-xorg
```

after hitting ctrl-alt-f1 and logging in

---

### Post by ububaba on 2006-03-21
[QUOTE=Brunellus]can you see anything at all when it starts up--the textmode stuff?

or rather

what happens when you hit CTRL+ALT+F1

that should get you a textmode console unaffected by your xorg problems.  all text, all the time, and enough to get stuff fixed.[/QUOTE]

Everything looks normal and perfect at the start. It is precisely after the jingle
the screen starts looking blue black and after a few seconds turns into pitch
black.

I will try with CTRL+ALT+F1, but at what moment?

---

### Post by AndrewCaul on 2006-03-21
[QUOTE=ububaba]Everything looks normal and perfect at the start. It is precisely after the jingle
the screen starts looking blue black and after a few seconds turns into pitch
black.

I will try with CTRL+ALT+F1, but at what moment?[/QUOTE]
Well, at the moment you have to use the console. You can't see X.

---

### Post by Brunellus on 2006-03-21
when it's all over.  CTRL ALT F1 will switch from the X session (the usual graphical login screen that you can't see) to the textmode console (the Oldskool command line that shouldn't be affected by anything)

---

### Post by ububaba on 2006-03-21
Thanks guys. By pressing CTRL+ALT+F1 I could get to the text mode and there I 
wrote sudo nano /etc/X11/xorg.conf and configured the file as suggested. All worked
like a charm.

Next problem......

---

