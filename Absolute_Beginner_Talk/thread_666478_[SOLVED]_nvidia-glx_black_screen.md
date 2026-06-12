---
title: "[SOLVED] nvidia-glx black screen"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by sokre on 2008-01-13
Hi!
I know there are similar posts, so I could use link too (I do have other questions also)

1.
I am using kubuntu 7.1 on my laptop. (pent2.5 512ram geforce4 440 GO)
I should use nvidia glx, but I get this black screen.

I disabled nvidia glx from console, but that is not what I want...
I copy pasted xorg.conf in attachment

2.
I want to install KDE4.
I followed instructions,installed, but how can I change desktop - says login manager?? Is that login screen, I do not see it there.

3.
I connect to my router via wireless - has WEP. Kubuntu uses some WALLET?? AKA safety. I do not want it. Each time I turn on PC, I have to enter pass to wallet to connect to wireless.  ;(
Also, is there auto login? I do not need multiple users now. Could I skip that login screen during boot?

4.
When I enter /etc/init.d/kdm stop I exit X, right?
But I do not see user@pcname:. It isnt there. I can enter letters, but PC does not react

---

### Post by nikoPSK on 2008-01-13
well, let's reconfigure xorg! :D

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Best,
nikoPSK

---

### Post by mattismyname on 2008-01-13
4) Yes.  Try using <alt>+<F1> to switch to the first virtual console.  Hit enter a few times and you should see a login screen.  You can also try <alt>+<F2>, F3, etc

---

### Post by sokre on 2008-01-14
> **nikoPSK said:**
> well, let's reconfigure xorg! :D

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Best,
nikoPSK


I did reconfigure it, but without phigh.
I ll get on it now

---

### Post by bumanie on 2008-01-14
The above posters seem to know what they are talking about, however, from personal experience with an older nvidia driver, I had to go to the nvidia site and download a glx-legacy driver before I could the graphics working properly in gutsy.

---

### Post by nikoPSK on 2008-01-14
> **sokre said:**
> I did reconfigure it, but without phigh.
I ll get on it now
 
ah, well phigh puts it at optimum.. oh well...

---

### Post by sokre on 2008-01-14
Sorry for the bother.
I installed ubuntu, since I didnt like KDE4.
I also installed nvidia-glx, reconfigured xorg 

Unfortunately I have same problem.
Now nvidia-glx is not enabled.
So x  works.


sudo dpkg-reconfigure -phigh xserver-xorg
Doesnt help it turns out this
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080114205850

---

### Post by sokre on 2008-01-14
Solved (I hope)

added
usesisplaydevice "dfp"

Under device nvidia
in xorg.conf

For all beginners like me:


1. open terminal

2. write this

**sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup **

3. then this

**gksudo gedit /etc/X11/xorg.conf**

4. add this

**Option 		"UseDisplayDevice" "DFP"**

5. so it looks something like this

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" "true"
	Option 		"AllowGLXWithComposite" "true"
	Option 		"AddARGBGLXVisuals" "True"
	**Option 		"UseDisplayDevice" "DFP"**
EndSection


6. restart X (this is for Ubuntu)

**sudo /etc/init.d/gdm restart**

As I understand, for some reason, nvidia doesnt registrate monitor.
It is an easy fix, saw other people with same problems (that is how I solved it)
But took me while to find solution.

---

### Post by nikoPSK on 2008-01-14
> **sokre said:**
> Solved (I hope)

added
usesisplaydevice "dfp"

Under device nvidia
in xorg.conf

For all beginners like me:


1. open terminal

2. write this

**sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup **

3. then this

**gksudo gedit /etc/X11/xorg.conf**

4. add this

**Option         "UseDisplayDevice" "DFP"**

5. so it looks something like this

Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 440 Go]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "True"
    **Option         "UseDisplayDevice" "DFP"**
EndSection


6. restart X (this is for Ubuntu)

**sudo /etc/init.d/gdm restart**

As I understand, for some reason, nvidia doesnt registrate monitor.
It is an easy fix, saw other people with same problems (that is how I solved it)
But took me while to find solution.

ah, nice. Glad you got it. Please mark this thread as "SOLVED".

Best,
nikoPSK

---

