---
title: "problems upgrading from feisty to gutsy."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Heffa on 2007-11-07
Hi i've got some problems since i upgraded to gutsy gibbon. 

first thing i noticed was the screen resolution, i had 1400x900 on feisty now im stuck on 1024x768. When i used feisty fawn i also had some problems with the resolution but that was fixed using resolution switcher. that does'nt work now.

I've tried using  sudo dpkg-reconfigure xserver-xorg, fund the resolution i wanted, but nothing changed afterwards. then i tried going into the system settings, monitor and display to see if i could change something there, but to my surprise all the text was in chinese(!). which brings me to my second problem. 

how do i change the chinese text in the monitor and display back to either norwegian or english, or even any language using the latin alphabet would be an improvement.

my computer is a dell inspiron 640m 
screen: Wide Screen 14,1" WXGA+ (1440x900) Ultrasharp TFT
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

please help me,

---

### Post by Nikitas350 on 2007-11-07
try to configure your screen with "screen and graphics" tool. Select 1440x900 widescreen for your monitor and it will play... (i think ;))

---

### Post by skyjacker on 2007-11-07
Downoad & install the restricted drivers. If that doesn't work:

Try this Procedure:

1) Back up the present xorg.conf
Code :sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

2) Stop gdm or kdm
Code: sudo /etc/init.d/gdm stop (or kdm for kde)

3) Edit xorg.conf
Code: sudo dpkg-reconfigure xserver-xorg

4) Select the resolutions you want available by arrowing down to each desired line and pressing the “space bar”

5) Validate your choices with “enter”

6) restart X with Control+Alt+Backspace

7) Choose the desired resolution under the “Systems/Preferences/Screen Resolutions drop down list

NOTE: if you don't need to add any additional resolution sizes, skip # 4 & 5

---

### Post by Heffa on 2007-11-08
managed to fix it with reconfigure xserver.

tjanks for the help.

---

