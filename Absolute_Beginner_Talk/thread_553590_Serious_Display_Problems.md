---
title: "Serious Display Problems"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by phlak on 2007-09-17
Ok, I'm on my second fresh install of Ubuntu, and about to start my third, here is the problem.

On my first fresh install, I enable the Nvidia restricted drivers to try and get the desktop effects working, and hopefully start operating at the correct resolution (1680x1050 NOT 1024x768) I soon realized that this was a bit idea, as Gnome would not longer start up for me, and there seemed to be no fix, so formatted and started over.

Here I am: I used apt-get -nvidia-glx to get the newest nvidia glx drivers, I followed all of the directions found on this forum regarding setting up nvidia drivers, and now once again, Gnome will not start up, and it states:

"Failed to load module wfb
Need libwfb but wfbscreen not found
Addscreen/Screeninit failed for Driver 0"

The worst part is, after this happens, it returns me to a blank screen (No login prompt or motd) and allows me to type on the screen, but with no response.

---

### Post by w4ett on 2007-09-18
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove your old  drivers and install the correct Nvidia proprietary driver.

Good Luck

---

