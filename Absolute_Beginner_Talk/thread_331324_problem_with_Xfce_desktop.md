---
title: "problem with Xfce desktop"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by queyrel on 2007-01-04
Hi, 

First, i'd like to apologize for my english (i'm french), and my poor knowledge in linux systems (even tough i know some basis)

Here is my problem :
I'm under Xubuntu for a while and i am really satisfied with it. Nevertheless, it's been a month ago, the "application" button in the upper tasks bar of the screen failed to appear while starting Xfce. Hopefully i'm still able to reach its contents by pressing the right button of the mouse on the desk. But, a week ago, it was the upper and lower task bars turns to disappear.
I don't know wether it's important, but i've got a Compaq laptop. Plus, it is possible (but not sure) that the tasks bars disappeared after the laptop turned out of power and so shootdown without any precautions. 
Finally, maybe it's nothing to do with that, but the same problem occured to me while I was running under my former distribution (FC4).

Hoping that you'll understand,
thanks you in advance for your answer.

J.Q.

---

### Post by jvc26 on 2007-01-04
Hi there you were perfectly understandable - is it possible if we can have a bit more info? - Processor/ram/graphics/hard drives then we can have a bit more to work with? Thanks,
Il

---

### Post by queyrel on 2007-01-04
Sure :

> processor : Pentium IV, 2,4 Ghz,
> ram : 256 Mo, DDR SDRAM
> hard disk : 40 Go, 4200 t/mn
> graphic card : Radéon IGP 345 M

thanks

jq

---

### Post by maxamillion on 2007-01-04
Sounds to me like you panel crashed ... here's what you do

hit alt+f2 and that will bring up a run dialog, in that run dialog enter 
```
xfce4-panel
```

that should bring back your top and bottom panels, and if your applications menu isn't there, right click on the panel you would like it placed, click "add new item" from the menu that pops up during the right click, and select "Xfce Menu" and add it to the panel.

If none of that works, there might be something wrong with your configuration file and if that is the case, I will post a walk through for fixing that.

So try this and post back if you have further problems.

---

### Post by queyrel on 2007-01-04
It does work perfectly ! :) 

Thank you very much maximillion,
and Illuvator too, for your relpy.

---

### Post by maxamillion on 2007-01-04
Anytime. :)

---

