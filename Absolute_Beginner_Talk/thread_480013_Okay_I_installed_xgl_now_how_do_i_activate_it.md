---
title: "Okay I installed xgl now how do i activate it?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-20
I have installed xgl for the purpose of trying to get my ATI x1900xtc video card to work with Beryl and I would like to know how to activate it and/or to replace x-server and then how to restore x-server if I get the blank screen of death once I switch over.  Also, does xgl still use the xorg.conf file?  Any help will be appreciated,

Thnaks in advance,

VC

---

### Post by ts51 on 2007-06-20
Don't you just run "beryl-manager" in the terminal? 

Not sure if that's what you need but, that's all I can think of.

---

### Post by overdrank on 2007-06-20
> **videocheez said:**
> I have installed xgl for the purpose of trying to get my ATI x1900xtc video card to work with Beryl and I would like to know how to activate it and/or to replace x-server and then how to restore x-server if I get the blank screen of death once I switch over.  Also, does xgl still use the xorg.conf file?  Any help will be appreciated,

Thnaks in advance,

VC

Hi did you use a "how to" to install the xgl? If you did then you should have install the xgl session that you can choose from at the login window. You can check by restarting x with the keys ctrl,alt backspace this will restart x and when you are at the login screen in the lower left corner you will see opitions and you can choose.

---

### Post by mack1082 on 2007-06-20
I followed the guide at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29")

Here's the xgl part from the site

> 
sudo apt-get install xserver-xgl

    * Write a script so Xgl can start on its own: 

sudo gedit /usr/local/bin/startxgl.sh

    * Enter and save this script information: 

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

    * If you are missing your shutdown and restart buttons, use this instead: 

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

    * Make the script executable: 

sudo chmod a+x /usr/local/bin/startxgl.sh

    * Now, we need to put in a Xgl option in our GDM login screen: 

sudo gedit /usr/share/xsessions/xgl.desktop

    * Enter and save this script information: 

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

    * Also make this script executable: 

sudo chmod a+x /usr/share/xsessions/xgl.desktop



---

### Post by videocheez on 2007-06-21
> **mack1082 said:**
> I followed the guide at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29")

Here's the xgl part from the site

Thanks bro.  This finally worked.  I saw a guide similar to the one above that you suggested but for a noo, it didn't go into specific detail on a few of the basic steps so I most likely forgot something.  Also, it didn't mention disabling universe repositories because of the following statement:

[B]"Disable the universe repositories (these provide Beryl software that is incompatible with the fglrx driver)."
[/B]
 
I would suggest not using the following guide for anyone using an 
ATI Radeon x1900xtx video card and proprietary drivers

ProprietaryOpenGL vendor string: 
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6473 (8.37.6)

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Use the guide at the following URL:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

Also, overdrank gave me a good tip to look at the lower left corner of the login window.  I didn't see the options box because my screen resolution was screwy upon start-up and I had to slide the mouse down to off of the screen before the options box appeared.  I must have logged in five times before finding the options button.:)

[QUOTE=overdrank]Hi did you use a "how to" to install the xgl? If you did then you should have install the xgl session that you can choose from at the login window. You can check by restarting x with the keys ctrl,alt backspace this will restart x and when you are at the login screen in the lower left corner you will see opitions and you can choose.[/QUOTE]

Anyways,   Thanks for the advice guys.

VC

---

