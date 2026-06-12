---
title: "xvkbd focus and gnome"
date: 2007-04-03
forum: Assistive Technology &amp; Accessibility
---

### Post by ka9qlq on 2007-04-03
I have to use xvkbd to type. In KDE I don't have trouble with focus but in gnome you have to click the focus button on the keyboard then the window I want to type to. Why?
Alvin

---

### Post by frafu on 2007-04-04
You might try the onscreen keyboard shipped with ubuntu called onboard. You can find it in the accessibility menu. 

Francesco

---

### Post by ka9qlq on 2007-04-04
Hay thanks, hadn't heard of that one. Wonder how you change the font? It's kinda small when you shrink the window to a small footprint [390*110]

---

### Post by frafu on 2007-04-05
Hello, 

There is no menu to change the font directly. However, the keyboard layout is customizable, so you can change it by editing the keyboard layout. 

If it has not changed recently, layout files are in a hidden directory called .sok in your home directory. The layout files have .svg as extension and can be edited with an application called inkscape. 

You can use the onboard settings window to make a copy of the default layout and I would suggest to edit the copy.

Francesco

---

### Post by ka9qlq on 2007-04-05
OK I'll look into it thanks

---

### Post by frafu on 2007-04-11
Hello, 

Here is a layout with bigger letters that I created several months ago. Uncompress the zip archive and put the 4 files into onboards layout folder. (You can open the layout folder with a button situated in the settings window of onboard). 

I hope that my modified layout will appear in the layout list after restarting onboard. Otherwise, I will have to look more precisely into it again. 

On my system, the modified layout has a few issues on some keys; nevertheless I hope that it will be useful... 

Francesco

---

### Post by ka9qlq on 2007-04-11
Hay, That's real close. It would be nice to have the top row F keys and the shift work on the 1-0 keys.  If I knew a little more about how to change things........Anyway Thanks.

---

### Post by frafu on 2007-04-12
I am glad that it helps. 

By the way, you can find the Fn keys by clicking on the purple square at the bottom right of onboard. 

You might have a look [here]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=onboard&titlesearch=Titles") , [here]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sok&titlesearch=Titles") and especially [here]("https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions?highlight=%28onboard%29"). 

Have a nice day.

---

### Post by ka9qlq on 2007-04-22
Hay is there a list for keysym f I want to change any keys?

---

### Post by ka9qlq on 2007-04-22
I figured an example of what I wish to do to the layout file you gave me the shift 2 key is " I want it @ like on a regular keyboard and use the @ key for something else not to mention why are the z and y keys switchedß and the question mark as you see doesn´t work. I want to mod your keyboard to use for my use, but will gladly turn any improvements over to you to have credit I just want a cool keyboard. Also wanna assign stuff to he Wn keys.

---

### Post by frafu on 2007-04-23
> **ka9qlq said:**
> Hay is there a list for keysym f I want to change any keys?

If you also installed the developer packages, you might find the list with the keysym in your Ubuntu installation. Look at: 
/usr/include/X11/keysymdef.h

Otherwise, have a look [here]("http://packages.ubuntu.com/feisty/x11/x11proto-core-dev"). 

Have a nice day.

---

### Post by frafu on 2007-04-23
> **ka9qlq said:**
> I figured an example of what I wish to do to the layout file you gave me the shift 2 key is " I want it @ like on a regular keyboard and use the @ key for something else not to mention why are the z and y keys switchedß and the question mark as you see doesn´t work. 
 


I don't know exactly how it works, but the position of the characters of the keys also depend of the keyboard settings in Ubuntu under the System menu. 

>  
I want to mod your keyboard to use for my use, but will gladly turn any improvements over to you to have credit I just want a cool keyboard. Also wanna assign stuff to he Wn keys.


I did not post my layout right away because it is only a little hack not done very well. But if you are going to create an interesting layout, we/you might ask the developer to include it in his official distribution. 

By the way, you should use Inkscape to design the layout of the keys; you can install it with the Synaptic Package Manager. 

Francesco

---

### Post by ka9qlq on 2007-04-23
I have Inkscape but I'm not good at it my keys are never strait :) I just think it'd be easier to reassign some buttons on your board. We'll see. I just need to understand how to mod the .sok file to use shift, Alt, Ctrl, and Wn. I'll keep reading.

---

