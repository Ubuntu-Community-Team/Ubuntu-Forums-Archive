---
title: "Issues with Desktop Effects"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tech_cheetah on 2007-07-19
Hi friends  .. I am a newbie to ubuntu .. its a really awsome distro .. n most user friendly I have ever seen.
When I enabled the desktop effects, things seem to be working fine except for two things :
1. Windows borders are gone, and also the close,maximise and minimise icons
2. Terminal is not working : it just appears as blank white screen 
Please help me !!

---

### Post by happy-and-lost on 2007-07-19
Which graphics card, and which driver for the card are you using?

---

### Post by FunkyJack on 2007-07-19
You need to install new drivers for graphic card and it will work.
You should also install Beryl Manager

```
sudo apt-get install beryl-manager
```

I recommend you to install emerald too

```
sudo apt-get install emerald emerald-themes
```

If you install emerald then choose it under Select Window Decorator in Beryl Manager.

---

### Post by tech_cheetah on 2007-07-19
I have installed invidia drivers on my laptop of NVidia Go7400 using "Envy".
I installed emerald too but and selected it as the window decorater .. but still the same problem ..

---

### Post by FunkyJack on 2007-07-19
Download drivers from here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

You will have to shut down xserver in order to install drivers.

---

### Post by tech_cheetah on 2007-07-19
I dont think there is any issue with nvidia drivers as the i am able to see the "nvidia settings"  under applicatons - > System tools
Probably there is some setting or something i am missing, because as i mentioned i am able to see all the window and 3D effects .. just i am not able to get close,minimise,maximise buttons (infact the whole title bar is missing)

---

### Post by tech_cheetah on 2007-07-19
and one more thing .. how can one apply the themes inside emerald theme manager .. there is no apply button ??

---

### Post by doutdes on 2007-07-19
I got exactly the same error, I installed the driver from nvidia; it installed ok, now I can enable the Desktop Effects, and I get the cube and the moving windows.
But no menu bar for the window so I have no minimize maximize nor close buttons for any window what so ever.

And yes It is the latest driver, I downloaded it yesterday from nvidias page.

I am running Ubuntu 7.04 for a 64 AMD.
the graphics card is a Geforce Go 6150 from a Pavillion dv2000z

---

### Post by AlexenderReez on 2007-07-19
i suggest you to use nvidia driver from repo rather than take it from its website because what is provided in repo is compiled to works with current kernel...

---

### Post by FunkyJack on 2007-07-19
I installed driver form nvidia website and it fixed me that same bug.

Did you stop xserver before installation?

---

### Post by FunkyJack on 2007-07-19
Try this:

Open xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

And in the "Screen" section add this line before EndSection:

```
Option "DisableGLXRootClipping" "True"
```

Then restart xserver (CTRL+ALT+BACKSPACE)

You apply themes in emerald just by clicking on them :)

---

### Post by tech_cheetah on 2007-07-19
I uninstalled the latest nvidia drivers v 100.14.11 and then installed the ones shown in add remove , but then got the message "Desktop Effects cannot be started"
Then I installed the old Nvidia drivers v 9639 (using envy) but the same problem still persists
Also the emerald themes aren;t working and the option is already there in xorg.conf file :confused:

---

### Post by FunkyJack on 2007-07-19
Try to install nvidia drivers v 100.14.11 again.
You have to stop xserver first and install it in console.

For emerald right click on Beryl Settings icon and check that under Select Window Decorator Emerald is selected.
But first install drivers.

---

### Post by tech_cheetah on 2007-07-19
finally things are working !! :)
All you have to do is edit /etc/X11/xorg.conf and set the default depth to 24 (initially it was 16)
now both compriz and emerald are working like charm

---

### Post by tech_cheetah on 2007-07-19
one more query :
I installed KDE over gnome using
sudo apt-get install kubuntu-desktop

I want to uninstall KDE now , but the remove is not workin in the above command. It says "Package kubuntu-desktop is not installed, so not removed"

Anybody has any clue ??
I

---

### Post by FunkyJack on 2007-07-19
Frst run
```
sudo dpkg -l
```
and see if kubuntu-desktop is on the list.

If it is then remove(purge) it:

```
sudo dpkg -P kubuntu-desktop
```

It is in the guide for installing beryl and compiz that you have to change default depth to 24 :)

---

