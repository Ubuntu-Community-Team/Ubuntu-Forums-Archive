---
title: "Urgent Problem."
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Nobel on 2006-07-24
I'm having a quite serious problem with the fan on my nVidia Geforce 5700 card.

I've managed to install the drivers correctly recently (nVidia splash screen shows before login screen)

My problem is , that my fan stops from time to time. This happens when im turning of the GUI (to go into console, CTRL + F1), and it is not turning on again when re-starting the GUI. (CTR + F7), it also happens when shutting down the system and/or rebooting.

I consider this an urgent problem. Of course i can just avoid going in to the console for the time being, but considering the constant heat this summer, it's not healthy everytime im rebooting (wich is happening often, seeing as i am a linux newbie :) )
Any help?

Can i provide logs or anything to help solve the problem?

Thanks in advance
Nobel

---

### Post by richbarna on 2006-07-24
> **Nobel said:**
> 

My problem is , that my fan stops from time to time. This happens when im turning of the GUI (to go into console, CTRL + F1), and it is not turning on again when re-starting the GUI. (CTR + F7), it also happens when shutting down the system and/or rebooting.



Hi nobel, 
I don't understand why you have to keep going to the console, unless you are regularly changing your xorg file/ drivers or something else graphical.

Most command line work can be done from the terminal. As for your fan turning off, I'm not sure.

Another tip: When you post on the forum, you will get a faster response if your thread is titled correctly :) 

ie. "nVidia Geforce 5700 fan keeps turning off"

Hit "Alt + F2" to get the run box, type "nvidia-settings" and see if you have anything fan-related there.

---

### Post by Nobel on 2006-07-24
Well, i admit console work is not needed so much at the moment (it was when trying to install nVidia drivers)

But still, i'd like to keep all my fans running at all times (they're there for a reason )

My nVidia-settings reveal nothing about my fan.

Any other ideas ?

Oh, and thank you for your quick response richbarna :)

-Nobel

---

### Post by richbarna on 2006-07-24
Hi Nobel,
I did a bit of googling and it seems that when your card thinks it's not running in 3d, it/(the driver) turns the fan off regardless of the temperature (which will not fry up to 100C apparently, so you are safe ;))

This is what happens when you use a non-3D screensaver or non-3D graphical mode :-
> This behavior was confirmed by Croteam who tried it with a NVIDIA reference    board they received from NVIDIA Developer Relations, and also by a friend of    mine with a MSI GF FX 5800 Ultra card. Also, if you try running the screensaver    in the preview mode, the fan will spin the whole time. For this to work, it    has to be done with a "real" screensaver, not with the preview of one. I am    off to try this on a different system (just to make sure for one more time)    and then I&#8217;ll start trying different Detonators.
 Why this is happening? Well, we think that for some reason when    using a 3D screensaver the card, or its drivers, decide the card is not running    in 3D mode and stop the fan. The problem, of course, is that regardless of the    temperature the card reaches, the fan won&#8217;t start running again (as long as    you don&#8217;t exit the screensaver and start running 3dMark or some game like Il2    Sturmovik, Quake 3, etc.). This means that NVIDIA has made a big overlook on    how the whole system of cooling-on-demand (i.e. when you are in 3D, or when    you a reach high temperature) works. Basically the whole thing obviously works    on the basis that the card/drivers will realize they are running in 3D, instead    of also taking the temperature in consideration.

From this website :-
[http://www.pcekspert.com/articles/127-1.html](http://www.pcekspert.com/articles/127-1.html)

---

### Post by Nobel on 2006-07-24
So, you suggest i ignore the problem ?

I could do this, altho i am not verry happy about it.

-Nobel

EDIT: Thanks for all your help, i did a bit of googling myself, and found nothing useful :)

---

### Post by richbarna on 2006-07-24
Well basically, if you don't use the console, or dodgy screensavers, your fan should keep running.
Also, keep an eye on the link in my previous post, as nvidia may have something to say. Another option could be to install another fan if you think that the card temperaturer might go above 100C.

---

