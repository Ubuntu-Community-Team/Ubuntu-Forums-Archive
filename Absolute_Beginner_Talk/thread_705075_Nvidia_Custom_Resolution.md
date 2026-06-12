---
title: "Nvidia Custom Resolution"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by uchihaitachi on 2008-02-23
Does anybody have any idea how I can go about getting a custom resolution on my laptop?

I'm using a T61P with a WUXGA screen 1920 x 1200 and Ubuntu detects and uses this resolution just fine.

However this resolution setting strains my eyes when used for extended periods so I want to switch to a custom resolution of 1280 x 800.

My closest attempt through changing the screen and monitor produced a resolution of 1280 x 800 in a screen of 800 x 532. Every other option I had tried resulted in 1280 x 1024.
 
modifying the xorg file has had little results so far.
Help anybody?

---

### Post by asmoore82 on 2008-02-24
I'm a fairly advanced GNU/Linux user and I too would be interested in a solution to this;
I'm migrating over to a Lenovo T61 with Intel GMA and it only seems to like to run in 1280x800.

---

### Post by Miller12 on 2008-02-24
I'm a noob but this was the answer give to me (for a different resolution problem though). It's a modline line change in xorg.conf. Not sure if you see it in apps>screen resolutions though.

Try this one: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by uchihaitachi on 2008-02-26
Yup I've checked out that thread but I've yet to get the result that I'm looking for.

I'm positively sure that this is a problem with the Nvidia drivers since I've no problem achieving what I want with the Vesa drivers. The Nvidia drivers just don't have a 1280 x 800 configuration.

Plus the Nvidia driver ignores the settings that I've made in xorg.conf which makes it frustrating to say the least.

---

### Post by herbster on 2008-02-26
Have you tried nvidia-settings?

---

### Post by Miller12 on 2008-02-28
I used Envy to install the latest nvidia driver and let it configure my xorg.conf. I don't have a widescreen monitor so I'm not sure if it would be any help.

nvidia-settings will be installed with Envy.

---

### Post by uchihaitachi on 2008-03-03
Yup I've tried nvidia settings. I can't get 1280 x 800.

---

### Post by Miller12 on 2008-03-03
try typing this into the terminal
```
xrandr -q
```
it will list all the resolutions for your video driver.

---

### Post by uchihaitachi on 2008-03-03
Thanks for the command.
Just as I suspected the resolution that I'm looking for is not offered.
It's either 1280 x 1024 or 804x525

I've yet to read of anybody who managed to force the Nvidia driver to display a resolution it doesn't support. Why should Nvidia restrict the resolution to so few options? The VESA optoin has the 1280 x 800 mode and it works just fine.

---

### Post by LowSky on 2008-03-03
just thought I should put this out there... many new LCD monitors can only run in one setting, Ubuntu relies on the graphics card to do t5he scaling.

Go to nvidia-settings and look for the scaling option. change it to graphics card instead of monitor

---

### Post by herbster on 2008-03-03
Yes, the scaling is probably it. LCD monitors have trouble using resolutions other than their native ones, depending on the driver of course, but it's not uncommon. In nvidia-settings, click on your monitor and see the scaling options,

---

