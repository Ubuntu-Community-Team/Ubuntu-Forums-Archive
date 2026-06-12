---
title: "Beryl Help"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by way2cool on 2007-06-17
I've been trying to install Beryl for a couple days now, I've gone though shutting down the Xserver and more, but I seem to be stuck here. O btw I have an ATI graphics card and direct rendering is enabled.

This is where the error occurs when I run the test for beryl.

```
Checking for non power of two texture support: Failed 
Support for non power of two texture missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screens: 0
beryl: no manageable screens found on display: 0.0
```

Thanks in advance for any help.

---

### Post by Majorix on 2007-06-17
It is really hard to install beryl on ati graphics cards. I am not sure if this error relates to it, but it most likely does.

You will have to wait a little while, probably they will come with a version that strongly supports ATI cards.

---

### Post by quinnten83 on 2007-06-17
[http://ubuntuforums.org/showthread.php?t=476572]("http://ubuntuforums.org/showthread.php?t=476572")
this won't help?

---

### Post by skymera on 2007-06-17
**i hope this helps! its directly from [www.ubuntuguide.org](www.ubuntuguide.org)!**

How to install Beryl (ATI)

    * Read: #General Notes 

Please note: There are 2 ways of installing Beryl for ATI Cards: The open source way and the closed source way. The Open source way is listed first, it should be the first way that you test to see if you can get Beryl working, however undo steps are provided in case it does not work, or you would like to use the closed source drivers that may have frame rate improvements and support your card better.

Open Source Method: (As of 01/05/07 this has been confirmed and tested on a 64 bit system as well) - I found this worked better for me (especially on older ATI cards). I would suggest trying this first as it is very simple and no damage should be caused to your system. It is also very easy to revert if it does not work (without a fresh install).

This assumes that you are not going to use the proprietary drivers and that the (Open Source) radeon drives are working ok for you. It will also use AIGLX. If direct rendering is not working for you yet this will software render (slowly) until you can get that up and running.

Step 1 : Edit your sources.list file adding
```

deb http://ubuntu.beryl-project.org feisty main 
```

to the bottom of it.

Step 2 : Add the GPG key. Open terminal and type
```

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add - 
```

Step 3 :

```
sudo apt-get update
```

Step 4 :

```
]cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
sudo gedit /etc/X11/xorg.conf 
```

(Note any changes so you can revert back if needed).

Under Section "Module", make sure that the following lines are included, and add them if they are not:

```
Load "dri"
Load "vbe"
Load "glx"
```

Also ensure the bottom of the file has:
```

Section "DRI"
 Mode 0666
EndSection
```

Step 5 : Reboot the system (Please don't restart only X. I had odd things happen to me when I skipped rebooting until my next proper restart).

Step 6 : In a terminal:

```
sudo apt-get install beryl
```

Step 7 : type into terminal

```
beryl-manager --no-force-window-manager
```

(this will start beryl but wont activate it yet).

Step 8 : Right click on the diamond near the clock - select advanced beryl options and change the window manager to metacity(GNOME) also change rendering path to copy. Also under advanced change rendering platform to force AIGLX.

Step 9 : Right click the diamond again. This time - select window manager - Beryl.

If it all works and you can spin the cube ok etc. you can try changing the rendering path back to automatic. If it all freaks out just reboot and start beryl again with:

```
beryl-manager --no-force-window-manager
```

Step 10 : Assuming it all worked ok you need beryl to start automatically on boot : Click System-Preferences-sessions. Click add and type
```

beryl-manager
```

Now reboot - beryl should all be sweet.

If you have broken everything - Help! Everytings broken!! Section:

!!!!!!!VERSION 2!!!!!!

Ok so you did all this and it didn't work for you and your GUI is now broken etc. Revert all changes by following these steps.

Step undo 1 : Drop to console outside GUI. and type
```

rm ~/.config/autostart/beryl-manager.desktop
```

This removes beryl from startup.

```
copy -p /etc/X11/xorgold.conf /etc/X11/xorg.conf
```

This will copy your old xorg settings back

Reboot - your GUI is now working. (Unless you followed some other steps not listed here...)

Step undo 2 : sudo nautilus from terminal. Then show hidden files. Browse to you users home directory and delete the .beryl and .emerald folder. Also delete the .beryl-managerrc file. Alternatively do this from via command line but your GUI should be working now. The command line listing would be:

```
rm -r ~/.beryl
rm -r ~/.emerald
rm ~/.beryl-managerrc
```

Step undo 3 :

```
sudo apt-get remove beryl beryl-manager emerald-themes
sudo apt-get autoremove
```

Step undo 4 : Edit your sources.list file again and remove the added source for beryl.

That's it. Your system is back as it was before you started. All the undo steps can be done without a GUI from the console

Good luck - I can vouch this method works for me on at least 2 different notebooks and a PC.


Alternate method: Using closed source FGLRX drivers from ATI.

    * Reference:ubuntuforums.org 

"All credit is due to the forum user in the reference link above. This is been added to this wiki so that other users will not (hopefully) have to search for a solution. This has been tested on the i386 version of Feisty Fawn. Someone, please modify this if the AMD64 version is also compatible."


    * Open a terminal: 

Applications > Accessories > Terminal

    * Verify our system is up-to-date: 

```
sudo apt-get update
sudo apt-get upgrade
```

    * Install Xgl (This is the main problem with ATI cards. The fglrx driver will not support the built-in Compiz feature in Ubuntu and we need Xgl to run our new version of Beryl with an ATI card.): 

```
sudo apt-get install xserver-xgl
```

    * Write a script so Xgl can start on its own: 

```
sudo gedit /usr/local/bin/startxgl.sh
```

    * Enter and save this script information: 

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

    * If you are missing your shutdown and restart buttons, use this instead: 

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

    * Make the script executable: 

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

    * Now, we need to put in a Xgl option in our GDM login screen: 

```
sudo gedit /usr/share/xsessions/xgl.desktop

```
    * Enter and save this script information: 

```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

    * Also make this script executable: 
```

sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

    * Disable the universe repositories (these provide Beryl software that is incompatible with the fglrx driver). 

Go to System > Administration > Software Sources 
Uncheck Community-maintained Open Source software (universe)
Click Close

Back in our terminal:

    * Add the correct repository key: 
```

sudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

    * Add the correct repository to the top of your apt source list: 

```
sudo gedit /etc/apt/sources.list
Enter: deb http://ubuntu.beryl-project.org/ feisty main
Save and close gedit
```

    * Update your apt sources: 

```
sudo apt-get update
```

    * Install Beryl: 

```
sudo apt-get install beryl
```

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

Download beryl-core deb from ```
http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb
```
Unpack beryl-xgl from archive to ie.```
 ~/Desktop
```
From terminal run:```
 sudo cp ~/Desktop/beryl-xgl /usr/bin/beryl-xgl
```


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

### Post by way2cool on 2007-06-17
Well, Beryl IS working it's just when it goes into the cube it's all white sides exept the top and bottom, which are the diamonds.

---

### Post by skymera on 2007-06-17
i tured my caps off!
i noticed a trememndous increase in performance with out cube caps!

---

### Post by way2cool on 2007-06-19
Well now, I'm started up in an Xgl session and i'm getting all black screens now instead of white screens. Any suggestions?
Edit i'll post a picture. 

[IMG]http://img359.imageshack.us/img359/17/screenshotoi7.png[/IMG]

---

