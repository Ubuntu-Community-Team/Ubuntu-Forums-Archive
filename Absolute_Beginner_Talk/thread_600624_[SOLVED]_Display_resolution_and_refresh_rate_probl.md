---
title: "[SOLVED] Display resolution and refresh rate problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by dmxsoulja3 on 2007-11-02
Using Ubuntu Gutsy and a Viewsonic VA900b 19inch monitor with an Nvidia 8300GS, I'm hoping for 1280x1024 at 70-72hz or higher which is what I use in Windows but I can't make this combination work at all or I should say I can get the res but only like 50hz.

My monitor is not in the Viewsonic list so if IIRC I decided on just one of the LCD panels.

Any ideas?

---

### Post by Steve1961 on 2007-11-02
First of all make sure you install the nvidia driver for your graphics card.  [Envy]("http://albertomilone.com/nvidia_scripts1.html") is probably your best bet.

---

### Post by dmxsoulja3 on 2007-11-02
Interesting I'm running whatever is installed initially, it shows as an Nvidia driver under my Screen and Graphics settings.

I will give this a try.

---

### Post by Steve1961 on 2007-11-02
Unless you've installed the nvidia driver using the restricted driver manager you've probably just got the open source nv driver.  Check by opening a terminal and typing nvidia-settings.  If the nvidia configuration utility opens then the driver is already installed.

---

### Post by dmxsoulja3 on 2007-11-02
Thank you for pointing this out, I bet this will get me going, I noticed just everything was jerky on the screen effects and such, and plus my monitor kinda distorts the fonts unless the refresh rate is on up there.

---

### Post by Steve1961 on 2007-11-02
No problem, but it's really important to make sure that "if" you have installed the nvidia driver by the restricted driver manager (you may not realise you have done this) that you uninstall it before using envy.  I believe that the nvidia drivers in the Ubuntu repo don't work well with geforce 8 series cards, so you need to install the latest driver with envy. The following command should check that everything is uninstalled:

sudo apt-get --purge remove nvidia-glx nvidia-glx-new

Then open a terminal and type:

sudo gedit /etc/X11/xorg.conf

Make sure you change the "nvidia" driver entry that looks something like this

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"

to "nv"

If it already says nv then you probably don't have the driver installed.  Once done restart x by alt-ctrl-backspace

---

### Post by lenu on 2007-11-02
> **Steve1961 said:**
> No problem, but it's really important to make sure that "if" you have installed the nvidia driver by the restricted driver manager (you may not realise you have done this) that you uninstall it before using envy.  I believe that the nvidia drivers in the Ubuntu repo don't work well with geforce 8 series cards, so you need to install the latest driver with envy. The following command should check that everything is uninstalled:

sudo apt-get --purge remove nvidia-glx nvidia-glx-new

Then open a terminal and type:

sudo gedit /etc/X11/xorg.conf

Make sure you change the "nvidia" driver entry that looks something like this

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"

to "nv"

If it already says nv then you probably don't have the driver installed.  Once done restart x by alt-ctrl-backspace

did this, but no change. my screen still "breaks"/flickers/lags when watching movies, dragging windows or rotating the cube. my setup: gutsy, amd64 3500+, 1gb ram, geforce 8500gt, 19" crt by belinea. 

my screen problems started when i upgraded to gutsy. feisty was fine.

---

### Post by Steve1961 on 2007-11-02
Weird.  Have you given envy a shot?

---

### Post by dmxsoulja3 on 2007-11-02
So fressssh, got the nvidia display tool as well, swapped to 75 hz and 1280x1024 and loving it... ENVY is awesome.

Thanks buddy

---

### Post by Maestro23 on 2007-11-02
> **dmxsoulja3 said:**
> So fressssh, got the nvidia display tool as well, swapped to 75 hz and 1280x1024 and loving it... ENVY is awesome.

Thanks buddy

Glad you got it going. Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by lenu on 2007-11-03
> **Steve1961 said:**
> Weird.  Have you given envy a shot?

yes, i immediately installed envy. what confuses me are the numerous ways of changing the resolution and refresh rates - and especially how they seem to differ from each other in what they claim the output _is_ at any given moment. there are:

[LIST]
[*]nvidia-settings (which don't seem to let me manually alter the refresh rates)
[*]the xorg.conf file
[*]system - preferences - screen resolution (which has a peculiar tendency to display my refresh rate as 50 kh)
[*]system - preferences - advanced desktop settings - general - display settings - refresh rate. (in conjunction with the tick box sync to vblank in nvidia-settings, i suppose).
[*]dpkg-reconfigure xserver-xorg 
[/LIST]

*edit:* i got rid of the splittered windows effect (when dragging a window, it would split into several blocks, especially visible with wobbly windows). however, video playback still isn't satisfying. it is hard to describe it, the picture just doesn't run smoothly. 

should i be starting a new thread or does this seem related to the original problem of this thread?

---

### Post by Steve1961 on 2007-11-03
Try sudo nvidia-settings to make changes stick

---

