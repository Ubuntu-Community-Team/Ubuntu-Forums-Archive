---
title: "How to install 915GM/GMS, 910GML Drivers?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by bitdefuser on 2007-05-21
"Mobile Intel® 915GM/GMS, 910GML Express Chipset Family"
[Link: Linux Drivers (Second one).]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

It's the second one on that link. It's the linux version of the driver. I've downloaded it but, I'm having trouble installing it. How do I install it? :p

---

### Post by psyke83 on 2007-05-21
You don't need those drivers, they're out of date.

Ubuntu already comes with newer drivers (i810) for Intel chipsets, and should already be configured for use on your system. You can ensure 3D support is functioning by pasting the following into a terminal:

```
glxinfo | grep direct
```

---

### Post by bitdefuser on 2007-05-21
Thanks but, I downloaded a driver anyway. It worked. :)
My resolution is now 1400 X 1050. Thanks anyway and also that terminal commanded replied with:
> account@laptop:~$ glxinfo | grep direct
direct rendering: Yes
account@laptop:~$ 
Good, right?

---

### Post by psyke83 on 2007-05-22
bitdefuser,

Yes that's good, as long as you realize that you've installed three-year-old drivers. You can expect breakage.

---

### Post by bitdefuser on 2007-05-22
Aw damn! :( How do I install the new ones?
Edit: While keeping my Resolution?

---

### Post by bitdefuser on 2007-05-22
Bumpie. :(

---

### Post by bitdefuser on 2007-05-22
Another bump. Sorry. >.<

---

### Post by bitdefuser on 2007-05-22
Bumpie. :(

---

### Post by bitdefuser on 2007-05-22
Hello?

---

### Post by psionyk on 2007-05-22
You can install a new version of the driver for your video card (I have the same one) using this:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Seems to work great, direct rendering is enabled, and you don't need to use 915resolution either, it should recognize and keep your widescreen resolution.

Hope this helps! :)

---

### Post by bitdefuser on 2007-05-22
Thank you. It looks like it successfully updated! :)

---

### Post by gregoooooo on 2007-06-05
I recently installed feisty fawn and i only had one option for resolution (1024x768 i believe). This made me think that maybe the proper driver wasn't installed. So i installed the newest driver using apt-get as told above. Now whenever i try to log in it will go to a black screen, then it brings me back to the login screen. I am able to get into the terminal. I'd be happy just to get back the original drivers at this point. I've already removed and reinstalled the drivers several times. I'm basically out of ideas. Any suggestions?

---

### Post by ramjet_1953 on 2007-06-05
One thing to remember with the new driver is that if you want to play any games that change the screen resolution, X will crash and take you back to the login screen.

I found this out the hard way, so I un-installed xserver-xorg-video-intel and re-installed the i810 driver and used the [COLOR="Blue"]915resolution[/COLOR] package to control it.

It works flawlessly for me.

Regards,
Roger :cool:

---

### Post by Bluecircle on 2007-06-05
> **gregoooooo said:**
> I recently installed feisty fawn and i only had one option for resolution (1024x768 i believe). This made me think that maybe the proper driver wasn't installed. So i installed the newest driver using apt-get as told above. Now whenever i try to log in it will go to a black screen, then it brings me back to the login screen. I am able to get into the terminal. I'd be happy just to get back the original drivers at this point. I've already removed and reinstalled the drivers several times. I'm basically out of ideas. Any suggestions?

If the intel driver doesn't work try the i810. on my 1366x768 laptop, the intel drivers log me out and don't work, but the i810 drivers work fine. The exact opposite happens for my 1920x1200 external monitor.

---

### Post by gregoooooo on 2007-06-05
Thanks. I reinstalled the i810 driver and i can get back in now. Is there an easy way to find out what resolution my monitor is capable of? This is something i should probably know but i don't. It's a cheap laptop so i'm guessing it's nothing too impressive. Again, thanks for the help.

---

### Post by ramjet_1953 on 2007-06-05
OK, just download the [COLOR="Blue"]915resolution[/COLOR] package, using Synaptic.

After you have done that, copy and paste this command into a terminal:

[COLOR="Red"]sudo 915resolution -l[/COLOR]

This will give you a list of all available resolutions.

In my experience, it is best to disregard the 32 bit options.

In my case I have a 1280 X 800 widescreen and needed 24 bit colour, so I did the following patch

[COLOR="Red"]sudo 915resolution 30 1280 800 24[/COLOR]

I chose mode 30 to over-write, because it would never be used

I then modified the [COLOR="Blue"]/etc/default/915resolution[/COLOR] file

[COLOR="Red"]gksu gedit /etc/default/915resolution[/COLOR]

When the editor opened, I changed the following settings, to agree with the patch, that I previously made.

[COLOR="Red"]MODE=30
XRESO=1280
YRESO=800
BIT=24[/COLOR]

Then saved the file and re-booted

Of course, you will need to tailor these settings to suit your monitor's native resolution.

Regards,
Roger :cool:

---

### Post by gregoooooo on 2007-06-05
muuuuuuuuuuuuuuuch better. I was looking for the 915resolution package, i didn't think about synaptic. As I'm sure you've figured out I'm quite new to linux but now that i have my wireless and my graphics working it will be much more fun/easy to use i think. Thanks again for your help.

Greg

---

