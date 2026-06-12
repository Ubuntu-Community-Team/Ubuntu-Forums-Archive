---
title: "Screen resolution issue"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ausbun on 2006-10-06
I am trying to install Ubuntu from a CD onto my 4-yr-old Compaq Presario, on which I just replaced the hard drive. (There's no OS on the drive, presently) I have been able to run Ubuntu from the CD easily, but the system only allows me to run my screen in 480x640 resolution. I have a 20-inch Samsung LCD, so you can imagine how large everything is. When I found the window to change the resolution, the only choice it gave me was the 640x480; no others. 

My problem is that when I try to install Ubuntu on my hard drive, the first window comes up for language selection and there is no scroll bar to move the page down to the bottom where I assume the button is to move on to the next page. I'm stuck! 

If anyone has any suggestions on the resolution problem or the installation, I will be most appreciative.

---

### Post by bodhi.zazen on 2006-10-06
Try this:

[[color=darkblue]Bodhi's Resolution Solution[/color]](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by ausbun on 2006-10-10
Thanks for the help. That got me to the screen with all my hardware info, but it showed the correct brand of monitor and a large variety of screen resolutions, including the optimal one, 1600x1200.

I did change was the monitor type, to UXGA, but that didn't help. When I tried to save the changes, I got a restart. I didn't think that was correct, but I didn't have enough time to go back into the config.

Any other suggestions to get it to recognize the monitor capabilities that it has stored inside its config file?

---

### Post by halitech on 2006-10-10
when you were looking at the screen resolutions, were there X's beside any other then 640x480?

---

### Post by ausbun on 2006-10-10
I don't remember. I'll try to get the window back open. I take it that there should be an X beside all available resolutions?

---

### Post by halitech on 2006-10-10
yes, if there is an X beside it, means it is availble for use on your desktop.

---

### Post by ausbun on 2006-10-10
None of the screen resolutions have an X beside them.

It doesn't show anywhere to enter the horizontal and vertical refresh modes, either. (I have the info.)

It does show the depth as 24, however.

---

### Post by halitech on 2006-10-10
have you followed bodhi's instructions? if you do, when you get to the escreen where it shows the resolutions, simply put checks next to the ones you want and reboot when done the setup and it should work

---

### Post by CatKiller on 2006-10-10
If you're still in the Live cd environment, then it won't keep your settings when you reboot. **Ctrl-Alt-Backspace** will restart X with your modified settings.

---

### Post by ausbun on 2006-10-10
I have installed Ubuntu on my hard drive now, so I'm not running the CD any more. 

I had emailed Samsung for some support over the weekend and got this message today: " Regarding Linux, your product should work fine on the Linux operating system, however, Samsung neither produces or (sic) offers support for Linux." For what it's worth...

---

### Post by xrchris on 2006-10-10
Which GPU card (and model) does your machine use Nvidia, Intel, ATI?

---

### Post by ausbun on 2006-10-10
Here's all I  get when I do: sudo nano /etc/x11/xorg.conf :

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection


Then it goes into the next section: 

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVCrush11 [GeForce2 MX Integrat$        Monitor         "SyncMaster"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x86$        EndSubSection
EndSection


You may note that it's cutting off the ends of the long lines with the $ symbols; this is a screen function of the low resolution that I've been trying to correct. Each of the lines that is cut off with a $ sign continues on to say:

 "1024x768" "832x624" "800x600" "720x400" "640x480"

I was able to change the default depth to 16 last night. I have tried, as the above posts suggest, putting an X beside the resolutions, but those changes won't save when I CTRL-ALT-BACKSPACE.

---

### Post by CatKiller on 2006-10-10
The talk of the Xes next to resolutions is for when you run the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` This will let you select the driver, resolutions and so on.

Editing your xorg.conf is a different kettle of fish altogether. Per bodhi's guide, you should try putting appropriate HorizSync and VertRefresh values into the Monitor section. Save the file, and then restart X

---

### Post by ausbun on 2006-10-10
Thanks. I'm trying that now.

---

### Post by ausbun on 2006-10-10
It worked!

When I rebooted after the "sudo nano" command, my 1600x1200 resolution returned!

Thanks for all your help, forum members!

---

### Post by CatKiller on 2006-10-10
Excellent. Good to hear that you got it working.

---

