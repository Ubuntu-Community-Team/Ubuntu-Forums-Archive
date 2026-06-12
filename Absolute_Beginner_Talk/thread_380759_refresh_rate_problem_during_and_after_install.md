---
title: "refresh rate problem during and after install"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by flensr on 2007-03-10
Hello,

I'm having a huge problem with 6.10 installation.  First, my system:
Athlon 64 X2
2 gig ram
Nvidia 6800GT (AGP)
Dell 1905FP LCD (DVI)
NEC Viewsonic LCD1760V (analog)

On first boot from the CD, the installer sets the wrong refresh rate.  I get the ubuntu splash screen with the progress bar, and then it goes out of range for both monitors.  Trying to use the "safe" video mode installer results in almost the same results, except that my monitor shows a very corrupted image instead of simply going blank after popping up an OSD error for input out of range.  

If I use F4 and set 1280x1024x32 during the first boot, it boots fine, Ubuntu loads, and I can run the whole installer.

After the initial installation though, the first boot to the installed OS gives me the exact same problem.  I get the splash screen and then the refresh rate goes out of range.  Even if I ctrl-alt-f1 and go to a console, the screen is still garbled due to the bad refresh rate.

I have tried editing xorg.conf to manually set the monitor VertRefresh to 60, set a range, went to the mode lines and changed them to things like "1280x1024_60", and I've run the xserver configuration scripts which resulted in a usable command prompt (only 40 lines mode) but the xserver fails to load with an "invalid screen" error.

So basically, the default installation is WORKING FINE except that it's setting a totally unusable refresh rate and I am not able to figure out how to override it during boot and login.  Any help will be appreciated.

flensr

---

### Post by Perfect Storm on 2007-03-10
Have you installed the Nvidia driver?
if so type 
```
nvidia-settings
```
and you'll find alot of stuff you can change.

---

### Post by flensr on 2007-03-10
Update - I ran dpkg-reconfigure xserver-xorg, and selected the vesa driver instead of the auto-detected nv driver.  I runs ok at 1280x1024, but of course it's slow, non-accelerated, etc.

So...  How do I re-try a better nvidia driver?

---

### Post by Perfect Storm on 2007-03-10
```
sudo aptitude install nvidia-glx
sudo nano /etc/X11/xorg.conf
```

Under **Section "Device"** change driver to **"nvidia"**

save <ctrl>+<o> and exit <ctrl>+<x>.
restart X <alt>+<ctrl>+<backspace>

---

### Post by flensr on 2007-03-10
I checked in synaptic package manager and it said that the command to activate nvidia-glx is "sudo nvidia-glx-config enable"...

Will that do the same thing as what you said to do?

---

### Post by Perfect Storm on 2007-03-10
People have reported back that it won't work (a bug). But if it worked it will have same effect as I shown you.

---

### Post by flensr on 2007-03-10
Hmmm nevermind I ran the nvidia-glx-config enable, and it seems to have sort of worked... HOWEVER...

The desktop is now only displayed on my secondary (analog) LCD instead of on both like before.  I would at least like to have the display on my primary (DVI) monitor.  Is there an nvidia control panel to help switch between displays or even activate dual displays?  nvidia-settings does not have any settings for that.

Thanks!

---

### Post by Crooksey on 2007-03-10
```

$ sudo nvidia-xconfig
$ sudo gedit /etc/X11/xorg.cong

```

Now, your device section will look something like..

```

Section "Device"
        Identifier     "NVIDIA Corporation NVIDIA Default Card"
        Driver         "nvidia"
EndSection

```

Now, change it to make it look like....

```

Section "Device"
        Identifier     "NVIDIA Corporation NVIDIA Default Card"
        Driver         "nvidia"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "string" 
	Option "RenderAccel" "True"
	Option "RandRRotation" "True"
	Option "DisableGLXRootClipping" "true"
	Option "BackStoring" "True"

EndSection
```

Save the file and reboot.

---

### Post by Perfect Storm on 2007-03-10
Well, you could try the latest nvidia driver to see if it had that switch, but it require a bit more to install it manually.

You can download the driver here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) save it to your Desktop.
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo aptitude --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
cd Desktop
sudo /etc/init.d/gdm stop (This will take you out of X, so better to write/print down this post)
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm start

```


Edit: Nevermind, seems to be one who knows more about dual screen.

---

### Post by Crooksey on 2007-03-10
Been running Dual screen setups on linux for about 6 months now, getting to know how wasnt fun :(

But when i got my nvidia card it took ~30secs todo!

---

### Post by Perfect Storm on 2007-03-10
> **Crooksey said:**
> Been running Dual screen setups on linux for about 6 months now, getting to know how wasnt fun :(

But when i got my nvidia card it took ~30secs todo!

You know what they say; Live and learn :) 
The only thing I wish is that I can affort dual screen...maybe next year.

---

### Post by flensr on 2007-03-10
Thanks for all the help. I think I have it running satisfactorily.

I have it set up with twinview.  The only major issues are that the initial login screen shows up on my secondary monitor and occasionally some apps will launch in the second monitor as well.  Otherwise though, it's working.  I'm pretty sure the hardware acceleration is working because the 3-d looking screensavers are smooth and fast.

---

