---
title: "Eeep!"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by YeahYeahYeahs on 2007-10-03
Hello good people of Ubuntu!

I'm completely new to Ubuntu! My dilemma is my mother is now writing articles for a spanish newspaper and I need to know how to convert her generic keyboard into one that has all the accented letters or if anyone knows the...commands? for it I'd be extrememly grateful. I also tried poking around myself before I resorted to using the forums. 

Umm, thank in advance!

---

### Post by Martje_001 on 2007-10-03
System --> preferences --> keyboard

---

### Post by YeahYeahYeahs on 2007-10-03
Riiight...the way she wants it is that she'll be typing without having to stop and go to symbols etc. Is that possible?

---

### Post by eljalill on 2007-10-03
Did you find the place the post before mentioned? If you go to the menu, and then in systems>preferences>keyboard (as mentioned) you have a option "layout" (second from the left I think). If you click on "add" you can add a Spanish keyboard and then change the keyboard settings to that. That way it would be like a normal spanish keyboard. OK?

---

### Post by YeahYeahYeahs on 2007-10-03
so how would I load that?

---

### Post by YeahYeahYeahs on 2007-10-03
Umm, she wants the accents without jumping thru the hoops. Is that possible? I apologize if I'm being annoying.

---

### Post by eljalill on 2007-10-03
You don't have to load it, these are the system preferences, they are there by default. Do you understand what I am (we are) talking about? The main menu, and then systems etc? If you have the defualt gnome desktop the main menu is on the upper left corner.

Then you are switching to another keyboard layout, so your mom can do accents just like with any spanish keyboard. You can look at the layout before you add it, to see, which looks familiar if there are many options (which there are for spanish).

PS: Don't apologize, it's fine. I am just not quite sure, whether we are understanding each other ... :)

---

### Post by YeahYeahYeahs on 2007-10-03
Ok, going by what you are saying I chose the Latin American sun dead keys. I attempted to type out a phrase with words that specifically had accents, and nothing. Am I doing something wrong? or is that how it is?

---

### Post by eljalill on 2007-10-03
Hm. you should have the box for that keyboard checked?
If that doesn't help, try moving it to the top of the list (with the "up" button on the left), and keep the box on the right checked.
Does that help?

---

### Post by YeahYeahYeahs on 2007-10-03
In that menu Latin American sun dead keys it is the only one option  there and of course it i checked.

---

### Post by eljalill on 2007-10-03
That's odd, it certainly works for me, if I do the above.
hm. Maybe your LoCo team knows more? There are quite a few Latin American Loco Teams (Look on the "home" page of this forum for the LoCo teams forums)

Sorry!

---

### Post by Robertorps on 2008-04-05
I have the same isuue on Xubuntu!!!!

I tried the latin american layout with sun dead keys and it does not work, nor the spain version of it.  The keys are fine, because with a dvorak layout (which changes almost everything else) I can print the characters with accents.

The thing is that the system doesn't recognize dead keys strokes in any layout.

Does anyone know a solution?

---

### Post by mivo on 2008-04-05
Have you tried leaving it on "default", without the "sun dead keys" option?

---

### Post by Robertorps on 2008-04-06
I think I have a way to solve the problem.

On the "keyboard settings" application, under the "Layouts" section, there is an option called "Use X Configuration". Enable this option and close the window.

Now, type

 ```
sudo mousepad /etc/X11/xorg.conf
``` (mousepad is the default notepad for Xubuntu, you can use whatever you want).

In the file look for the option "XkbLayout". The default value for this option is "us". In my case, I wanted English layout (that's the layout for my keyboard) and Spanish layout (I live in Mexico), so I changed it to look like this:

"XkbLayout"       "us, es"

You can use the code name you want (swe for swedish layout, latam for latin american, etc).

After that, restart the computer (I think that logging out works too). Once you are back, you should be able to switch the keyboards layouts by clicking the icon on your toolbar (If you haven't added it yet: right click on the bar, add item and look for the keyboard Layout Switcher).

This worked for me.

For some reason, when you try to add the board layouts using the "keyboard settings" program, it does not recognize the sun dead keys on any layout.

Hope it helps. Reply if there are question, and forgive my spelling.

---

