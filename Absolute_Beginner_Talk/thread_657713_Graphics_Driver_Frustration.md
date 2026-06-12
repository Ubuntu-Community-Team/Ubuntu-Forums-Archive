---
title: "Graphics Driver Frustration"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by boardfoot on 2008-01-03
Complete noob here. Attempting to dump MS for Ubuntu.

All has been well except for a really annoying anomolie:

My graphics drivers are cooked or something. 

Trying to install the nvidia restricted drivers but I get white screen at login everytime I attempt to use them.

Read some threads in here and managed to sudo dpkg-blah blah blah in safe mode back into vesa so I can see the GUI. Change the drivers... login cooked again with white screen. Then I *THINK* I got things figured and swing 1280x1024 with NV driver (still no 3d accel)... until I reboot... now I got 640x480 forced down my throat and an xorg.conf file that looks like MS Frontpage HTML source... what a mess (compared to the xorg.conf files I've seen posted).

So... mr smartypants thinks he'll just edit the xorg.conf file in gedit to match posted ones.... WRONG... permission error on the file... OMG ;(

Can someone PLS post a fix that a nooB can 1) follow 2) wrap his head around 3) that is known to work

My info is this:

Toshiba Laptop 
GeForce4 440 Go graphics card

Ubuntu wants me to install the nvidia restricted driver but I get white screen.
Please don't ask for my xorg.conf since I am writing this on my wife's MS machine......... not by choice

Hiw do I "sudo" in gedit so I don't have to sudo dpkg-blah blah just to get out of white screen hell and change my conf settings?

---

### Post by boardfoot on 2008-01-03
I would actually settle for a quick rundown on editing the xorg.conf :)

Can I do it in the GUI? (gedit) If so... how? I suspect becoming root is the problem...

Any help would be greatly appreciated.

Cheers,
Jay

---

### Post by taurus on 2008-01-03
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by overdrank on 2008-01-03
> **boardfoot said:**
> I would actually settle for a quick rundown on editing the xorg.conf :)

Can I do it in the GUI? (gedit) If so... how? I suspect becoming root is the problem...

Any help would be greatly appreciated.

Cheers,
Jay

HI and you can edit you xorg with 
```
gksudo gedit /etc/X11/xorg.conf
``` I was going to suggest when you edit to change the driver to nvidia instead of nv then you may want to add this under the device section
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
And at the end add
Section "Extensions"
Option "Composite" "Enable"
EndSection
And this may help with the 3-d
Good luck!

---

### Post by boardfoot on 2008-01-03
Thanks for the help guys.

I've spent so much time analyzing xorg.conf that I don't really need the dpkg-reconfigure xserver-xorg terminal... the sudo command from terminal bypassed the permission problems and I'm editing in gedit finally (THANK YOU!)

However, my new found ease of editing has brought me to a dead end. It doesn't seem to matter what I add/change/try I cannot get 3d acceleration in the "nvidia" driver. In fact, if I use the nvidia driver I get the same white screen (and/or restricted drivers errors when I hammer through the additions listed in last post.)

Outside of new drivers... I suspect I'm doomed to the nv drivers which seem to be the only drivers that work outside VGA and VESA. It's not a huge deal since I use KOffice, firefox, t-bird, etc and no gaming, but it would be nice to put this prob to rest and be using purpose-built drivers.

GeForce 440 Go is the chipset and white screen is the prob. Hope someone has another idea. 

Cheers,
Jay

P.S. Outside the nvidia prob I love the OS so far... bye-bye MS at last...

---

### Post by overdrank on 2008-01-03
> **boardfoot said:**
> Thanks for the help guys.

I've spent so much time analyzing xorg.conf that I don't really need the dpkg-reconfigure xserver-xorg terminal... the sudo command from terminal bypassed the permission problems and I'm editing in gedit finally (THANK YOU!)

However, my new found ease of editing has brought me to a dead end. It doesn't seem to matter what I add/change/try I cannot get 3d acceleration in the "nvidia" driver. In fact, if I use the nvidia driver I get the same white screen (and/or restricted drivers errors when I hammer through the additions listed in last post.)

Outside of new drivers... I suspect I'm doomed to the nv drivers which seem to be the only drivers that work outside VGA and VESA. It's not a huge deal since I use KOffice, firefox, t-bird, etc and no gaming, but it would be nice to put this prob to rest and be using purpose-built drivers.

GeForce 440 Go is the chipset and white screen is the prob. Hope someone has another idea. 

Cheers,
Jay

P.S. Outside the nvidia prob I love the OS so far... bye-bye MS at last...

HI and it sounds like you are using KDE so you may look here for some help as I don't use KDE
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
Good luck!

---

### Post by aktiwers on 2008-01-04
Why don't you try install them manually?

This is how you install them manually:

Go here and download the latest  driver:
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
(here is the main link [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1
Log in
 type:
```
cd Desktop
``````
sudo /etc/init.d/gdm stop
``````
sudo chmod +x NVIDIA-Linux-x86-169.07.pkg1.run
```And then
```
sudo ./NVIDIA-Linux-x86-169.07.pkg1.run
```when done.. type:
```
sudo reboot
```

---

### Post by boardfoot on 2008-01-05
Thanks for the additional help on the NVIDIA drivers, but upon attempting to deploy your suggestions I have encountered another problem:

1) First of all... upon reading the master page posted and looking up the driver device compatibility sheet I found that I have to use legacy drivers (96.43)

2) #1 wouldn't be a problem except that 7.10 uses a linux kernel that is not recognized by the installer... so it gives me the option to compile using my current kernel... great... whamo...

Turns out I do not have the <b>lib.c</b> libraries required to do this new compiling.

My puter hasn't worked this good in years (minus the graphics driver issue which is kind of a non-issue since I am not running anything that requires it) so I am hesitant to fix that which is not broken in light of the potential havoc it could cause me if it doesn't take.

However, upon reading NVIDIA page and docs it seems that these 96.43 drivers are the ones that solve my specific problems (white screen on login). So I kinda want to install them and be done with it.

So... I have 1 more newbie request:

Is there a package or something that will allow me to install the lib.c library specific to ubuntu 7.10?

Thanks for your help so far, and I hope I might see 1 more post with an answer to my last question.

Cheers guys,

Jason

---

### Post by xeth_delta on 2008-01-05
> **boardfoot said:**
> Thanks for the additional help on the NVIDIA drivers, but upon attempting to deploy your suggestions I have encountered another problem:

1) First of all... upon reading the master page posted and looking up the driver device compatibility sheet I found that I have to use legacy drivers (96.43)

2) #1 wouldn't be a problem except that 7.10 uses a linux kernel that is not recognized by the installer... so it gives me the option to compile using my current kernel... great... whamo...

Turns out I do not have the <b>lib.c</b> libraries required to do this new compiling.

My puter hasn't worked this good in years (minus the graphics driver issue which is kind of a non-issue since I am not running anything that requires it) so I am hesitant to fix that which is not broken in light of the potential havoc it could cause me if it doesn't take.

However, upon reading NVIDIA page and docs it seems that these 96.43 drivers are the ones that solve my specific problems (white screen on login). So I kinda want to install them and be done with it.

So... I have 1 more newbie request:

Is there a package or something that will allow me to install the lib.c library specific to ubuntu 7.10?

Thanks for your help so far, and I hope I might see 1 more post with an answer to my last question.

Cheers guys,

Jason

Try installing some extra packages:

```
sudo aptitude install libc6 libc6-dev
```

[EDIT] You might also need some development packages:

```
sudo aptitude install build-essential linux-headers<your version>
```

You can find out your kernel version with:
```
uname -r
```

Xeth

---

### Post by empty_spaces on 2008-01-05
Just saw this thread, and it is pretty much as exact description of the problems I have faced with my Toshiba Satellite laptop(2415-S205). 
My graphics card is GeForce4 420 Go instead of the 440 being discussed here. Went through all the trial and errors as mentioned above, but got the black screen of death everytime I changed/installed the nvidia driver.
Finally, I resigned myself to the fact that my laptop, being at least 5 years old, the GeForce card is not going to play along with the legacy/restricted graphics drivers.

Do post updates on your progress.

Cheers.

---

### Post by aktiwers on 2008-01-05
Yes Xeth is right, you need to install those first. I totally forgot that I had installed them. Also Empty_Spaces follow Xeths post first, then mine then everthing should be fine :)

---

### Post by cjm5229 on 2008-01-05
Have you tried using Envy? It has an installer for manually installing NVidia drivers. If you search the forums for "Envy"you should be able to find a "How to" on using it. It is an app for installing graphics drivers when "Restricted Drivers" doesn't get it right.

---

### Post by boardfoot on 2008-01-05
Wow... cheers guys.

I'll first try Envy (less work... I'm moderately lazy) and see if it works later. If not, I'll attempt the lib.c compile when I have a night to myself.

I must admit though, this Toshiba 5100 Satellite was a real PITA for driver support in Winsux  as well, so I'm at peace with no 3d accel... it's the natural course for a 4-5 year old laptop with a solid history of graphics driver issues transcending the OS spectrum.

Beers all around for the kind souls who have helped.

Cheers,

Jason

---

### Post by empty_spaces on 2008-01-05
fyi, with reference to my previous post, I would like to add that I have tried Envy without success.
Just thought I'd mention that, since we both have pretty much the same graphics card.
Of course, if Envy works for you, that would be great.

---

### Post by empty_spaces on 2008-01-10
Hey Boardfoot, 
I was wondering if you had any luck with this issue. Would appreciate any updates on what worked and what did not.
Thanks

---

