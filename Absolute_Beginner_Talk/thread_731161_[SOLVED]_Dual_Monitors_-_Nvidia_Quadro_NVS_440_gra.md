---
title: "[SOLVED] Dual Monitors - Nvidia Quadro NVS 440 graphics card"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by mundo on 2008-03-21
I am struggling to get Ubuntu to work with my 2 monitors.  

I go to System>Administration>Screens and Graphics then enter my password. I see the options to enable other screens.  I click on screen 2 then select Generic>LCD Panel 1280x1024 and check the secondary screen option and Extend to right.  However, when I click Test it doesn't do anything.

Could this be a driver issue?  I haven't installed a graphics driver for it yet.

By the way, I used the Nvidia driver in the "Restricted Drivers Manager" but it all went pear shaped.

---

### Post by herbster on 2008-03-21
Your card is supported by the latest driver, 169.12. I'm guessing that's what Ubuntu uses for nvidia-new, so open a terminal and do:

```
sudo apt-get install nvidia-glx-new
```

Then reboot and run "nvidia-settings" and check the X Server Display Configuration tab, looks like this:

[img]http://www.bobgill.net/nvidiasettings.jpg[/img]

I've been using duals for a while, you can definitely get it working.

---

### Post by mundo on 2008-03-22
Thanks for this.  I have followed your instructions but when I launch Nvidia Settings I get this message:

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server

All well and good but as I'm a newbie I don't know how to do what it's asking me to do.

---

### Post by Neo0351 on 2008-03-22
Run 
```
sudo nvidia-xconfig
```

---

### Post by mundo on 2008-03-22
ah ha, thanks, now I have some action and can see that the NVIDIA X Server Settings are now populated with information.

---

### Post by mundo on 2008-03-22
Blimey, I got it to work.  I've only read about 1,000 posts and spent 10 hours getting this to work!

My Nvidia settings screen wasn't quite the same as the screenshot above but I enabled the secondary screen anyway and it came up with a message saying that not all the settings were possible, then I did a restart and it worked!

---

### Post by herbster on 2008-03-22
Yes, mundo, it's funny how really simple it is once you know what you're doing ;) Ain't that always the catch? :D

For your sake, you really want to backup your xorg.conf now since you've got it working right. Just open a terminal and make a tar out of it and email it to yourself and/or copy it to a backup drive. Popping your xorg.conf onto a newly installed linux will save tons of hassle as you only need to then install the driver and boom, all your visuals are taken care of. You can copy it over as such:

```
tar cjf ~/Desktop/xorg.tar.bz2 /etc/X11/xorg.conf
```

Now you have a little archive on your Desktop containing your xorg.conf, which is the file your system reads to load the appropriate visual settings (screen res, monitor[s], etc. etc.) and more. Email it to yourself, copy it to a backup drive, etc. :)

And mark the thread as solved for others :)

---

### Post by mundo on 2008-03-23
Thanks for your help with this Herbster, I have done as you suggested and marked the topic as solved.

---

