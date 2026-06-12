---
title: "Getting Beryl to Cub"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-07-09
Hi i've installed beryl manager with 

sudo apt-get install beryl-manager

the icon appears in the upper right of the desktop.  I am able to set preferences fine, however, when I go to "Select Window Manager", there are the options of Beryl, Compiz, or Metacity.  I cannot select Beryl (it revets to metacity-gnome); when I select Compiz, it behavs just like gnome does.  How do I get the cube effect going? 


Thanks.

---

### Post by AlexenderReez on 2007-07-09
refer how to....you need to configure graphic card and install few things....search in tips section or even google....

---

### Post by forrestcupp on 2007-07-09
Also, did you actually install Beryl, too, or just the Beryl manager?  You have to install both.
```
sudo aptitude install beryl
```

---

### Post by tcpip4lyfe on 2007-07-09
What kind of graphics card do you have?

---

### Post by johntkucz on 2007-07-09
okay, forrestcup, brilliant (although obvious) suggesion.  I did 

sudo aptitude install beryl

and got this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Is it installed?

Also, Restricted Drivers Manager shows ATI accelerated graphics driver that is "in use".

I don't know other ways of getting my graphics card info.

---

### Post by johntkucz on 2007-07-09
pretty sure I have the necessary graphics support:

kooz@kooz-laptop:~$ glxinfo | grep direct
direct rendering: Yes


kooz@kooz-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by johntkucz on 2007-07-09
bloody hell; when you fix something, you break something else.  this is ridic.  I just did the howto for full beryl xgl install and am under the beryl session, and "Select Window Manager" actually stays at beryl, but the gui is still very much gnome.

---

### Post by jvc26 on 2007-07-09
Beryl isnt a gui... You mean the windows don't wobble etc? Or it is looking like Metacity? Or it is using metacity?
Il

---

### Post by forrestcupp on 2007-07-09
What kind of ATI card do you have?  Obviously, you figured out that you have to run an Xgl session to use Beryl with ATI's proprietary drivers.  I'll be honest, Xgl really stinks.  You can't run opengl apps/games very well with it.  Unless you have an X700 or newer, you'll be better off not using the proprietary drivers and using the open source ones.  With the open source drivers, you can run Beryl without Xgl (using the built in AIGLX), and it works with opengl apps too.  The cards that are X700 and newer have some opengl extensions that aren't supported in the open source drivers yet, but anything before that should work perfect.

If you can do it, run with open source and without Xgl.  It will save you a lot of headaches.

And if you want to have different window decorations, you need to install emerald
```
sudo aptitude install emerald
sudo aptitude install emerald-themes
```
Then right click the Beryl icon and choose Emerald in Select Window Decorator.  Then you can choose/edit your theme by right clicking the Beryl icon and click Emerald Theme Manager

---

### Post by Alexh830 on 2007-07-09
I am having the same problem. I have followed both the wiki for installation of beryl with ATI and AIGLX but still nothing. By the way my graphics card is ATI Technologies Inc M22 [Radeon Mobility M300].

---

### Post by MementoMori on 2007-07-09
I got Beryl to work just fine, but when I installed Emerald it doesn't show up as a choice for window decorator.

---

