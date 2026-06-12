---
title: "[SOLVED] Nvidia - Help needed"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-01-16
I installed a new video card, Elsa Synergy 2000 (Xserver identifies it as Nvidia Quadro 2 MXR/EX/Go) and it uses the Nvidia Quadro2 chip with 32MB. Previously I was using the onboard Intel graphics (i815e).

I installed the Nvidia driver (from Nvidia directly) and I was getting only a white screen after the login screen. So I uninstalled it. Reconfigured xserver-xorg.

I got it to work with 3D effects using Ubuntu's nvidia-glx. However, a few things are strange:

1. Although I set the monitor as ViewSonic VA520, 1024x768 @ 75Hz, it keeps coming back as ViewSonic VA520, 1024x768 @ 50Hz (and the choice are 51, 52, 53, 66 in the set resolution utility)

2. The Title bar in all windows/applications is tiny. I would say about half the size it should be.

Thanks

---

### Post by SOULRiDER on 2008-01-16
Are you sure you need the nvidia-glx package and not the nvidia-glx-legacy?

---

### Post by lduplantie on 2008-01-16
Good Question. How can I determine which is the preferred?

---

### Post by SOULRiDER on 2008-01-16
[http://packages.ubuntu.com/gutsy/x11/nvidia-glx](http://packages.ubuntu.com/gutsy/x11/nvidia-glx)
> These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and support the newer GeForce, nForce and Quadro families of NVIDIA chipsets. AGP, TV-out and flat panel displays are also supported. Looks like you got the right driver...

Why dont you try reinstalling them using envy? I highly doubt it will fix it, but it may...

---

### Post by OffAxis on 2008-01-16
32 MB Quadro 2 should land you solidly in the legacy category.

You can get the legacy driver for your card from nvidia here:
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html")

Interestingly enough, nvidia packages their legacy drivers into two distinct categories, so you should make sure that your card is on the listing (I checked on the link above, and it was listed)
Here's the list:
[http://www.nvidia.com/object/IO_32667.html]("http://www.nvidia.com/object/IO_32667.html")

or you can try the nvidia-glx-legacy driver from the repository (which I believe the 'Restricted Driver Manager' will install)


You can also try this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by SOULRiDER on 2008-01-16
I think it should be legacy too, but the package description says its not legacy.

---

### Post by lduplantie on 2008-01-16
I used Envy to install the driver.

The problem with the title bar has been solved.

When I enable the graphic accelerator, the screen capabilities are overstated in terms of resolution and understated in terms of refresh rate.

When I disable the graphic accelerator, the monitor's spec are correctly stated.

I just noticed that the keyboard has been set to US/PC101 instead of what I originally had i.e. ca/PC105. Hum!

---

### Post by OffAxis on 2008-01-16
> I think it should be legacy too, but the package description says its not legacy.
You're right. I was looking at the description which said Newer Quadro families, so I assumed the 3 and 4 series; I missed it in the package's dependency list.

I also found this on the Binary Install page
>     *

      nvidia-glx-legacy (corresponds to the 71xx driver)
    *

      nvidia-glx (which corresponds to the 96xx driver)
    *

      nvidia-glx-new (which at the time of writing corresponded to the 97xx driver)


which clearly spells it out, too.

Thanks SOULRider.

---

### Post by lduplantie on 2008-01-16
Envy apparently installed the nvidia-glx and nvidia-glx-dev.

Can I aks OffAxis and SoulRiDER their recommendation.

Should I unistall the envy drivers and go with the legacy?

---

### Post by lduplantie on 2008-01-16
I attribute the Title bar problem to Compiz. I removed it. Title bar is back to normal.

As for the screen resolution and refresh rate, I beleive it has to do with the proprietary nvidia drivers or how Envy install them. If you de-activate the accelerator nvidia-glx is removed and the screen res and rate is back to normal. I guess the driver is now from the xserver-xorg-video-nv package.

Thanks to all

---

### Post by SOULRiDER on 2008-01-17
The nv driver doesnt give you 3D acceleration though.

---

### Post by lduplantie on 2008-01-17
Oh well. I got frustrated and re-installed Ubuntu. Used Envy to install the nvidia driver. Ubuntu just did not want to enable desktop effects. Installed XGL. Launched compiz from a terminal [compiz --replace &]. It worked with a few problems (missing window frames). Got the answers from [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org). Lots of help there for many distros.

Thank you all

---

