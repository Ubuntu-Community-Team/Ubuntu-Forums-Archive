---
title: "Enabling extra visual effects"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by PogMoThoin on 2007-10-20
Hey all,

I'm a complete noob when it comes to ubuntu, but i would consider myself an advanced windows user & overclocker. I have the hardware to run advanced visual effects ie core2quad, nVidia 7900GT & 2Gb ram, but when i click extra visual effects, it tells me i must enable the accelerated graphics driver, i get the following when i try
> The software source for the package

   nvidia-glx-new

 is not enabled.
and then it tells me that the driver will be enabled after a restart i have the same problem

Any help would be great,

Pog

---

### Post by Anztac on 2007-10-20
Have you installed the restricted drivers with the Restricted Driver Manager yet?  I believe it's under Administration...

---

### Post by PogMoThoin on 2007-10-20
No as I said, I'm a complete noob, please tell me how?

---

### Post by Gawc on 2007-10-20
I am a complete noob too, and had the same problem.

After reading boards, and screaming at my computer, I tried reinstall Ubuntu, and now it works for me.

Dont know what I did different except had internet access second time around.

---

### Post by PogMoThoin on 2007-10-20
Ok, tried to instaling in restricted drivers manager & still no luck. Just get the same 

The software source for the package

nvidia-glx-new

is not enabled.

Can anybody help please

---

### Post by PogMoThoin on 2007-10-20
Bump :confused:

Have dl'ed the nvidia driver mentioned on [this]("http://ubuntuforums.org/showthread.php?t=583439") thread, but cannot install them. I get this error > Could not open the file /home/colm/Desktop/NVIDI&#8230;ux-x86-100.14.19-pkg1.run.

---

### Post by PogMoThoin on 2007-10-20
Ok, got it working, for those with the same problem, open syntapic package manager & do a search for > nvidia-glx-legacy. Under settings click repositories & check all the boxes. Then it'l download.

---

### Post by Celegorm on 2007-10-20
> **Gawc said:**
> Dont know what I did different except had internet access second time around.

The internet access is what made it work- the restricted driver is not included by default and must be downloaded from the repositories before it can be enabled.

---

### Post by maxxym on 2007-10-20
Newbie here.. I managed to get it working...


First, you need to install Restricted drivers...it won't install for you because when you click to Enable the driver, it tells ya that there is no source, right? Been there...

First, you need to enable something.... so go to :

System>Administration>Software Sources
Type in your Root password
Check all boxes...

Now go to:

System>Administration>Restricted Drivers
Put the checkbox next to your device to enable it.

It will tell you that you need to download drivers....Go ahead and do it...then it will show you download window.. it might hang there for a while with progress at 0%. Just be patient and let it do it's thing. It took me about 5 minutes to finally start downloading the drivers... Once that is done, restart your Xserver by doing CTRL+ALT+BACKSPACE


Now to to Apperance and turn on your desktop effects and see if they work....

---

