---
title: "How do I install Nvidia drivers?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-03
I just installed Edgy Eft (my first time ever using Linux) and it seems the entire screen was shifted to the right (leaving a three inch band of blackness on the left side of the screen and the same amount cut off on the right). I was able to manually adjust my monitor a couple inches to the left, but I still have about another inch to go. Also, the height is slightly over sized so that the bottom toolbar is cut off my screen. I can adjust this manually with monitor adjustments, but then the top of the toolbar is cut off. Any suggestions? I checked out 'Monitor & Display' and 'Appearance' under 'System Settings' but I didn't see where I could adjust the screen. I'm using Windows XP on the same hard drive without this problem.  Does anyone know how I can fix this? Thanks.

---

### Post by xopher on 2007-04-03
What graphics card are you using? And what drivers?

Installing ATI/NVIDIA-proprietary drivers might fix this.

---

### Post by x-ray vision on 2007-04-03
NVIDIA GeForce2 MX/MX 400 (six year old Gateway computer)

I have no idea about what drivers I'm using? :confused: 

I have no idea how to do anything in Linux yet; I'm just getting my feet wet. If I go to Gateway's site, will I be able to download and install the drivers for my computer the same way I do in Windows?

---

### Post by x-ray vision on 2007-04-03
I just installed Edgy Eft and I'm totally new at this.

I'm having problems with my desktop being shifted several inches o the right, and I'm hoping installing video drivers will fix this.

My graphics card is an NVIDIA GeForce2 MX/MX 400 (six year old Gateway computer).

I believe I found the correct driver on NVIDIA's website (Linux Display Driver - x86

Version: 1.0-9755) and the instructions for installing says:

**Type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.**

Where do I type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run"?

---

### Post by NeoLithium on 2007-04-03
You can click on Applications -> Accessories -> Terminal
That will pop a window open that will allow you to type that command in :)

---

### Post by jvc26 on 2007-04-03
It might be easier to use the envy script to install the drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Il

---

### Post by x-ray vision on 2007-04-03
Hmm, I'm getting the message: **Can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run**

Does that mean I might have chosen the incorrect driver or am I doing something else wrong?

---

### Post by x-ray vision on 2007-04-03
> **Illuvator said:**
> It might be easier to use the envy script to install the drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Il

Okay, I'll try that.

---

### Post by x-ray vision on 2007-04-03
> **Illuvator said:**
> It might be easier to use the envy script to install the drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Il
I got this message when I tried to open the download:

**Error: Dependency is not satisfiable: module assistant**

---

### Post by jhenager on 2007-04-03
You can also use Automatix to do that. It might also be available through Add/Remove.

---

### Post by x-ray vision on 2007-04-03
> **Illuvator said:**
> It might be easier to use the envy script to install the drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Il

Okay, I followed the directions on Envy's website and hopefully I did it right. How do I check to see if the new driver is installed?

---

### Post by jkeyes0 on 2007-04-03
If it's installed right, it should show an Nvidia splash screen on startup.

Not owning an nvidia card, that's about all i've heard. :)

---

### Post by Terl on 2007-04-03
Did you restart X after you installed it?  If not hit ctrl-alt-backspace.  You should see an nVidia screen if all went right.

---

### Post by x-ray vision on 2007-04-03
Awesome! I restarted the pc and I saw the splash screen.

Not so awesome: I still have a problem with my screen being shifted to the right. I'll post about that downloading video drivers didn't work in the thread i started about it.

---

### Post by x-ray vision on 2007-04-03
Well, I installed NVIDIA drivers (I hope the right ones?) and it didn't fix my screen problem. Any ideas what to try next?

---

### Post by r4ik on 2007-04-03
Never mind me,
Try hit you're cursor to the right.

---

### Post by Scribbler on 2007-04-03
This has always worked best for me:

Open your terminal and type (copy & paste) in:

[FONT="Courier New"]sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable[/FONT]

Remember, with "sudo" you'll be prompted to type in your password.

Then restart Gnome (ctrl+alt+backspace)

If there's no change, open your terminal and type (copy & paste) in:

[FONT="Courier New"]sudo gedit /etc/X11/xorg.conf[/FONT]

In the text page that opens, scroll down and look for Section "Device" and next to where it says Driver, change to "nvidia" (yes, with quotes).

Then save, close, and restart Gnome again. That should do it.

---

### Post by Feba on 2007-04-03
try adjusting your monitor. My BIOs has a tendancy to be off the left side of the screen, I press right on "FUNCTION" (Sceptre Monitor) and it aligns...of course, then I have to align it back for the OS. so I don't really bother, but you get my point

---

### Post by x-ray vision on 2007-04-04
Anyone?

---

### Post by Feba on 2007-04-04
same thing happens to me, also on an MX440, however letting the monitor auto-adjust fixes it.

---

### Post by x-ray vision on 2007-04-04
bump

---

### Post by x-ray vision on 2007-04-04
I just installed Edgy Eft (my first time ever using Linux) and it seems the entire screen was shifted to the right (leaving a three inch band of blackness on the left side of the screen and the same amount cut off on the right). I was able to manually adjust my monitor a couple inches to the left, but I still have about another inch to go. Also, the height is slightly over sized so that the bottom toolbar is cut off my screen. I can adjust this manually with monitor adjustments, but then the top of the toolbar is cut off. Any suggestions? I checked out 'Monitor & Display' and 'Appearance' under 'System Settings' but I didn't see where I could adjust the screen. I'm using Windows XP on the same hard drive without this problem. Does anyone know how I can fix this? Thanks.

---

### Post by brentoboy on 2007-04-04
If you are willing to get your hands a little dirty, I believe I can help you.

Often times, when Linux bumps into a monitor that it doesn't a spec for, it assigns it some safe default values for things like horizontal and vertical refresh rates.   These values generally work, so noone cares if their screen could be refreshing more rapidly.

the offset of the image on the screen is a result of the speed that the little needles in the back are moving relative to the expected speed that the manufacturer optimized for.  You just happen to have a situation where the difference is more than just "noticeable."

So, the fix.  Find the exact model number of your monitor. (usually on the back, sometimes even on the front of the monitor).  And do a Google search.  Hopefully, the manufacturer's site will be fairly high on the list of hits, you need to find the exact refresh rates of your monitor, as well as the maximum resolutions and all that sort of technical stuff.

For instance, I have a CTX model 3L9,  a google search brings me here...
[http://www.abestpc.com/parts/monitor/crt/crt-19-ctx.htm](http://www.abestpc.com/parts/monitor/crt/crt-19-ctx.htm)
and I this info:

Frequency Range
Horizontal: 30-95kHz
Vertical: 50-160Hz

Screen Resolutions
1600 x 1200 @ 75Hz,   1280 x 1024 @ 85Hz
1024 x 768 @ 117Hz,    800 x 600 @ 150Hz

Note:  That is for my monitor, NOT YOURS.  but, you can find that same stuff for yours.

Once you know the refresh rates and screen resolutions, you are armed and ready to go into battle.

open a command prompt, and run this:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo gedit /etc/X11/xorg.conf

```
notice: the X is capital in X11
The first line saves a backup copy
The second line opens the file for you.

find the refresh rates, and fix them.  they are probably significantly lower than what they could be.

you might also find the section where it lists all the available resolutions.  You could add the ones you know are supported by your monitor. (and remove the ones you dont want)

save the file
restart  (you can either restart the whole computer, or you can restart X, which ever makes you happier.)  If you want to avoid rebooting everything you can do this:

press ctrl + alt + F1
login to the text console and run this

```

sudo /etc/init.d/gdm restart

```
(if you have kubuntu, you should switch gdm for kdm)

that should do it for you.

---

