---
title: "Lost my desktop!"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by pebberbrown on 2007-06-22
Hello out there!
Boy these forums are a fantastic idea.
hey now
I was messing around late last night with the add/remove programs
and I somehow managed to delete something vital to my system

All I get now is a command line interface uponboot with
error message indicating I've lost my X windows.

Is there an easy way to repair this short of re-formatting and re-installing?
If not oh well - I only have 1.6GB of data to extract somehow....
My plan was to install Ubuntu on a NEW HD and then attache teh old HD as a second
drive and grab the data off of it once I was up.

feel free to email me directly

[email]pebberbrown@gmail.com[/email]

[www.pbguitarstudio.com](www.pbguitarstudio.com)
__________________

---

### Post by lazyart on 2007-06-22
sudo dpkg-reconfigure xserver-xorg

---

### Post by josesanders on 2007-06-22
When you get the text interface, you can login and then run the command:

$ sudo dpkg-reconfigure -phigh xserver-xorg

That will reset your xorg.conf file so that hopefully you will be able to get the desktop back.

---

### Post by eluzi on 2007-06-22
All you do on the X (graphical interface) can be done directly in the shell. So try the above tip, If somehow you managed to exclude de X interface completely you don't need to format or anything, u can reinstall it through the shell... Try the previous tips and tell us if it worked...

---

### Post by Crafty Kisses on 2007-06-22
> **pebberbrown said:**
> Hello out there!
Boy these forums are a fantastic idea.
hey now
I was messing around late last night with the add/remove programs
and I somehow managed to delete something vital to my system

All I get now is a command line interface uponboot with
error message indicating I've lost my X windows.

Is there an easy way to repair this short of re-formatting and re-installing?
If not oh well - I only have 1.6GB of data to extract somehow....
My plan was to install Ubuntu on a NEW HD and then attache teh old HD as a second
drive and grab the data off of it once I was up.

feel free to email me directly

[email]pebberbrown@gmail.com[/email]

[www.pbguitarstudio.com](www.pbguitarstudio.com)
__________________

Well, then press Control-Alt-F1 and try this:

```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

---

### Post by shifty_powers on 2007-06-22
Just as an aside, it is generally bad practice to put your own private e-mail address in a post on a public forum. for your own sake ;) There are many spam-bots out there that will trawl forums looking for e-mail addresses to spam ;)

---

