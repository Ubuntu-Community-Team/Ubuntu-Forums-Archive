---
title: "Switch back to metacity?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Phristen on 2007-11-04
Forgive my noobness, but how do I switch back to metacity from emerald?
"metacity --replace" kind of works, but if I do that, then compiz-fuion will get turned off as well... That is, the "None" option will be automatically selected in the preferences>>appearance>>visual effects menu... And if I then select anything other than "None", the theme will switch to emerald again! :confused:
The only way I was able to make it work is by removing emerald, but I sure hope there is a simpler solution.

Also, why are we supposed to run the "--replace" commands via Alt-F2, rather than in terminal? What are the differences between the two, and when should they be used? I'm a total Linux noob, sorry :confused:

---

### Post by dpar on 2007-11-04
In ccsm under 'window decoration' type in gtk-window-decorator on the command line.
Then when you run compiz --replace you will have compiz but not emerald.

No difference between terminal and alt f2. They both do the same, but alt f2 is a more gui type interface.

---

### Post by Phristen on 2007-11-04
Thank you for replying.

If I put "gtk-window-decorator" in "command" field under window decorations and then run "compiz --replace", the screen will flicker a little bit, but that's pretty much all that happens.

However, if I just run "gtk-window-decorator --replace" in terminal, then it will change the theme and compiz will stay (just what I wanted),
But... When I go to the appearance>>visual effects, change it to "None" and then immediately change it back to "Custom", emerald comes right back.

In fact, while the gtk-window-decorator is active, if I run "compiz --replace", then that will also revive emerald.
Emerald just doesn't wanna let go :)

---

### Post by dpar on 2007-11-04
You don't have emerald in the 'command' field in window decorations, do you? That will start emerald any time compiz starts.

---

### Post by Phristen on 2007-11-04
No, I have "gtk-window-decorator" there.

---

### Post by Marc Hoffman on 2007-11-05
I am having the same problem. Every time I restart emerald is back.

---

### Post by quinnten83 on 2007-11-05
I started a similar thread here:

[http://ubuntuforums.org/showthread.php?t=602499]("http://ubuntuforums.org/showthread.php?t=602499")

I didn't receive an answer yet.
Also I can't seem to be able to import icon themes, I just don't have the button like I did in feisty.

---

### Post by dfreer on 2007-11-05
> **Phristen said:**
> However, if I just run "gtk-window-decorator --replace" in terminal, then it will change the theme and compiz will stay (just what I wanted),
But... When I go to the appearance>>visual effects, change it to "None" and then immediately change it back to "Custom", emerald comes right back.

In fact, while the gtk-window-decorator is active, if I run "compiz --replace", then that will also revive emerald.
Emerald just doesn't wanna let go :)

Let me get this straight. When you run:
```
gtk-window-decorator --replace
```
It uses metacity theme like you want with compiz, just the way you want it right? Then why not add that command to your startup session, and don't mess with the **Appearance > Visual Effects**?

I'm probably misunderstanding, but I'm thinking uninstalling emerald would be the simplest solution. 

Also, the difference between running a command via <Alt>+F2 and the terminal? Basically, let's say you are running metacity normally, and want to switch to using compiz. If you were to type:
```
compiz --replace
```
in terminal, you would be running compiz **until** you close the terminal window. Basically, if a program is running in terminal and you close it's terminal, the program along with the terminal gets killed.
<Alt>F2 launches the program directly, so compiz --replace will continue running until you tell it to stop otherwise.

---

### Post by Marc Hoffman on 2007-11-05
Thanks for that last post- I was just on the verge of reinstalling but we are now back to normal

---

### Post by Phristen on 2007-11-06
Thanks for clarifying the Alt-F2 & terminal thing.
As for emerald, the solution was to edit the /usr/bin/compiz script, which would otherwise use emerald by deafult, if it existed.

---

