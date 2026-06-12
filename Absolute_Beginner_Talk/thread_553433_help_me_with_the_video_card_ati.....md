---
title: "help me with the video card ati...."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by reduardo182 on 2007-09-17
i've just installed the ubuntu Feisty Fawn today and i don't know where o how to install the driver of video card ati .... my video card is ati radeon 1050 and how can i do to work the video card in ubuntu....

---

### Post by w4ett on 2007-09-17
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from AMD/ATI [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck

---

### Post by reduardo182 on 2007-09-17
ok i'm just installing envy, now how can i to change the screen resolution???? just now is 1024 x 768 and really everything is big....

and can i to play old games in ubuntu ( for example resident evil 3, unreal tournarment, age of empire)

---

### Post by w4ett on 2007-09-17
to change screen resolution:

System>Preferences>Screen Resolution on the top panel.

to play those windows games you will need to install [COLOR="Blue"]Wine[/COLOR].

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Good Luck.

---

### Post by Maestro23 on 2007-09-17
> **reduardo182 said:**
> ok i'm just installing envy, now how can i to change the screen resolution???? just now is 1024 x 768 and really everything is big....

and can i to play old games in ubuntu ( for example resident evil 3, unreal tournarment, age of empire)

If you are looking to play windows games, you need to look into WINE or Cedega.

Winehq: [http://www.winehq.org/](http://www.winehq.org/)

Cedega: [http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by alienexplorers on 2007-09-17
what resolutions and refresh rates are you looking to run.  Please list your monitor type or vert & horz refresh rates.

---

### Post by reduardo182 on 2007-09-17
i can't to change the screen resolution since sistem - preferences.... mi screen is a dell se 177fp and in windows the resolution it was 1200 x 900 and now in ubuntu i can't over the 1024 x 768

how can i to know if my video card is just installed?

---

### Post by alienexplorers on 2007-09-17
You could try adding a modeline such as >   # 1280x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 94.84 MHz
  Modeline "1280x900_60.00"  94.84  1280 1352 1488 1696  900 901 904 932  -HSync +Vsync to your monitor section of xorg.conf file.

---

