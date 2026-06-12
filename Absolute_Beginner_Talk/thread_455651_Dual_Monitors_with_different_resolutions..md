---
title: "Dual Monitors with different resolutions."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2007-05-26
I want to buy a new monitor so that I can hook it up to my laptop and watch movies or what not. 
The problem is that the monitor I'm looking to buy has a 1600x1050 resolution, and my laptop has a resolution of 1280x800.

I tried to connect a second monitor to the laptop using TwinView, but the laptop half of the setup took on the resolution of the larger monitor, and only displayed part of the desktop.

Is there any way to set it up so that the smaller half of the setup has retains it's own resolution?

Here's the monitor I want to buy:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16824116075](http://www.newegg.com/Product/Product.aspx?Item=N82E16824116075)

---

### Post by shanepardue on 2007-05-26
What video card are you using? Nvidia has a control panel that makes this process much easier.

```
sudo nvidia-settings
```

---

### Post by RussianVodka on 2007-05-26
> **shanepardue said:**
> What video card are you using? Nvidia has a control panel that makes this process much easier.

```
sudo nvidia-settings
```

nVidia GeForce 7400

I used nvidia-settings, and I got those problems. If i try to use "separate X screen", it tells me i have to save xorg.cfg. When i do that, it gives me errors.

---

### Post by shanepardue on 2007-05-26
Interesting. I have separate resolutions with twinview and I'm using the same control panel. Just to make sure 
you're opening it with root and sacing the changes to your xorg through the control panel?

---

### Post by RussianVodka on 2007-05-26
> **shanepardue said:**
> Interesting. I have separate resolutions with twinview and I'm using the same control panel. Just to make sure 
you're opening it with root and sacing the changes to your xorg through the control panel?

When I click, "Save to X Configuration File", nothing happens, and i get these errors in the terminal:

```

ERROR: Unable to determine valid vertical refresh ranges for display device
       'LPL' (GPU: GeForce Go 7400)!


ERROR: Failed to add display device 'LPL' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

```

---

### Post by ivesjd on 2007-05-28
It worked fine on my fx 5500, with 19" crt and 27" tv

---

