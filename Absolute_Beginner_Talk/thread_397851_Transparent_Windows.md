---
title: "Transparent Windows"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dun4d on 2007-03-31
Hi,

I'm trying to get my terminal windows to be transparent. When I use the default settings the window become transparent, but only shows the background image, not any of the windows behind them. Any help?

Thanks

---

### Post by arron on 2007-03-31
Have a look at beryl. That has see threw windows and some other 3d cool stuff.  If not, i believe you only see the desktop image below.

---

### Post by Maestro23 on 2007-03-31
> **dun4d said:**
> Hi,

I'm trying to get my terminal windows to be transparent. When I use the default settings the window become transparent, but only shows the background image, not any of the windows behind them. Any help?

Thanks

What Desktop are you using? I use Gnome and had to go and change the profile in my terminal window to get it transparent.

Terminal Menu bar:  Edit>>Profile

---

### Post by x1a4 on 2007-03-31
Hi,

Are you using Xubuntu?  If so, upgrade to the latest version of Xfce, enable compositing in your _xorg.conf_ file then configure transparencies in 'Window Manager Tweaks' to get _true_ transparencies.  

**To upgrade Xfce:** 

Add these repositories to _/etc/apt/sources.list_: 

[B]deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main[/B]

You can also add them using Synaptic: 

Settings > Repositories > Third Party

Or use the Software Sources tool

Update your list of packages: 

*sudo apt-get update*

or use Synaptic by clicking the Reload button

Upgrade Xfce: 

*sudo apt-get upgrade*

Or in Synaptic

Status button > Installed (upgradable) > Mark Xfce packages to upgrade > Apply button

**Enable compositing in X:** 

Open _/etc/X11/xorg.conf_ for editing by 
opening the Run dialog (Alt+F2) and typing 

*gksu gedit /etc/X11/xorg.conf*

Add this section at the bottom of _xorg.conf_

[B]Section "Extensions"
    Option         "Composite" "Enable"
EndSection[/B]

Restart X: 

Ctrl+Alt+Backspace

Now configure your transparencies: 

Menu > Settings > Settings Manager > Window Manager Tweaks > Compositor tab



Be sure to include which Ubuntu distro you're using in your Profile.

---

### Post by girard on 2007-03-31
this is for true transparency? the same procedure goes for ubuntu? and there are no video requirements such as those required for enhanced 3d graphics in beryl?

---

### Post by dun4d on 2007-03-31
Just using GNOME, been playing with XGL and Beryl, but they have been been trouble. Just wondered if it was possible without Compiz.

---

### Post by x1a4 on 2007-03-31
> **girard said:**
> this is for true transparency? the same procedure goes for ubuntu? and there are no video requirements such as those required for enhanced 3d graphics in beryl?

Yes, that's for true transparencies but only in Xfce.  As far as I know GNOME's window manager doesn't have compositing support, Xfce's does--albeit without those fancy cubes etc.  

You might want to try and install Xfce: 

Add these repositories: 

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main

And execute: 

[I]sudo apt-get update
sudo apt-get xfce4[/I]

then kill GNOME's window manager (*gnome-wm*) and run Xfce's window manager (*xfwm4*). 

Please note that I've never done this and make no guarantee this will work, although it should.

---

### Post by jem7v on 2007-03-31
XFCE's compositor still more or less requires hardware accelleration and a few packages for composite rendering, and the only things it does are transparent windows and shadows... No wobble or cube or anything crazy like that.  On the other hand, if you don't want a zany desktop and all you want is nice, simple transparent windows, it does a reasonably good job.

To get Real transparency in the terminal without a composite manager for the rest of the desktop you might be able to find some tweaks or patches if you search Google for something like "gnome terminal real transparency."

---

### Post by brinked on 2007-12-27
sorry this may sound like a stupid question..but how could xfce work for this?  isnt xfce a virtual environment?

---

### Post by Royke on 2008-01-12
Hello, i'm new to the ubuntu forum. I had only vitsa and ubuntustudio installed. I wanted to try out the environmentsettings of xfce without messing with my stable ubuntustudio wich i use (try to use [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif) )for my musicproduction. So i just downloaded an image of xubuntu and installed it.(triple boot) After some adjustments to make the windows transparent and installed a nice dark skin i have the nicest desktop i've ever seen! Why not 'play save' and backup your homefolder and just start again (with xfce) I have to say that xfce isn't as stable as gnome (on my machine) but when jou've finally set it up...

---

