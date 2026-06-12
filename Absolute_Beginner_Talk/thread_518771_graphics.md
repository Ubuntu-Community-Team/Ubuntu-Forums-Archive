---
title: "graphics"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mozeruk on 2007-08-06
Im itching to have a play with the desktop effects, but everytime i try and launch them i get a message saying 

[B]Enable the driver?

NVIDIA accelerated graphics driver

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as to provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.[/B]

then i get a message saying i need a restart - but when i do, i get the same message upon my second time of trying!! Need some help here!

My GPU is listed in the restricted drivers manager as not it use, when i try and enable it, i get a repeat of the above!!


Hope someone can shed some light!

cheers, in advance!

---

### Post by family on 2007-08-06
Maybe you should try to enable your driver through the Synaptic Package Manager. I'm not positive, but it should be under Restricted -(Drivers). If not, see if you have all of the available repos under Software Sources.

---

### Post by family on 2007-08-06
[COLOR="Magenta"]ALL CREDIT TO [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)[/COLOR]
 [SIZE="4"][CENTER][B]How to install Beryl (Nvidia)

[/B][/CENTER][/SIZE]    * Read #General Notes
    * Read #How to add extra repositories
    * Read Beryl and Nvidia Drivers Installation Steps
    * Read Howto Fix Beryl Worspaces Problem in Feisty Fawn 

    * Ensure all packages up to date 

```

sudo apt-get update
sudo apt-get dist-upgrade

```
    * Back up xorg.conf 

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf

```

    * Install Nvidia Driver for Graphics Card*
          o System -> Administration -> Restricted Driver Manager 

Enable Nvidia Drivers

Restart X-Windows and confirm Nvidia Drivers are working correctly

    * Install Beryl 

```

sudo apt-get install beryl emerald-themes beryl-manager

```

    * Start Beryl 

```

beryl-manager

```

    * Start Emerald (if it doesn't start on its own) 

```

emerald --replace

```

    * Have Beryl and Emerald load on login
          o System -> Preferences -> Sessions
          o Startup Programs -> New 

```

beryl-manager

```

and

```

emerald --replace

```


    *
          o If, on reboot, program menus aren't displaying in the correct layer (you can't see them when you select them because they are displaying behind the window) then right click on the 'Beryl Manager' icon in the panel (the red gem icon) and select 'Reload Window Manager'. The problem should be solved the next time you reboot. 

    *
          o If when you start Beryl you find your windows have no title bar (with the minimise, maximise and close buttons) or borders, you may need to add the following line to the device section of the file /etc/X11/xorg.conf (See this page [http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631) for details): 

Option "AddARGBGLXVisuals" "True"

and change to

DefaultDepth 24  

in the "Screen" section.

Also if you are using a NVIDIA GeForceGo graphics card you may also need to add

Option "DisableGLXRootClipping" "True"

in the device section of your xorg.conf

If that still doesn't help you then right click on the beryl diamond icon by the clock and select advanced beryl options-rendering platform and choose "force AIGLX"

This should get everything going.

---

