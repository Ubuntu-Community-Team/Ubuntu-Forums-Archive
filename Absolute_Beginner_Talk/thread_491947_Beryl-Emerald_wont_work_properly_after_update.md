---
title: "Beryl-Emerald wont work properly after update"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by erusfatum on 2007-07-04
hello people! once more things get messed  up :(
After the update of nvidia-xgl and 2 more nvidia components i cant rememer now (must be drivers or smt) xserver crashed, and wont boot me into the gui saying that xserver isnt configured and it wont start gdm until i configure bla bla bla... so i did sudo dpkg-reconfigure xsercer-xorg, configured it and reboted, then when i booted, beryl wouldnt work, and the windows had no borders, so i thought if i install the old drivers i had it will solve it, so i did. but the problem is the same, beryl works but there are no borders if i select beryl as the window manager... i tried ti reinstall beryl and emerald but no use... any suggestions?

---

### Post by erusfatum on 2007-07-04
any one? :(

---

### Post by CaptainInsaneO on 2007-07-04
I just installed a new 8800 gts and am having the same problem. For functionality for now, right click your Beryl manager icon and go "Select Window Manager"-->"Metacity".

I'm working on this right now, when I find a solution I'll post again.

---

### Post by bren on 2007-07-04
i made a script to do install of beryl.... for me it works....

the bit about stopping the update for beryl to the latest version (which breaks it)  is file /etc/apt/preferences

hope it works for you

the other files are necessary config files for the script - you can change as you need

for the oriiginal thread where i copied the commands search for "ati x200m beryl"

bren

---

### Post by bren on 2007-07-04
for some reason preferences file will not load as attachment 
here is code

```
]# /etc/apt/preferences
Package: beryl
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-manager
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-core
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-plugins
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-plugins-data
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-settings
Pin: release a=stable
Pin-Priority: 1001

Package: beryl-settings-bindings
Pin: release a=stable
Pin-Priority: 1001

Package: emerald
Pin: release a=stable
Pin-Priority: 1001

Package: emerald-themes
Pin: release a=stable
Pin-Priority: 1001

Package: libberyldecoration0
Pin: release a=stable
Pin-Priority: 1001

Package: libberylsettings0
Pin: release a=stable
Pin-Priority: 1001

Package: libemeraldengine0
Pin: release a=stable
Pin-Priority: 1001

Package: emerald
Pin: release a=stable
Pin-Priority: 1001
```

---

### Post by CaptainInsaneO on 2007-07-04
I don't think he really needs to re-install beryl, this is more of a xorg.conf issue.


erusfatum, I found a solution to your/our issue. Right now my beryl window manager is working perfectly except for now it is killing off my gDesklets, but I digress.

Make sure you have OpenGL enabled:
```
glxinfo | grep "direct rendering"
```
It SHOULD be enabled if you installed the correct drivers, which you obviously have because you can get X to start. If, by chance, it isn't, enable it.

In terminal, type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
to make a backup of your xorg file.

Then, open your xorg file for editing with gedit.
```
sudo gedit /etc/X11/xorg.conf
```

In section "Module", put
```
Load       "dbe"
```
in the topmost position.

Add
```
Option   "XAANoOffscreenPixmaps" "true"
Option   "AllowGLXWithComposite"   "true"
Option   "TripleBuffer"   "true"

```
to the "Devices" section.

Add this to the bottom of the file:
```
Section "Extensions"
       Option       "Composite" "Enable"
EndSection
```

And the "Screen" section MUST have this:
```
Option   "AddARGBGLXVisuals"   "true"
DefaultDepth   24
```



Save and reboot, everything should be fixed. If it isn't, post your xorg.conf file here for more help. :D

P.S. If you want to prevent the Nvidia splash screen from displaying and potentially slowing your boot time, add the following line to your "Device" section as well:
```
Option   "NoLogo" "true"
```

---

### Post by erusfatum on 2007-07-04
awesome man! thanks! i owe you this one! :popcorn: worked just fine, 
thanks guys both of you!

---

### Post by CaptainInsaneO on 2007-07-04
Always glad to help. :cool:

---

### Post by erusfatum on 2007-07-05
but could you please explain what i did there? :D

---

### Post by CaptainInsaneO on 2007-07-05
Nope. :p

But [this]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html") might help you understand a little better.

---

### Post by erusfatum on 2007-07-05
lol
thanks any way :D

---

### Post by xtemplarx on 2007-07-05
> **CaptainInsaneO said:**
> I don't think he really needs to re-install beryl, this is more of a xorg.conf issue.


erusfatum, I found a solution to your/our issue. Right now my beryl window manager is working perfectly except for now it is killing off my gDesklets, but I digress.

Make sure you have OpenGL enabled:
```
glxinfo | grep "direct rendering"
```
It SHOULD be enabled if you installed the correct drivers, which you obviously have because you can get X to start. If, by chance, it isn't, enable it.

In terminal, type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
to make a backup of your xorg file.

Then, open your xorg file for editing with gedit.
```
sudo gedit /etc/X11/xorg.conf
```

In section "Module", put
```
Load       "dbe"
```
in the topmost position.

Add
```
Option   "XAANoOffscreenPixmaps" "true"
Option   "AllowGLXWithComposite"   "true"
Option   "TripleBuffer"   "true"

```
to the "Devices" section.

Add this to the bottom of the file:
```
Section "Extensions"
       Option       "Composite" "Enable"
EndSection
```

And the "Screen" section MUST have this:
```
Option   "AddARGBGLXVisuals"   "true"
DefaultDepth   24
```



Save and reboot, everything should be fixed. If it isn't, post your xorg.conf file here for more help. :D

P.S. If you want to prevent the Nvidia splash screen from displaying and potentially slowing your boot time, add the following line to your "Device" section as well:
```
Option   "NoLogo" "true"
```

Should this also be working for those of us with ATI setups who's beryl broke as a result of updating?  I've gone back (I think) to the older version of beryl, and even placed my old xorg.conf back in place, but I'm still broken.  Guess I can wipe it all out and start over from scratch again... :(

---

### Post by Raineer on 2007-07-05
Not sure about the module line, but yeah for ATI the composite setting and the 3 options should be required as well.

---

### Post by xtemplarx on 2007-07-05
I ended up doing a few things to get mine back up and running:

1)  I had to reset all of my repositories (and apt prefs) per the instructions on the beryl-project.org site.
2)  Uninstalled (Complete Removal) all Beryl and Emerald-related apps.
3)  Reinstalled them all (0.2.0) per the beryl-project.org instructions

I'm back up and wobbling.

Here's the page I'm referring to:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by CaptainInsaneO on 2007-07-05
I'm just telling him what worked for me. Thankfully, it worked for him also.

Everyone's machines, configurations, auras, etc. are different. :popcorn:

---

