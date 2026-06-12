---
title: "corrupted desktop- help"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by nanaogg on 2008-01-16
we installed a graphics driver ,recommended on the Ubuntu site, it promptly messed up the desktop and now we can,t access any of the commands/ top task bar/or bottom task bar -help as a smeary screen is not our idea of fun  please keep replies simple as we are newbies at all this:confused:

---

### Post by kpkeerthi on 2008-01-16
Can you post a link of what you followed so I can take a look ?

---

### Post by nanaogg on 2008-01-16
yes 
we went to  administation on our desktop, then restricted drivers manager, and it told us to tick the following:- 

ATI Driver 3 of 3 , we did that and applied it, it then came back with it 
would only run the screen in 800 x 600 or lower, but it worked.
Then it told us to go to Preferences and put a tick in box marked "sound and Video?" which we did and apply, it then told us to restart the computer ,which we did, and it came back with the desktop scrambled!

---

### Post by kpkeerthi on 2008-01-16
OK. So you guys installed ATi binary driver. While I cannot help you fix ATi problems (as I don't have an ATi), I can help you restore your display.

From the boot menu (GRUB), select the recovery mode and press <enter>. It should take you to command prompt. Now type
```

dpkg-reconfigure -phigh xserver-xorg

```
This should list all detected resolutions for your monitor. Choose the ones you prefer (and known to work for you monitor) using the <space> key. Press OK to go back to prompt. Now type **reboot** and boot normally (NO recovery mode this time). 

Post back what happened.

---

### Post by balaknair on 2008-01-16
1) When you get to the Desktop press Alt+F1, this will drop down the Application menu from the top panel. Right arrow will take you to --> the Places menu ---> then the System Menu. In the System menu go to Administration>Restricted Drivers Manager and disable the restricted driver. Restart X by pressing Alt+Ctrl+Backspace. This is assuming the drop down menu is readable. If the menu is also scarmbled then go to the next method.

2) If you can't use the first method then press Alt+F2---> This will bring up a small Run apllications dialog ---> Type gnome-terminal----> this will bring up the terminal----> in this type 
sudo dpkg-reconfigure xserver-xorg

Use this to set your driver to vesa and restart x by hitting Alt+Ctrl+Backspace
You should be back to the default settings.

3) If you have no working desktop or GUI at all, don't worry. Just hit Alt+Ctrl+F1
This will start a command line session. Log in with your user name and password
now type
sudo dpkg-reconfigure xserver-xorg
use the tool which starts now to set your driver to vesa, save and exit
type this now
startx

you will get a graphical desktop with default configuration

---

