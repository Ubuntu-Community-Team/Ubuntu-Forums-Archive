---
title: "[SOLVED] How to use Compiz-Fusion in Ubuntu? Need guidance"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by onlytanmoy on 2007-11-26
Dear All, I have installed Ubuntu Gutsy Gibbon 7.10.
Is there any site which shows which key combinations to use to get the effects out of
compiz fusion? or how to configure it? say wen i close a window, flames show up etc..like the one shown below

```
http://www.youtube.com/watch?v=l_ssPEzybjs&feature=related
```


i need a step by step tutorial guys as i am an absolute newbie in Linux.
Thanks in advance.

---

### Post by conjur3r on 2007-11-26
Install a package called **compizconfig-settings-manager** from System > Administration > Synaptic.  This provides a nice gui to customize anything related to compiz fusion (eg effects, shortcut keys, etc).

---

### Post by overdrank on 2007-11-26
> **onlytanmoy said:**
> Dear All, I have installed Ubuntu Gutsy Gibbon 7.10.
Is there any site which shows which key combinations to use to get the effects out of
compiz fusion? or how to configure it? say wen i close a window, flames show up etc..like the one shown below

```
http://www.youtube.com/watch?v=l_ssPEzybjs&feature=related
```


i need a step by step tutorial guys as i am an absolute newbie in Linux.
Thanks in advance.

Hi, have you install CCSM? If not you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. The fire effect will be located under effects, animations. then you can set the fire for closing of apps or minimize.

---

### Post by Ub1476 on 2007-11-26
First make sure you can run Compiz-Fusion. Open System>Preferences>Appearance>Visual Effects and check normal/extra whatsoever. 

If that works alright, open add/remove, search for compiz and install "Advanced Desktop Effects Settings". To enable this, go to Visual Effects again and select custom. Now you can play with different plugins and such. 

To do so, open System>Preferences>Advanced Desktop Effects. If you want the to burn up the window when you close it, go to Effects>Animations>Close (doesn't matter what you choose)>Edit the settings to use Fire animation.

For other plugins like the famous Cube, enable it, click on the plugin>actions>see what key to press to use it. 


Hope that helped a bit.

---

### Post by onlytanmoy on 2007-11-26
u guys rock..thanks a lottt for such quick replies..i will try out wat all u suggested n then update this thread..thanks again.

---

### Post by Ub1476 on 2007-11-26
We suggested the same, just said it in different ways:p

---

### Post by onlytanmoy on 2007-11-29
thanks a lott guys....am now using compiz-fusion in its full glory.
aero in vista doesn't hold a candle before compiz-fusion in ubuntu :)

---

### Post by mo2pow on 2008-01-09
> **conjur3r said:**
> Install a package called **compizconfig-settings-manager** from System > Administration > Synaptic.  This provides a nice gui to customize anything related to compiz fusion (eg effects, shortcut keys, etc).

hello noob!
i want to play with 3d effects and desktop but i can't seem to find the compizconfig-settings-manager...i have the 7.10 ubuntu and did all updates..no luck on googling too...where can i find the file ?

---

### Post by shareMenaPeace on 2008-01-09
Hi, 
open ADMINISTRATION - > SYNAPTIC PACKAGE MANAGER and search there for "compizconfig", than choose to install compizconfig-settings-manager, 
OOps that was waht you did, ok if you cannot find it than go to

ADMINISTRATION or PREFERENCES -> SOFTWARE SOURCES and enable here in tab 1 and 2 everything (repos) except source code.

ps.
If you overdo with the settings you can reset from the general tabs, and i suggest create profiles.


Have Fun 


:popcorn:

---

### Post by pengko.eo on 2008-05-17
hello there people. i have installed advanced desktop effects settings on my ubuntu, but i dont know how to make the 3d cube effect work. i cant find the shortcuts to make that happen. and the other thing is how can i show all of my working windows on just one windows? is it done by enabling the desktop plane? how can i get that working? i cant find the shortcuts or where can i set the shortcuts. please help me, thanks

---

### Post by pengko.eo on 2008-05-17
hello there people. i have installed advanced desktop effects settings on my ubuntu, but i dont know how to make the 3d cube effect work. i cant find the shortcuts to make that happen. and the other thing is how can i show all of my working windows on just one windows? is it done by enabling the desktop plane? how can i get that working? i cant find the shortcuts or where can i set the shortcuts. please help me, thanks

---

### Post by overdrank on 2008-05-17
> **pengko.eo said:**
> hello there people. i have installed advanced desktop effects settings on my ubuntu, but i dont know how to make the 3d cube effect work. i cant find the shortcuts to make that happen. and the other thing is how can i show all of my working windows on just one windows? is it done by enabling the desktop plane? how can i get that working? i cant find the shortcuts or where can i set the shortcuts. please help me, thanks

HI and you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked. Also make sure that the desktop cube is checked also. It seems you are speaking of the scale plugin. The cube is use but the ctrl, alt, single click mouse and you can find the other short cuts under the bindings of the plugin.

---

### Post by pengko.eo on 2008-05-17
thanks man this help me out a lot. one more thing, how can i show all my active windows all together on just a window / my desktop? just like the one on mac. i noticed this is possible on ubuntu with compiz fusion (thats what i saw on youtube). is it by using the desktop plane? i enabled it but i dont know how to use it, the bindings said press ctrl alt down, but nothing happen when i pressed those buttons. please help me out. thanks.

---

