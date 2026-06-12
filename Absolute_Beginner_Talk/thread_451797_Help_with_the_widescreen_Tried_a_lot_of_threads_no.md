---
title: "Help with the widescreen? Tried a lot of threads nothing helps"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by mr32123 on 2007-05-22
Hey I'm still fairly new to Linux.  I just installed Feisty on my computer and everything is working fine except for the screen resolution.  It is supposed to be 1440 x 900 but there is no option for it.  I messed around in the terminal and I was able to unleash more resolutions, but still no 1440 900.  Can someone please help?  I'm really new to the command line thing so if you could walk me through it it would be a great help!

(The graphics card is an nVidia GeForce4 4200)

---

### Post by Ek0nomik on 2007-05-22
You can simply add the resolution to your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

Than add "1400x900" to each entry.

Or you can run this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and it should detect the highest screen resolution possible.  I just bought 2 new widescreen monitors yesterday and that is how I got them running.

---

### Post by mr32123 on 2007-05-22
Nope.  That didn't work.  The max resolution is still 1024x768

---

### Post by voltagex on 2007-05-22
What kind of computer is this? Do you know what graphics card is in it? If not, type lspci into a Terminal and paste the output here, and I'll try to help.

---

### Post by TheMono on 2007-05-22
OK. Firstly, when you run in a terminal the command 

cat /etc/X11/Xorg.conf

What driver does it say you are using for your graphics card? Is it nv, nvidia, or vesa?

Secondly, what brand monitor?

---

### Post by mr32123 on 2007-05-22
The computer is a Dell.  Pretty old i guess but definately in amazing shape.  its got 1.5 gb ddr-sd, its a P4 2.66 Ghz.  The video card I ripped out of my old computer and it is an nVidia GeForce4 4200.  Ubuntu is installed on the slave drive in a two drive configuration (both IDE).
The monitor is a Norcent 19" (I never heard of them before but it works beautifully under XP (2ms refresh and wonderful colors)

I'll answer the rest of your questions in a minute or two as I had to reinstall ubuntu because i messed up the xorg file somehow (and a 15 minute install is better than fiddling around with code for hours for me)

---

### Post by Ek0nomik on 2007-05-22
Did you manually add the resolution to your xorg.conf file?

---

### Post by homergreg on 2007-05-22
Look and see of you can enable a restricted video card driver in system > administration > restricted drivers manager .   That "might" give you some more options.

---

### Post by mr32123 on 2007-05-22
TheMono: when i run that command it gives me it tells me there is no such file or directory.

Ek0nomik:  Yes and I failed miserably forcing me to reinstall Ubuntu when it no longer booted correctly.

homergreg:  It did give me a few more resolutions but both of them were in the 800's.  I still have no 1440x900.

---

### Post by homergreg on 2007-05-22
Did you try 1280X800?

---

### Post by Ek0nomik on 2007-05-22
> **mr32123 said:**
> TheMono: when i run that command it gives me it tells me there is no such file or directory.

Ek0nomik:  Yes and I failed miserably forcing me to reinstall Ubuntu when it no longer booted correctly.

homergreg:  It did give me a few more resolutions but both of them were in the 800's.  I still have no 1440x900.

You didn't have to reinstall Ubuntu, you simply had to boot into command line and change your xorg.conf file again...

Anyways,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When following that, what did you all put in?  Did you choose your proper video card and use the spacebar to select the resolution(s)?

---

### Post by mr32123 on 2007-05-22
yes I did all of that and it still wouldnt work

---

### Post by Ek0nomik on 2007-05-22
> **mr32123 said:**
> Thats not one of the choices.  The highest it goes is 1024 x768

Dang, I am running out of ideas because that was all I had to do.

In your xorg.conf file, was 1024x768 the highest resolution listed too?

---

### Post by mr32123 on 2007-05-22
No as a metter of fact after I had edited the the xorg file through sudo dpkg-reconfigure -phigh xserver-xorg, it had 1440 listed.  But as soon as I restarted my computer the gui gave me errors

---

### Post by Ek0nomik on 2007-05-22
> **mr32123 said:**
> That is not one of the choices

Post your xorg.conf file.

Also, you ran that command WITH this xorg.conf file in its present state, right?

---

### Post by mr32123 on 2007-05-22
YES!   Ek0nomik I just tried that sudo code again and this time it worked flawlessly.  I guess i pressed something incorrectly before

Thank you for your help and thanks to all that tried to help out!

---

### Post by alienexplorers on 2007-05-22
Try adding this to your xorg.conf monitor section.
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Generic"
    ModelName      "Monitor0"
    HorizSync       30.0 - 70.0
    VertRefresh     60.0 - 120.0
    Option         "UseEDID" "FALSE"
    Option         "IgnoreEDID" "TRUE"
    Modeline "1440x900_70.00"  126.98  1440 1536 1688 1936  900 901 904 937  -HSync +Vsync
    Option         "DPMS"
EndSection

---

### Post by Ek0nomik on 2007-05-22
> **mr32123 said:**
> YES!   Ek0nomik I just tried that sudo code again and this time it worked flawlessly.  I guess i pressed something incorrectly before

Thank you for your help and thanks to all that tried to help out!

Might I ask what you did differently?  Was it because you added resolutions to your xorg.conf file?  Or did you just not select the resolution after running the command or not select nVidia?

---

### Post by mr32123 on 2007-05-22
I guess it was that i didnt properly highlight the resolutions

---

