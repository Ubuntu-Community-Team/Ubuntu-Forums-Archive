---
title: "Keyboard shortcut to switch between desktops"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by jbj on 2007-06-01
I'm having a bit of a thick 29 years... can someone please humour me and tell me the keyboard shortcut to switch between desktops?

I have tried, honestly!

---

### Post by jonward0690 on 2007-06-01
Well you can go to system, preferences, keyboard shortcuts and look there and you can change them if you want to.

---

### Post by daimaru on 2007-06-01
ctrl+alt+cursor keys left right

---

### Post by jbj on 2007-06-01
Oh yeah... :redface:

Thanks!

---

### Post by daimaru on 2007-06-01
\\:d/

---

### Post by jbj on 2007-06-01
I've no idea what that smily means, but I imagine you're telling me I'm lame... (and you are true) :)

---

### Post by daimaru on 2007-06-01
> **jbj said:**
> I've no idea what that smily means, but I imagine you're telling me I'm lame... (and you are true) :)

hell no ... i suck at ubuntu stuff too, no offense intended mate. and the stupid smily doesnt even display 4 me ... in only see the friggin text

---

### Post by jbj on 2007-06-01
haha, no offense taken whatsoever :) But if you really want to make amends, you could always help me get Amarok as my default music player, as seen in one of my many idiotic questions tonight ;)

---

### Post by daimaru on 2007-06-01
> **jbj said:**
> haha, no offense taken whatsoever :) But if you really want to make amends, you could always help me get Amarok as my default music player, as seen in one of my many idiotic questions tonight ;)

thats an easy one just right click on a mp3 file choose properties -- > open with --> select amarok and your good to go

edit: sorry just read your original post and saw that someone already suggested that and it wont work for you. 
how did you install amarok? 
i typed sudo apt-get install amarok and for me it lists it in the open with tab .. but you could still just say (under open with tab -- add) and select it from there or if it is not listed there, expand the " use custom command " option and enter "/usr/bin/amarok" without quotes. 

to check type in terminal 
```
whereis amarok
```
that should give you the path to your amarok installation

---

### Post by jbj on 2007-06-01
Argh! If only it was that simple :( It soesn't seem to want to do that for me.

---

### Post by daimaru on 2007-06-01
bumping so you check answer , edited my last post check that

---

### Post by jbj on 2007-06-01
Thanks for your help, but I can see it there and Ubuntu is refusing to remember it as the default player. I installed it via 'add programs' in the applications menu, I also used 'Automatix to get my codecs, I don't know if this could have screwed things up...

Anyway, I'll tackle this further in the morning as it's getting a *little* late for me ;)

---

### Post by daimaru on 2007-06-01
no i also used automatix. 
but i had the same problem with pdf files they were being opend by some default prog but i wanted adobe reader (or acrobat) or whatever.
it showed up in the open with menu but i could not select it. entering the custom command didnt work either. 
my suggestion go in terminal 
```
sudo apt-get remove amarok
```
or in your add remove programs --> uninstall amarok then type in terminal

```
sudo apt-get autoremove 
sudo apt-get autoclean
sudo apt-get install amarok

```
first 2 commands are supposed to remove redundant suff (but in dont know much about this either) 
and the last one reinstalls amarok. 
i mean what have you got to loose just try uninstall reinstall xept if u got a very slow internet connection.

---

