---
title: "Beryl not working! Composite not found!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-15
After reinstalling Ubuntu after a dad thought he knew what he was doing :roll: and formatted my hard drives, Beryl is not working! I can launch beryl-manager, but when I select Beryl as a window manager, window borders / title bars disappear for about a second and it defaults to Metacity again. Also, I get this error when I type 'sudo beryl':

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

Any ways around this? Ty in advance everyone!

---

### Post by lamalex on 2007-06-15
use sudo beryl-xgl

---

### Post by eoghanmurray on 2007-06-15
Returned:
```
sudo: beryl-xgl: command not found

```

---

### Post by zeeR on 2007-06-15
What is your graphic card? And what guide did you follow to install Beryl (if any)?

---

### Post by eoghanmurray on 2007-06-15
Beryl works fine on my monster machine (not this one), which has nvidia 8800, but this one doesn't seem to want to work.

ATi x600.

I followed this one: 

>     * Open a terminal: 

Applications > Accessories > Terminal

    * Verify our system is up-to-date: 

sudo apt-get update
sudo apt-get upgrade

    * Install Xgl (This is the main problem with ATI cards. The fglrx driver will not support the built-in Compiz feature in Ubuntu and we need Xgl to run our new version of Beryl with an ATI card.): 

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

    * Disable the universe repositories (these provide Beryl software that is incompatible with the fglrx driver). 

Go to System > Administration > Software Sources 
Uncheck Community-maintained Open Source software (universe)
Click Close

Back in our terminal:

    * Add the correct repository key: 

sudo wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

    * Add the correct repository to the top of your apt source list: 

sudo gedit /etc/apt/sources.list
Enter: deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
Save and close gedit

    * Update your apt sources: 

sudo apt-get update

    * Install Beryl: 

sudo apt-get install beryl

Apt should retrieve all of the dependencies such as plug-ins and libraries

    * Install your ATI drivers (if needed): 

Go to System > Administration > Restricted Drivers Manager
Check the Enable check box for your ATI graphics card

You will need to reboot to enable the card.

    * After a reboot and choosing Xgl from your sessions list at your login screen, test Beryl. In a terminal: 

beryl-manager
emerald --replace

You should see the Beryl diamond next to your clock, and you should try moving a window. You may need to right-click on the diamond, select "Beryl" from the "Select Window Manager" flyout, and select "Standard Beryl Decorator (Emerald)" from the "Select Window Decorator" flyout. You may also need to click Reload for each one of these under the same menu.

    * If you are using ATI with XGL, you'll get an error that beryl-xgl is missing. Solution is not elegant, but it's working: 

Download beryl-core deb from [http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb](http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb)
Unpack beryl-xgl from archive to ie. ~/Desktop
From terminal run: sudo cp ~/Desktop/beryl-xgl /usr/bin/beryl-xgl


    * If everything seems to work OK, add Beryl and the Emerald themes to your start-up programs: 

Go to System > Preferences > Sessions
Click the New button
Type "Beryl" (no quotes) for the Name text box
Type "beryl-manager" (no quotes) for the Command text box
Click the OK button

Click the New button
Type "Emerald Themes" (no quotes) for the Name text box
Type "emerald --replace" (no quotes) for the Command text box
Click the OK button

Congratulations! Hopefully, you have Beryl working now. You can now re-enable your universe repositories, but make sure you do not let it update anything related to Beryl. Hopefully, the Beryl apps in the universe repositories will soon work with the ATI cards without Xgl. 

---

