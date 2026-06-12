---
title: "Cannot change monitor resolution"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Stall on 2007-09-30
I have attempted to configure the xerver xorg, but it has failed to work. I am running the Dell 19" widescreen, along with a Nvidia 6100 SE video card.

Please help.

---

### Post by Arthur Archnix on 2007-09-30
I'm on my way.

All kidding aside, you're going to have to provide more information. By the sounds of it though, you want help configuring your nvidia card. 

Hopefully you backed up your xorg first. 

Write back with more details about what resolution your trying to achieve, what changes you've made to your xorg, and we'll see what we can do.

---

### Post by Stall on 2007-09-30
I am trying to set up 1440x900 resolution. I also did the who "restricted driver thing" too.

I also did back up xorg, but where do I find the back ups?

And I did the how dpkg-reconfigure xserver-xorg, and followed the instructions on the screen.

But no dice.

my apologizes, I was messing around with themes =D. I am here.

---

### Post by Arthur Archnix on 2007-09-30
No need to worry about the backup right now. As long as you did it we can find it if x breaks.

Let's try installing the nvidia driver ourselves, instead of using the restricted driver manager.

I found this[ website]("http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/"), sounds pretty good. All written out. Easy to follow. Knowing that we got that backup means you should give this a try and if the sheet hits the fan, we'll revert it back, and try again. 

Isn't linux grand?

---

### Post by Stall on 2007-09-30
I will attempt to use this tutorial. I report back shortly if I get any results.

---

### Post by mivo on 2007-09-30
There is also Envy, which might be easier for a first attempt to fix the trouble: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Stall on 2007-09-30
Envy didn't work. I still cannot change my resolution beyond 1024x768.

When I hit alt + ctrl + F7 in the no gpm, I couldn't type anything.

=( I really want to use Ubuntu in the right resolution.

---

### Post by Stall on 2007-09-30
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA 6100SE nForce 430"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

This is what I have in my xorg. But I still cannot access 1440x900 in the resolution menu under system - preferences.

---

### Post by Alpha010203 on 2007-09-30
Hi, I'm an extremely new user to Ubuntu myself, and had found myself with your problem as well.  Below are the steps I used to solve my problem, even though it might be a bit rudimentary:

1. Enable the experimental desktop effect (doing this will enable the experimental nVidia graphic driver)
2. Open up the terminal and type : nvidia-settings
3. Once the graphical control panel for Nvidia opens up, I think you will see 1440x900 as an option
4. chose the option and click apply, don't forget to change refresh rate from 57-60hz.

Good luck,

---

### Post by alienexplorers on 2007-09-30
When running nvidia-settings remember to run it with the sudo prefix or your changes will not be saved.   The command should look like this:
> gksudo nvidia-settings
Remember to click apply and click on save x configuration file.
Exit nvidia-settings and reboot.

---

### Post by Alpha010203 on 2007-09-30
^^^^^Thank you for that, I knew I was missing something:)

---

### Post by nowshining on 2007-09-30
alien with the new .19 drivers I myself found out that i didn't have to sudo the settings, but maybe it was just me also by default I just hit quit and it saved fine for me. :) except for of course the other settings I had to do myself and posted a thread on how to keep the nvidia-settings on reboot.

edit: by the way the resolution should keep but the other settings such as anti-aliasing, etc. will not stay on reboot.

---

### Post by Stall on 2007-09-30
Ok. Opening, changing, and setting all the options to nvidia settings are able to change the resolution fine. However, once I reboot, all of the settings revert to default.

It appears that everything has also saved in my X11.conf

---

### Post by Stall on 2007-09-30
bump.

Please. Nothing seems to be working.

---

### Post by alienatom on 2007-09-30
I was having a similar issues with my widescreen.  I used this link here and it worked super.

[http://ubuntuforums.org/showthread.php?t=560247&highlight=1440x900](http://ubuntuforums.org/showthread.php?t=560247&highlight=1440x900)

---

### Post by Stall on 2007-09-30
> **alienatom said:**
> I was having a similar issues with my widescreen.  I used this link here and it worked super.

[http://ubuntuforums.org/showthread.php?t=560247&highlight=1440x900](http://ubuntuforums.org/showthread.php?t=560247&highlight=1440x900)

I love you.

It worked. Thank you.

---

### Post by nowshining on 2007-09-30
> **Stall said:**
> Ok. Opening, changing, and setting all the options to nvidia settings are able to change the resolution fine. However, once I reboot, all of the settings revert to default.

It appears that everything has also saved in my X11.conf

go into my profile and find all threads started by me and from there find one not exactly titled - how to keep nvidia-settings on reboot well the reboot part won't work but logging into ur session is when all will take effect of course. :)

---

