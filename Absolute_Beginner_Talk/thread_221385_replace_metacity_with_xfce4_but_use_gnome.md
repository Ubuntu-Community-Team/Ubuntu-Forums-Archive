---
title: "replace metacity with xfce4 but use gnome"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2006-07-23
install xfce4-utils, xfce4-mcs-plugins, xfce4-panel, xfwm4, xfwm4-themes, libxfce4mcs-client3, libxfce4mc-manager3, libxfce4util4, libxfce4gui4-4, and xfce4-mcs-manager

run 
xfce-setting-show 
to configure xfce4 to work with gnome and keyboard shortcuts

---

### Post by rowanparker on 2006-07-23
Is this a question or a How-To.
Which ever it is you need to explain a bit more.

Rowan.

---

### Post by adam.tropics on 2006-07-23
Am I missing something here? Why not just install xubuntu-desktop and run gnome apps within xfce4 session?

---

### Post by lance bermudez on 2006-07-25
log into recover mode or what ever it is called the second linux under your kernel that has something in the () if you do not see this then you need to hit the esc key in the terminal type

apt-get remove metacity

then install xfce4-utils, xfce4-mcs-plugins, xfce4-panel, xfwm4, xfwm4-themes, libxfce4mcs-client3, libxfce4mc-manager3, libxfce4util4, libxfce4gui4-4, and xfce4-mcs-manager
with 

apt-get install xfwm4 xfwm-themes xfce4-mcs-manager

the rest  are deps on xfwm4 xfwm-themes xfce4-mcs-manager so you may or may not have to install them

to set xfwm4 as the window manager for gnome then in terminal type

sudo sed -i "s/openbox)/openbox|xfwm4)/" /usr/bin/gnome-wm

and then type

echo export WINDOW_MANAGER=/usr/bin/xfwm4 >> ~/.gnomerc

the ~/.gnomerc is a hidden file in you /home/your user name

to log back into gdm window to log int to ubuntu type exit
then change the session to gnome and save it as the default session if you wish to do that but do not have the save session automatically check in the session manager you get from system preferences session session options becuse it will screw up every thing or at least is dose for me. it make the start up slow 

then from run type
xfce-setting-show
to configure xfwm4 themes and setup the keyboard shortcuts
you get run by right clicking a panel
+ Add to panel...
click run application... to add run to panel the icon is a set of gears

or create an icon in System/Preferences menu to change the window manager themes and settings i have not tryed this but every thing i have read so far says it will work just type in terminal

sudo gedit /usr/share/applications/xfwm4-themes.desktop

then copy the text below in the file and save

[Desktop Entry] 
Encoding=UTF-8 
Name=xfwm4 themes 
Type=Application 
Exec=xfce-setting-show xfwm4 
Terminal=false 
Icon=xfwm4 
Categories=GNOME;
Application;Settings; 
OnlyShowIn=GNOME;

anything else you do not understand

---

### Post by lance bermudez on 2006-07-25
adam.tropics said, "Am I missing something here? Why not just install xubuntu-desktop and run gnome apps within xfce4 session?"

i have don that on my other computer but have kept xfwm4 on this computer becuse i can use the right click with the xfdesktop4 to quickly open and close programs and i only have gnome for the proxy settings thing, gnome-cups-printer, and the network broswering thing to. also i use the gnome desktop to keep the computers seperate. i also changed metacity for xfwm4 for faster startup and i will work with pcmanfm file manger which does tabs like firefox. nautilus dose not do tabs and i was using if for a while with xfwm. also most people that i know that use linux use ubuntu and gnome with nautilus and they may have to use my pc that is another reason why i kept gnome and use xfwm4 as the window manager. did this answer your qustion?

---

### Post by adam.tropics on 2006-07-25
Yeah, was just curious! May look into pcmanfm though.

---

### Post by lance bermudez on 2006-07-25
check out 
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=212417&highlight=pcmanfm](http://ubuntuforums.org/showthread.php?t=212417&highlight=pcmanfm)
[http://ubuntuforums.org/showthread.php?t=179677&highlight=pcmanfm](http://ubuntuforums.org/showthread.php?t=179677&highlight=pcmanfm)
for download and documention

and to just download it from synaptic add
deb [http://apt.debian.org.tw/](http://apt.debian.org.tw/) unstable main 
to your sources.list under /etc/apt/sources.list or by synaptic

or to just download the .deb
[http://lottalinuxlinks.com/files/pcmanfm-0.2.4_0.2.4-1_i386.deb](http://lottalinuxlinks.com/files/pcmanfm-0.2.4_0.2.4-1_i386.deb)

---

