---
title: "screen resolution with ati card"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by cgons on 2007-01-16
well i was trying to install xgl on my system which led me to trying to see if i had 3D rendering enabled...i don't  so i found a few tutorials on the subject.... anyhow, i wish i didn't because now my screen is kinda fuzzy or out of sharp focus...

my system 
dell1501 laptop
amd64 X2 
edgy
ATI RADEON® Xpress1150 256MB HyperMemory™ (Integrated)

first i downloaded and installed the driver i "think" i needed
```
sudo apt-get install xorg-driver-fglrx
```

then i followed the steps to configuring it
```
sudo dpkg-reconfigure xserver-xorg
```

when i was brought to the next menu i set fglrx but i obviously messed up the settings somehow but i don't now where.....i checked to see if the 3D rendering worked
```
glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

```

so now i'm left with a fuzzy, out of focus screen...and no real idea on how to fix it...so my question is this

1.is my card even capable of rendering 3D graphics? if so how do i continue with the installation? and if not how to i get back to the original state?

thanxs for any help....

---

### Post by discord on 2007-01-17
check out the beryl project website. They should have all the info you need.

---

### Post by CowzRule on 2007-01-17
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by cgons on 2007-01-17
thanks for the link its just what i was looking for and apparently this will also fix my hibernation issues.....nice.

i also didn't know it was called beryl i thought it was the xgl/compiz window????????? just me being a noob..lol..anyway i'll post my results later today..

---

### Post by CowzRule on 2007-01-17
Beryl is what they call a "fork" of Compiz. They both pretty much do the same thing but just go about doing it in different ways.
Here's the info I used for setting up XGL and Beryl
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL")

---

### Post by tibore on 2007-01-24
Hi guys,
I had also problem with scrolling and rendering, but the driver from the [http://ati.amd.com/support/drivers/linux/linux-firegl.htm](http://ati.amd.com/support/drivers/linux/linux-firegl.htm) page solved the problem.
Thanks.

---

