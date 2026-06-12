---
title: "Workplace Spaces Into Cube???"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by GorillaDilla on 2007-07-08
Sorry, I am very new to Linux, and just spent 32 hours getting WoW and other things to work, but it was fun. Now i realised that there is no minimize key A.K.A - The windows/little flag key. I was wandering how i make it so i can view them as a cube, like i zoom out, then can scroll around and pick whcih one i want.

---

### Post by proalan on 2007-07-09
You talking about beryl?

if so then do in a terminal

```
sudo apt-get install beryl-manager
```


minimising all windows 

```
CTRL+ALT+D
```

window menu options are as in that other operating system

```
ALT+SPACE
```

one thing to beware of when using beryl, there are alot of global shortcuts defined that may clash with any you have defined with other apps

---

### Post by Sklasko on 2007-07-09
Just to note, Beryl (and compiz as far as I know) will result in a loss of 3D acceleration.. meaning that WoW and Beryl won't cooperate.

---

### Post by johntkucz on 2007-07-09
Hi i've installed beryl manager with 

sudo apt-get install beryl-manager

the icon appears in the upper right of the desktop.  I am able to set preferences fine, however, when I go to "Select Window Manager", there are the options of Beryl, Compiz, or Metacity.  I cannot select Beryl (it revets to metacity-gnome); when I select Compiz, it behavs just like gnome does.  How do I get the cube effect going? 


Thanks.

---

### Post by coolen on 2007-07-09
Feisty comes with Compiz. It's a fairly minimal setup, though. Try dragging some windows around, and see if they go wobbly. You don't have the workspaces cube to begin withl. I think there's a menu entry in Preferences where you can do some basic setup.
If neither is working, then, well, they're not working, for whatever reason. beryl-manager, the program sitting in your notification area, takes care of the current window manager/decorator. It'll automatically fall back to Metacity (or another window manager of your choosing) if the current one fails.
I can't really help you out with these, though. It's been ages since I got mine set up successfully. I used to know a few handy commands, but they escape me now.

---

### Post by GorillaDilla on 2007-07-09
Yes, I learned that this version of Linux, ATI, WoW, and Cube View, do not comply very well. Thank you for your information, I will keep trying.

---

### Post by sailor2001 on 2007-07-09
I found that when my broadband drops below 100kbs from the supplier I can't get into beryl    check [www.speedtest.net](www.speedtest.net)

---

### Post by Mazza558 on 2007-07-09
> **Sklasko said:**
> Just to note, Beryl (and compiz as far as I know) will result in a loss of 3D acceleration.. meaning that WoW and Beryl won't cooperate.

Does it? I can run 3d stuff and beryl at the same time fine.

---

### Post by coolen on 2007-07-10
I know using OpenGL applications with XGL is a pain, but I think AIGLX is better for it. Makes sense, as it's part of your X server.

---

