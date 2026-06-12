---
title: "This Prank I was told about confuzzles me"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-02
What is a GTK theme, and how do I apply one? I was reading this, very controversial might I add, posting about make Ubuntu look like Vista, and (having anti-Vista roomies), I too decided to play this prank. But this whole tutorial confuses me :

> [http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html](http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html)

Does anyone have a more straight-forward, teach-a-"n00b" guide to help me pull this wonderful prank :popcorn:

---

### Post by eternalsword on 2007-07-02
as for gtk theme, you can install that through gnome-theme-manager.  looks like they have to be running beryl though for this to work correctly.  beryl themes are installed through emerald (a ruby icon in the system tray).  if there is no ruby in the system tray, this won't work the way you want

---

### Post by Raineer on 2007-07-02
Try entering ```
emerald --replace &
``` at a command line (or Alt-F2) at see if it does anything.  If so, you've got a chance at making it work. If not, you'll need to follow one of the links on these forums for installing Beryl. There are several stickied links with instructions for this.

---

### Post by tcoffeep on 2007-07-02
> **Raineer said:**
> Try entering ```
emerald --replace &
``` at a command line (or Alt-F2) at see if it does anything.  If so, you've got a chance at making it work. If not, you'll need to follow one of the links on these forums for installing Beryl. There are several stickied links with instructions for this.

When I do type that, what I get in responce is :

> [1] 13549

Does that mean it works or something?

---

### Post by eternalsword on 2007-07-02
did a window pop up titled something like Emerald Manager?

---

### Post by tcoffeep on 2007-07-02
Nope. It just said "[1] 13549" and thats all. But thats from the terminal.

Although I had started running Beryl, and typed it, and what I get is now "[5] 13797
[3]   Done                    emerald --replace"

Am I missing something? I had installed Emerald.

---

### Post by Raineer on 2007-07-02
Well the numbers you are seeing just mean that it opened the process (the '&' on the end just make it run in the background, so you can close the terminal and it won't close emerald)

You should now be able to go into preferences or administration and be able to open a theme manager for Emerald, as if it wasn't found you would have gotten an error message.

---

### Post by tcoffeep on 2007-07-02
OK, and for another question.

This tutorial gives links to d/l tar.gz files. How exactly do I run these?

Do I extract them, or is there another method to doing this?

[as it the tutorial does state that I have to install these themes, but in order to install the, I need to extract them or what? :S]

---

### Post by Raineer on 2007-07-02
Yes they are extracted. You can do this from your file browser, but to be honest it's even easier from the terminal.

Go to the directory where the files exist and type
```
tar -xf yournewfile.tar.gz
```
This will create the directory the files belong in and put them there, a lot faster than clicking through archive manager in my opinion.

Also, in case you aren't aware, some of these filenames get pretty long and annoying to type. Start the first few characters and press [TAB], it will autocomplete the filename or beep letting you know there are more than one that match the description (pressing [TAB] a second time will list all the files matching what you've typed so far)

---

### Post by tcoffeep on 2007-07-02
Thanks for the tip.

Now I attempted to install the Emerald theme, but it always come up with the Papered "X" if you know what I mean. *confuzzled...but closer to finishing the god-forbidden journey*

---

### Post by tcoffeep on 2007-07-02
Also (god, I must be annoying),

How do I install the theme?
Every time I go to the Theme manager, I click "install theme" and double-click on the *.theme file...and it keeps coming up as "invalid format"...ideas?

---

### Post by TrueJk7 on 2007-07-02
> **tcoffeep said:**
> What is a GTK theme, and how do I apply one? I was reading this, very controversial might I add, posting about make Ubuntu look like Vista, and (having anti-Vista roomies), I too decided to play this prank. But this whole tutorial confuses me :



Does anyone have a more straight-forward, teach-a-"n00b" guide to help me pull this wonderful prank :popcorn:
That is awesome! Gonna do that soon

---

### Post by eternalsword on 2007-07-02
> **tcoffeep said:**
> Also (god, I must be annoying),

How do I install the theme?
Every time I go to the Theme manager, I click "install theme" and double-click on the *.theme file...and it keeps coming up as "invalid format"...ideas?

it's probably looking for the tarballed format.  did you extract from a .tar.gz?  if so try installing the .tar.gz instead.

---

### Post by tcoffeep on 2007-07-02
That actually worked, but what about the improper emerald theme?

---

### Post by tcoffeep on 2007-07-02
This is so frustrating.
Is there tutorials for this kinda stuff? I really really want to do this prank (although I'll probably get punched in the face for it, but it's totally worth it)

---

