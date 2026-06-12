---
title: "Video card"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by whiteraven on 2007-10-10
Just being a bit lazy and trying to avoid shutting the computer down to open the case and look, but is there any other way other than using "lspci" to return the make and model of my video card?

lspci output:
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)

I don't think this is enough to determine the right driver to download from nVidia. I'm running 64-bit Feisty on an Intel 2.8 GHz dual core and the nVidia site recommends to download the _[NVIDIA-Linux-x86_64-100.14.19-pkg2.run]("http://www.nvidia.com/object/linux_display_amd64_100.14.19.html")_ from this location _[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")_

Thanks in advance!

---

### Post by chrisTGc on 2007-10-10
Hi,

You could take a look at System>Preferences>Hardware Information and scroll down to your video card.There is an advanced tab and would think you are likely to get more info than you have presently.And take a look at /etc/X11/xorg.conf (right click that file and choose view NOT run) and look over the section 'device' associated with your video card to see what X11 has configured,may give you a little more info.

Also there is information available re tweaking video card settings.Mine is an ATI Radeon 7000 and i have used the info on Xfree86 to get a teriffic increase in frame rates,approx as follows,

standard Ubuntu Xorg configuration 350 frames per second with glxgears in terminal
tweaked using advice from Xfree86 re radeon 700 fps
same settings in xorg.conf but installed the latest X11 radeon driver (not the ATI one if it exists -dunno) 900 fps.
 
Best Wishes Chris.

---

### Post by overdrank on 2007-10-10
> **whiteraven said:**
> Just being a bit lazy and trying to avoid shutting the computer down to open the case and look, but is there any other way other than using "lspci" to return the make and model of my video card?

lspci output:
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)

I don't think this is enough to determine the right driver to download from nVidia. I'm running 64-bit Feisty on an Intel 2.8 GHz dual core and the nVidia site recommends to download the _[NVIDIA-Linux-x86_64-100.14.19-pkg2.run]("http://www.nvidia.com/object/linux_display_amd64_100.14.19.html")_ from this location _[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")_

Thanks in advance!

Hi you could always try and update your pci ids
```
sudo update-pciids
```

---

### Post by whiteraven on 2007-10-10
Thank you for the suggestions... I'll get back with the results.

By the way, I find these Ubuntu forums to be very helpful and prompt despite some of the threads that state the contrary. Great work community - hope to be learned enough someday to contribute and pass it forward so to speak!

---

### Post by chrisTGc on 2007-10-11
Hi,

Glad you going to check for info.I thought i might add;

If you are anything like me there is a chance of tweaking your existing nv (probally what X has configured) driver a bit hard or doing the same on a nVidia one you install.Always back up your original xorg.conf file,may be needed if you end up with 'no screens found' by X.

The quickest way i found of optimising the xorg.conf file was by booting up in recovery mode and useing nano,ie, nano /etc/X11/xorg.conf from the command line.then GDM to start X and the graphical login.

Good luck.

---

