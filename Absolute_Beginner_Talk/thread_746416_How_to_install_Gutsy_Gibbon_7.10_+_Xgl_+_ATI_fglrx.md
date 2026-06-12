---
title: "How to install Gutsy Gibbon 7.10 + Xgl + ATI fglrx + Compiz Fusion"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-04-05
Hi all :),
           I wanted to install fancy graphics effects by following the following tutorial:

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

I have a qustions(s).

First: do i have to install my graphics card for this to work? I just finished installing a fresh copy of ubuntu 7.10 and i havent done anything to install my graphics card (which BTW is RADEON 9550 256MB - if thats important).

Second  of all - how do i **Enable fgrlx driver**? 

Thanks :D

Regards

Q

---

### Post by bumanie on 2008-04-05
The ubuntu drivers may work if you install through restricted drivers. Try here for help
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz) This also is a good site [http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by quddusaliquddus on 2008-04-05
i dont know if im allowed to do this but here it goes - bump.

---

### Post by quddusaliquddus on 2008-04-05
thanks for the advice. I went to your first link and there is options to choose linux - but no ubuntu :(

---

### Post by billgoldberg on 2008-04-05
Go to system -> administration -> restricted drivers managment.

Install your driver.

If it doesn't show up, use envy (google for envy+ubunu).

The first steps seems to tell you how to enable fglrx

---

### Post by bumanie on 2008-04-05
Linux is a generic name for a lot of operating systems that use the same basic kernel. The different operating systems are called distributions - of which there are many. Ubuntu is but one of the many distributions. Ubuntu is linux. If using 32 bit gutsy, choose the x86, however I would suggest you install via restricted drivers manager. Only use ATI's or envy if the ubuntu driver doesn't work. System --> Administration --> Restricted drivers Click the enable box. The drivere should download automatically. Then you can follow the rest of the guide.

---

### Post by quddusaliquddus on 2008-04-05
thanks for the help guys. I've used thye rescticted drivers managament program and installed a driver using it.

Then ive followed the steps here:

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

and I've restaretd the pc. Now ubuntu has slowed down and whenever i open up a new application then an outline of a square enlarges to fill the screen then the application appears. it takes time to open any application. Also - the panel button used to show the desktop has fuzz for an icon. i enabled the desktop cube in  compizconfig settings manager aka  advanced desktop effects settings ut there are no cubes.

Where did i go wrong? :(

---

### Post by quddusaliquddus on 2008-04-05
also - its extremely slow going when i scroll up or down in firefox.

---

### Post by billgoldberg on 2008-04-05
To enable the cube, open the advanced desktop effects settings.

Go to general options, and in one of the tabs you should set the "horizontal size" to 4.

About it being slow, disable some effects.

note:

Compiz fusion was slow as hell when I used the drivers from envy, but the drivers in the restricted drivers were fast. 

So it could be that also.

---

### Post by quddusaliquddus on 2008-04-05
ive done the horizotal size - but the desktop cube doesnt show up. iv also gotten rid of 
 most of the effects but things still seem to be slow.

---

### Post by quddusaliquddus on 2008-04-05
thanks for all the help guys. I have to admit that one of the main reasons why i installed ubuntu was because of the lure of the graphical effects it was possible to have with it. I am pretty desperate to get this working. Has anyone got any solutions to my problems? please help me!

---

### Post by bumanie on 2008-04-05
Ati cards don't work as well with ubuntu as nvidia cards. I have an nvidia, so know little about troubleshooting ati problems. usually the resticted works, normally users have trouble with ati drivers and sometimes envy. Hope someone who is ati savvy comes along quickly to help you through the problems.

---

### Post by quddusaliquddus on 2008-04-05
Thank you for your sympathies. I also hope someone comes along who can fix this as well.

---

### Post by joshrobinson on 2008-04-05
in firefox you want to make sure "smooth scrolling" is off
edit > preferences > advanced in firefox

did you install ccsm?

```
sudo apt-get install compizconfig-settings-manager
```
```
ccsm
```

enable desktop cube and rotate cube
also make sure in the bottom right of your screen you have 4workspaces next to your trashcan
if not right click the workspaces and turn it up to 4 columns

also run this command, and post its output
```
fglrxinfo
```

---

### Post by quddusaliquddus on 2008-04-05
ive done everything you've said...but when i enter **fglrxinfo** into the terminal ubuntu restarts

---

### Post by joshrobinson on 2008-04-05
did the cube work though?

ctrl+alt+left or right arrow

how about
```
glxinfo
```

does it say direct rendering: yes

---

### Post by quddusaliquddus on 2008-04-05
the cube doesnt work.  and glxinfo says no to direct rendering.

---

### Post by joshrobinson on 2008-04-05
sounds like your drivers arent installed correctly

open system > administration > restricted drivers manager
uncheck your ati driver, recheck it and reboot

try glxinfo again

---

### Post by quddusaliquddus on 2008-04-05
i did as you said. it still says no and the cube isnt working either. There Must be a solution to this problem...please someone...help!

---

### Post by ElTimo on 2008-04-05
I'm not sure if this will help, but you could try going in ccsm to General->Display Settings and untick Detect Refresh Rate, then change the Refresh Rate slider to 200. Also, if "sync to vblank" is ticked, untick it. Don't worry, changing the refresh rate won't break your computer.

About the cube, are you sure you have the "Rotate Cube" plugin enabled? you can't turn the cube without it.

---

### Post by quddusaliquddus on 2008-04-05
yeah...i have the rotate cube plugin enabled - cube not working though. Also - i did what you said but things are still slow....

---

### Post by quddusaliquddus on 2008-04-05
i guess its hopeless :(

---

### Post by quddusaliquddus on 2008-04-06
at last! I dont know how but the desktop cube is working now. There are some snags though.

1. The titlebar is mising in every window i open.

2. I cant see the top and bottom of the cube and  i dont know how to make my cube transparent so that i can see other desktop behind the selected desktop.

Any ideas?

---

