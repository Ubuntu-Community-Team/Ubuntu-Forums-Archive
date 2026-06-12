---
title: "Cool sound icon"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by marko_4454 on 2007-04-27
Does anyone know how to get the volume icon that looks like the screenshot? I am running Feisty...and maybe its just a sudo apt-get install ~~~ and I just dont know the program, but can someone help?

[http://img15.imgspot.com/?u=/u/07/116/02/Screenshot.png](http://img15.imgspot.com/?u=/u/07/116/02/Screenshot.png)

---

### Post by marko_4454 on 2007-04-27
anyone? please?

---

### Post by freakavoid on 2007-04-27
Well, i have two graphics cards on this machine; with the nvidia card and enabled restricted drivers i get that icon. With the onboard intel card i get the usual one from edgy. I am not sure but considering this it can be a glx thingy.

---

### Post by compmodder26 on 2007-04-27
As far a I know, you get that icon when you have compositing enabled in xorg.conf.  You have to make sure you have the 3D drivers for your video card first.

---

### Post by marko_4454 on 2007-04-27
Thanks to both of you.
I have Radeon X600, Beryl, using the open source radeon drivers. 
I will try and so what you said compmodder26 and see how that works...

---

### Post by kwaanens on 2007-04-27
> **freakavoid said:**
> Well, i have two graphics cards on this machine; with the nvidia card and enabled restricted drivers i get that icon. With the onboard intel card i get the usual one from edgy. I am not sure but considering this it can be a glx thingy.

I get the icon with Intel graphics. (Aiglx enabled out of box)

-K

---

### Post by locke.dragon on 2007-04-27
first, backup your xorg.conf.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

print out these instructions.  after you finish editing xorg.conf, if you have problems after restarting x (ctrl>>alt>>backspace) then do this...

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

now open up your xorg.conf

```

sudo gedit /etc/X11/xorg.conf

```

and make sure you have this...

```

Section "DRI"
Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

```

somewhere in your xorg.conf.  it doesn't have to be in this exact configuration, just make sure it's in there somewhere.  in addition to enabling the volume icon, it should boost the 3d performance of your computer.  but i'm just a noob speaking from limited experience.

---

### Post by marko_4454 on 2007-04-27
wow...thanks dragon. That worked just fine....
especially it was this line the one I was missing:

```
Option "RENDER" "Enable"
```

So that did the trick! Thanks for all your help.

---

### Post by orb9220 on 2007-04-27
And it is not COOL! I like the old orange progress much smaller and dosn't take up a big chunk of screen.

> "DOWN! Down! I say with the New Volume control.!"

AHhhh! I Feel better now.

---

### Post by Najand on 2007-04-27
I also prefer the old one. There must be a difference between Ubuntu and Mac O$ X,

---

### Post by locke.dragon on 2007-04-30
well i for one prefer the newer one.  the older one looked clunky and non-professional.  that's just my personal preference though.

---

