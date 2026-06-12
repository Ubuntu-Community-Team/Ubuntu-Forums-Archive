---
title: "Installing Nvidia Geforce 2 GTS on ubuntu"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by drstrangelove on 2007-09-14
Hi guys! Have just installed Ubuntu on a 6 year old pc, and the installation went fine. Problem is I cant get any higher resolution than 1024x768@60Hz. Downloaded the "NVIDIA-Linux-x86-1.0-9755-pkg1.run", but when I click it on my desktop I get the following error msg: 

(Norwegian)
Kunne ikke åpne fil /home/ragnar/Desktop/NVI…nux-x86-1.0-9755-pkg1.run som bruker tegnkoding Unicode (UTF-8).

Translated to english it would be something like:

Could not open file /home/ragnar/Desktop/NVI…nux-x86-1.0-9755-pkg1.run that uses ... Unicode (UTF-8)

Please help! :-)

---

### Post by CaptainInsaneO on 2007-09-14
Ok, make sure you've run all available updates (especially kernel updates) and then install a program called [Envy]("http://albertomilone.com/nvidia_scripts1.html"). I have the same exact video card as you and this is how I installed the drivers. Good luck!

---

### Post by amneziac on 2007-09-14
i think the best thing to do is to install Envy, it makes installing nvidia and ati drivers a lot easier
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
when uve installed envy just open it and itll give u an option to install nvidia driver

---

### Post by drstrangelove on 2007-09-14
Thanks guys, quick response! I downloaded and installed the new drivers via envy. But i still cant increase my resolution. Any suggestions?

---

### Post by nonewmsgs on 2007-09-14
sometimes you have to manually 

```

sudo gedit /etc/X11/xorg.conf

```
 and addthe desired rez in front of the highest resolution.

also it's a good idea to double check the horizontal sync and vertical refresh (vice versa?)

---

### Post by drstrangelove on 2007-09-14
> **nonewmsgs said:**
> sometimes you have to manually 

```

sudo gedit /etc/X11/xorg.conf

```
 and addthe desired rez in front of the highest resolution.

also it's a good idea to double check the horizontal sync and vertical refresh (vice versa?)

Sorry for being such a noob :(

But where exactly do I  type this? Console?

---

### Post by ofb on 2007-09-14
> **drstrangelove said:**
>  Problem is I cant get any higher resolution than 1024x768@60Hz. 

Quick question - is it actually running at 60Hz? For some reason, Ubuntu reports lower than reality.

I have GeForce4 MX440-SE. Ubuntu's Screen Resolution Preferences reports 50Hz, which is obviously fiction. My monitor's built-in software reports 85Hz, which makes sense, as there is no flickering.  I also had no flicker with the LiveCD's of Ubuntu and Xubuntu  on my other box with a GeForce2. I haven't used Envy.

---

### Post by ofb on 2007-09-14
> **drstrangelove said:**
> But where exactly do I  type this? Console?

Yes. It'll open the xorg.conf in Gedit under root, so you'll have permission to change the file.

You better make a backup copy first, if you're going to play with that.  (You can also damage your monitor with the wrong settings, so you better know what you're doing.)

---

### Post by Maestro23 on 2007-09-14
> **ofb said:**
> Yes. It'll open the xorg.conf in Gedit under root, so you'll have permission to change the file.

You better make a backup copy first, if you're going to play with that.  (You can also damage your monitor with the wrong settings, so you better know what you're doing.)

And in the xorg.conf, you are looking for the following section:

> Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    #1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection


---

### Post by CaptainInsaneO on 2007-09-14
To make a backup of your xorg.conf, open a terminal and type this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

In case you bork something (happens to me all the time, no worries) you can replace your (working) backup file like this from a tty:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Edit your xorg.conf file using gedit:

```
sudo gedit /etc/X11/xorg.conf
```

I've included the Screen section from my xorg.conf, since I use the same card as you:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce 8800GTS"
	Monitor		"2407WFP"
	Option		"AddARGBGLXVisuals" "true"
    DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
EndSection


```

Note that the resolutions in your screen section all depend on your monitor, my monitor supports UP TO 1920x1200, edit this to suit your needs.

Hope this helps!

---

### Post by drstrangelove on 2007-09-14
> **Maestro23 said:**
> And in the xorg.conf, you are looking for the following section:

Thanks, I put the "1280x1024" in front of "1024x768" in xorg.conf. But still 1280x1024 doesnt appear as an option in "Systm -> Settings -> Screen res"

---

### Post by drstrangelove on 2007-09-14
And, yeah, my monitor supports 1280x1024.

---

### Post by CaptainInsaneO on 2007-09-14
Did you restart your x server after saving your xorg.conf? The hotkey is Ctrl+Alt+Backspace.

---

### Post by drstrangelove on 2007-09-14
Did now, didnt work...

---

### Post by alienexplorers on 2007-09-14
Try adding a modeline to your MONITOR section of your xorg.conf file.  I have a link to a modeline maker in my signature line.

> # 1280x1024 @ 70.00 Hz (GTF) hsync: 74.62 kHz; pclk: 128.94 MHz
  Modeline "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
You may need to adjust refresh rate as this is just an example.

You could also try running the nvidia-settings program.
> sudo nvidia-settings

---

### Post by drstrangelove on 2007-09-15
Tried adding the modeline and restart xserver. BTW, I am supposed to include the line above the Modeline-line? Anyway, it didnt work.

When I  run "sudo nvidia-settings", I get the following;

> 
ragnar@ragnar-desktop:~$ sudo nvidia-settings 

ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.9.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


---

