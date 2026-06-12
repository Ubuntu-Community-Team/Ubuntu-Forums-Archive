---
title: "What does Failed to start the x server mean???"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by chitalian on 2007-04-08
im using a radeon 9250 on my hp pavilion 7955 computer. 1.5ghz.

i installed feisty and am trying to make my video card work. after i restart my computer it tells me at a blue screen that Failed to start the X server (your graphical interface). and it tells me to refer to [http://wiki.x.org](http://wiki.x.org) before reporting problems.  Can anyone tell me how to properly install my card and anything else relating to it, like the 3d accelerator or xerver-xgl.  I am very new to ubuntu and am trying to get this to work to install beryl.  thank you for your help.

---

### Post by Happy_Man on 2007-04-08
Hoo boy, ATI cards. Not to worry, you can get it to work, but it will be thorn in your side for a long time, most likely. FIrst off, after the blue screen drops you at the terminal (where it asks you to login), go ahead and log in. Then, enter 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and remember to choose ATI (i think) when it asks you for your kind of graphics card. Once you get your desktop back, post back with what exactly you did to screw up your X server.

---

### Post by chitalian on 2007-04-08
thanks, well i wrote in that command but nothing relating to me selecting ati was ther.. in all, i decided to just start fresh so i deleted everything and i just finished installing ubuntu, and am updating right now.. if you could.. could you show me how to go through the steps on setting up the vid card and then installing beryl , the way you did it.. that would be great thanks for the time and help

---

### Post by Happy_Man on 2007-04-08
Hmm... how about just plain 
```

sudo dpkg-reconfigure xserver-xorg

```

I have a Nvidia card, so I have no idea what hoops to jump through to get Beryl to work. Still, see if this site helps you:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

---

### Post by igknighted on 2007-04-08
With an old card like that you might be better off using the "radeon" driver... it is open source and included already.  Read this thread for more info on how to set it up:

[http://ubuntuforums.org/showthread.php?t=290841](http://ubuntuforums.org/showthread.php?t=290841)

---

