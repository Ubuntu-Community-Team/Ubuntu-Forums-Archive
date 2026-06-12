---
title: "does restricted manager detects and installs ati radeon 9800 pro 128mb drivers?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by syms on 2008-01-02
hi,
does restricted manager will install this radeon drivers? i hear that there is problems to find ati drivers in linux. so does it works? or i need to install drivers in more difficult way?

---

### Post by Ub1476 on 2008-01-02
[Envy]("http://albertomilone.com/nvidia_scripts1.html") will automatically download the latest driver from ATI's website (7.12) and configure them for you. The drivers in RDM are more stable though. According to some google searches, you are likely to get a blackscreen upon starting if you use the restricted drivers.

---

### Post by syms on 2008-01-02
> **Ub1476 said:**
> [Envy]("http://albertomilone.com/nvidia_scripts1.html") will automatically download the latest driver from ATI's website (7.12) and configure them for you. The drivers in RDM are more stable though. According to some google searches, you are likely to get a blackscreen upon starting if you use the restricted drivers.

thanks, i didnt knew that :). i know envy. so u say that drivers installed from envy are more stable than from restricted manager?

---

### Post by w4ett on 2008-01-02
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager. (try this option first)

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from AMD/ATI [http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html)

To use Envy, navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then install the correct ATI proprietary driver.

Good Luck
__________________

---

### Post by Ub1476 on 2008-01-02
No, the latest driver from ATI is buggy as hell, but if you want 3d effects it's the only way for you to go at the moment, I think. You can always try to use the drivers from RDM though. ATI/AMD has just started supporting Linux, so hopefully when the next Ubuntu is released those will be incuded and will be stable (which means 3d works out of the box).

I use Envy myself, and the issues I have is:

[LIST]
[*]Flickering on video playback (not on the web)
[*]Slower 3d effects compared to RDM and XGL
[*]Firefox scrolling is not very smooth
[/LIST]

BTW, to run Envy in a GUI type:

```
envy -g
```

---

### Post by esteckis on 2008-01-02
ATI has a new driver dated 12/20/07, I have used it with no problems on Ubuntu Gutsy 64 bit.  The prior ATI driver caused rebooting of Ubuntu whenever an opengl screensaver started on my system.

---

### Post by w4ett on 2008-01-02
3D effects (and Compiz) do work with the open source xorg-driver-ati as well....I use them with my ATI 9200SE card with good results and also good use of google earth.

---

### Post by Heinstein on 2008-01-02
> **esteckis said:**
> ATI has a new driver dated 12/20/07, I have used it with no problems on Ubuntu Gutsy 64 bit.  The prior ATI driver caused rebooting of Ubuntu whenever an opengl screensaver started on my system.

Do you got 3d acceleration  with those drivers?

---

### Post by esteckis on 2008-01-04
OK, with all the pages of getting ATI's driver installed for the video card, The NEW envy did get the new ATI driver and installed it for me. How I know is that if I go to the restricted driver, the ATI is listed but not checked and there is a green light all the way to the right stating that the ATI driver is running.  That is supposed to let you know that your new driver is being used and the old FLGRX is not (I guess) (that was on another site stating how to check that the new driver is being used) As to 3d effects. Out of all the posts for installing the ATI driver, I could never get the advanced effects to be used. But by using Envy, I was able to get advanced effects  to be used and also to get COMPIZ to work also (funny, ATI's site states that compiz is not comaptible)

The NEW Envy program installed the new driver and special effects and compiz both work. The only thing with the new ATI driver for me is the screen slightly flickers when the screen saver is running. Out of 12 times of trying to get the ATI installed, special effects to take and Compiz working, this NEW ENVY version worked for me.

ENVY site [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

My ATI video is onboard 1250 series.  using UBUNTU Gutsy amd 64

---

