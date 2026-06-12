---
title: "install new video card drivers?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by cwm33 on 2007-07-26
I just installed Fiesty Fawn and have been playing with it some.  One thing that's mildly irking me (old windows user, big surprize?) is I'm not sure wether or not I should update the video card drivers, or if the ones installed by default are good enough.  I plan to get a stable configuration up and running, figure out which all programs I would like to use, and hopefully install compiz fusion on it for some sexy desktopness.  Would it be wise to install the latest and greatest video card drivers? or am I better off just with the ones ubuntu installs by default?  My video card is an eVGA Nvidia Geforce 6800GT.

I searched around about video card drivers, and found a more or less definitive guide for installing them, but nothing on if I should bother with upgrading or not.  Any and all help will be much appreciated. :)

---

### Post by SkippyIsForYou on 2007-07-26
i wanted to install the catalyst ones from ATI and i followed the guide exactly, but the GUI for the install didnt pop up when it said it would, so I couldn't get em installed.

So, I'm interested in the same thing. :-P

---

### Post by wolfen69 on 2007-07-26
yes, install the nvidia drivers via restricted drivers manager.

---

### Post by bsharp on 2007-07-26
What I would do is **backup your /etc/X11/xorg.conf file, **install the drivers, if it doesn't work, boot it into recovery mode (or a live cd) and replace it with your backup.  You probably wouldn't have to worry about it not working tho, I have a Nvidia card too with the driver installed it hasn't given me any problems.

---

### Post by jerrynewt on 2007-07-26
What is the command line entry in recovery mode to restore the xorg.conf backup? Just enabled the nvidia driver in restricted drivers and screen went to black and grey lines and grey sploches. thank you for the help.

---

### Post by RomeReactor on 2007-07-26
Hi. It depends on how you backed up the file. What method did you use to make the backup? Please post the output of running this command in the terminal (Applications->Accessories->Terminal):
```
ls /etc/X11
```

---

### Post by David C on 2007-07-26
Hi there,

I'm having the same issue. I've enabled my legacy drivers via "Restricted Drivers Manager" and did a reboot, but now, I am only restricted to 640X480 and 800X600 resolution.

Any ideas?

---

### Post by RomeReactor on 2007-07-26
Hi. What video card do you have? Try running this from the terminal:
```
sudo nvidia-settings
```
this should bring up a settings manager for your nVidia card--if it *is* nVidia...

---

### Post by crjackson on 2007-07-26
> **SkippyIsForYou said:**
> i wanted to install the catalyst ones from ATI and i followed the guide exactly, but the GUI for the install didnt pop up when it said it would, so I couldn't get em installed.

So, I'm interested in the same thing. :-P

I have several machines with ATI cards and it's easy.  I won't hi-jack someone elses thread to explain how to do it though.

Start your own thread and alert me with a PM when you do.  There I'll explain how I do it, but it's not documented anywhere that I know of.  It works everytime for me...

---

### Post by David C on 2007-07-26
> **RomeReactor said:**
> Hi. What video card do you have? Try running this from the terminal:
```
sudo nvidia-settings
```
this should bring up a settings manager for your nVidia card--if it *is* nVidia...
```
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```
:(

---

### Post by RomeReactor on 2007-07-27
What nVidia card do you have? please post the output of this command:
```
sudo lshw -class display
```
Also, you could try to reconfigure your display; but first, make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Now to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
and when it asks you what driver to use, choose **nvidia**. If for any reason you don't like the results and want to revert to the previous configuration, run this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by David C on 2007-07-27
Found the solution to all my problems.

64bits Ubuntu isn't ready yet. I've downgraded to 32bit ubuntu and everything works perfectly now.

---

### Post by Malta paul on 2007-07-27
I find that 'Envy' is great for installing the latest video drivers.
Hope this helps you :wink:
Here is the link [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by andyho on 2007-07-27
I was having the WORST time trying to install my nvidia 5200.. followed this guide [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) for the most part! Step 4 threw me a little since there was no alteration to make until I actually rebooted and the system saw the card?!? I also had the weird screen with black and white lines at one time along with a half dozen other freeze ups and such! All is working great now though!! Good luck!!

---

