---
title: "Video Drivers"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-04-29
Tried some restricted NVidea drivers for my GForce 5200x 

No dice. They work , but they're no better than the regular linux drivers. 

How do I remove them ? And go back to the regular linux drivers. 

And how do I get better than 800 x600 resolution ? I know my card can do it, but there doesn't seem to be an easy way.

---

### Post by annda on 2007-04-29
you actually need the drivers to get a better resolution. try nvidia-settings.

if it's not in the menus, you can run it from the terminal with gksudo, or you can create a launcher (right-click on the desktop, 'create launcher') with this as the command:

gksudo nvidia-settings

make sure you save xorg.conf by clicking "save changes to X configuration file". restart X or reboot.

---

### Post by koconnor100 on 2007-04-29
> **annda said:**
> you actually need the drivers to get a better resolution. try nvidia-settings.

if it's not in the menus, you can run it from the terminal with gksudo, or you can create a launcher (right-click on the desktop, 'create launcher') with this as the command:

gksudo nvidia-settings

make sure you save xorg.conf by clicking "save changes to X configuration file". restart X or reboot.

No luck ! 

It successfully openned the utility you mentioned, and told me I'm on a GeForce 5200x with 128 meg of ram, but it stubbornly refused to admit any screen resolution other than 800x600 existed. 

Another problem. All my log on screens and utilities mention ubuntu 6.10 , not Ubuntu 7.04 ... how do I tell which version I'm on ? I distinctly remember spending hours and hours installing Feisty Fawn , but nothing here seems much different , and nothing here mentions anything about the Fawn ...

---

### Post by starcraft.man on 2007-04-29
> **koconnor100 said:**
> No luck ! 

It successfully openned the utility you mentioned, and told me I'm on a GeForce 5200x with 128 meg of ram, but it stubbornly refused to admit any screen resolution other than 800x600 existed. 

Another problem. All my log on screens and utilities mention ubuntu 6.10 , not Ubuntu 7.04 ... how do I tell which version I'm on ? I distinctly remember spending hours and hours installing Feisty Fawn , but nothing here seems much different , and nothing here mentions anything about the Fawn ...

Ummm, well i don't get your 6.10 thing... Feisty doesn't look THAT much different from 6.10, I mean most of the stuff is under the hood. Newer programs, easier to install restricted drivers, windows migration assistant and a variety of other things. But if you don't use those things its not that different.

In your case, how did you install your nvidia drivers the first time? I strongly recommend the envy script, I find its the best way to get drivers into your computer. I'd say to uninstall your version I suppose through terminal, switch back to nv and then use the [envy]("http://www.albertomilone.com/nvidia_scripts1.html") script.

---

### Post by Atmosphere on 2007-04-29
link to envy script or more info about it pls 

;)

---

### Post by starcraft.man on 2007-04-29
Heres the direct download envy [link.]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu5_all.deb") Its for feisty and edgy.

Simple to install.

1) Double click the download and install the debian.

2) Go to menu, Applications > System Tools > Envy

3) Menu will open and then just select automatically install Nvidia or ATI drivers. You can also uninstall them automatically (for when you upgrade your version or do something else that needs them removed).

4) When its all don, push yes to autoreconfigure your xorg and then yes to reboot. Thats it for drivers install.

Theres plenty of info on the splash page though, read down on this link his home page. [Link]("http://www.albertomilone.com/index.html")

You can also get more info in general from [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") 

Also look at Edgy guide for some things missing from the feisty one.

---

### Post by koconnor100 on 2007-04-29
> **starcraft.man said:**
> Ummm, well i don't get your 6.10 thing... Feisty doesn't look THAT much different from 6.10, I mean most of the stuff is under the hood. Newer programs, easier to install restricted drivers, windows migration assistant and a variety of other things. But if you don't use those things its not that different.

In your case, how did you install your nvidia drivers the first time? I strongly recommend the envy script, I find its the best way to get drivers into your computer. I'd say to uninstall your version I suppose through terminal, switch back to nv and then use the [envy]("http://www.albertomilone.com/nvidia_scripts1.html") script.

must be 7.04 , there is a restricted drivers manager that let me get rid of the proprietory drivers in one button push. 

now I'm at 640 x 480 ! yeesh !  Hope that envy script works, trying it now.

---

### Post by starcraft.man on 2007-04-29
> **koconnor100 said:**
> must be 7.04 , there is a restricted drivers manager that let me get rid of the proprietory drivers in one button push. 

now I'm at 640 x 480 ! yeesh !  Hope that envy script works, trying it now. Ya, theres no way to get the restricted management into Edgy. Do post how envy goes, it should work well without any real need for input. If it asks to install something via terminal do answer "y" of course.

---

### Post by koconnor100 on 2007-04-29
> **starcraft.man said:**
> Ya, theres no way to get the restricted management into Edgy. Do post how envy goes, it should work well without any real need for input. If it asks to install something via terminal do answer "y" of course.

oh come on ! I'm on 640 x 480 resolution ! I can't see half the screen on these utilities ! The thing runs , but I can't see the bottom half where you choose resolution , assuming there are any resoltions to choose from ... the top shows 640 x 480 and clicking on it doesn't bring any other coices !

---

### Post by koconnor100 on 2007-04-29
> **koconnor100 said:**
> oh come on ! I'm on 640 x 480 resolution ! I can't see half the screen on these utilities ! The thing runs , but I can't see the bottom half where you choose resolution , assuming there are any resoltions to choose from ... the top shows 640 x 480 and clicking on it doesn't bring any other coices !

It has now been decided to try the "burn an iso of 7.04 and install from scratch" approach.

This is because after some searching I took some bloggers advice to insert two lines into the /etc/X11/xorg.conf file, entering some default values for horizontal and vertical synch. 

Rebooted, and the graphics server no longer started. AND ... even the command line mode kept asking me to log in , refusing to accept what I know to be my password and user id , thus heading for the xorg.conf file and removing those lines is not an option. 

*sigh* good thing it's just my back up machine.

---

### Post by koconnor100 on 2007-04-30
Envy

Say's it has a text interface if your xserver wont run (or the resolution is too low)

How do you start this text interface ?

---

### Post by koconnor100 on 2007-04-30
> **koconnor100 said:**
> Envy

Say's it has a text interface if your xserver wont run (or the resolution is too low)

How do you start this text interface ?

wow..if you type "envy" into a terminal , it tells you you must run envy -t to run it in text mode. 

Of course if you do that in a terminal window , it promptly kills your xserver and you have to reboot.

---

