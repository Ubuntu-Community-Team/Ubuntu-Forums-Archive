---
title: "[SOLVED] Nvidia driver 169.12 = blank screen"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Daggo on 2008-03-20
[Resolved] Read post#9
Setup:
EVGA 7950GT (dual dvi Ports)
Xerox xr6-19dw (1 dvi port, 2 crt)

I did a clean install to see if I can get Ubuntu to work with the dvi.
Works well when I am using the "vesa" (default), or the "nv" drivers but with no 3d acceleration. I dual boot and  works 100% in windows so I know it is not a hardware issue. Works with my vga cable + adapter but meh, dvi is much better.

After an installation of the 169.12 nvidia drivers a blank screen appears in the login. so...
I ran sudo dpkg-reconfigure xserver.xorg to get the xorg.conf wizard and input the correct data in. 
blank screen

Tried  sudo nano /etc/X11/xorg.conf and added the line:
Option "UseDisplayDevice" "DFP" 
under the device section and made sure that the driver being used is the "nvidia" one
blank screen  

Tried adding the line:
Option "ConnectedMonitor" "DFP"
which overrides the crt signaling and forces it to use dvi.
blank screen

Attached is my xorg.conf 
I really like ubuntu and want to stick with it so any additional ideas is very appreciated!

edit: forgot to mention that I already tried Envy. Awesome tool but did not help me this time.

---

### Post by StOoZ on 2008-03-20
try using 'Envy' to install these drivers again:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by Therion on 2008-03-20
Sounds like the Black Screen of nVidia Death...  Happened to me too.  You may need to remove the splash srceen and do your system updates (make sure you do them ALL) using the default vesa driver, and then go back and install the Restricted Driver using Envy.  To get the the desktop using the default driver:

Reboot your machine and when you see the GRUB menu, ESCape out.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this particular line.
Delete the words **splash** and **quiet**.
Hit &#8220;Enter&#8221;, then "B" to continue booting.
Once you're in Ubuntu, open up the Terminal and enter:
```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words quiet and splash from the line that starts with Kernel one more time.
Save the file (overwrite), Exit.

Now do your system updates reboot and run Envy to install the Restricted Driver.

You should be good to go at this point.

---

### Post by Daggo on 2008-03-20
-went into the grub menu list and deleted the 'splash' and 'quiet' from the kernel line
-booted into ubuntu using 'vesa' driver
-deleted 'quiet' and 'splash' from menu.lst from terminal
-ran sudo apt-get update
-installed and ran envy 
restarted
blank screen

so I then went into the xorg.conf and added the line Option "UseDisplayDevice" "DFP"
blank screen - also tried Option "ConnectedMonitor" "DFP" -same result

My mobo has an onboard vga+dvi, although I disabled it from the bios im wondering if it may be causing a conflict.

---

### Post by stchman on 2008-03-20
> **Daggo said:**
> Setup:
EVGA 7950GT (dual dvi Ports)
Xerox xr6-19dw (1 dvi port, 2 crt)

I did a clean install to see if I can get Ubuntu to work with the dvi.
Works well when I am using the "vesa" (default), or the "nv" drivers but with no 3d acceleration. I dual boot and  works 100% in windows so I know it is not a hardware issue. Works with my vga cable + adapter but meh, dvi is much better.

After an installation of the 169.12 nvidia drivers a blank screen appears in the login. so...
I ran sudo dpkg-reconfigure xserver.xorg to get the xorg.conf wizard and input the correct data in. 
blank screen

Tried  sudo nano /etc/X11/xorg.conf and added the line:
Option "UseDisplayDevice" "DFP" 
under the device section and made sure that the driver being used is the "nvidia" one
blank screen  

Tried adding the line:
Option "ConnectedMonitor" "DFP"
which overrides the crt signaling and forces it to use dvi.
blank screen

...and the guys from nvidia support stopped contacting me so I guess theres not much hope. :(

Attached is my xorg.conf 
I really like ubuntu and want to stick with it so any additional ideas is very appreciated!

edit: forgot to mention that I already tried Envy. Awesome tool but did not help me this time.

When using Envy tell it to install the nvidia driver manually.  Use Envy 0.9.10 and with manual selection there will be the 169.12 driver there.

Worked for my 8800GT.

---

### Post by Daggo on 2008-03-20
Installed 169.12 driver manual install from envy
blank screen
ran nvidia-xconfig
blank screen

I guess 169.12 hates me or something  *shrugs*

---

### Post by stchman on 2008-03-20
> **Daggo said:**
> Installed 169.12 driver manual install from envy
blank screen
ran nvidia-xconfig
blank screen

I guess 169.12 hates me or something  *shrugs*

Your xorg.conf is very small.  Run this utility.

```
sudo dpkg-reconfigure xserver-xorg
```

See if that fixes your problems.

---

### Post by Daggo on 2008-03-20
-Ran the command, went through the wizard
blank screen

I have attached my new xorg.conf after the wizard
I have also added the lines under screen:

Option "ConnectedMonitor" "DFP"
Option "UseDisplayDevice" "DFP"

I feel I almost have it. soo cloose..

---

### Post by Daggo on 2008-03-22
!Success!

I have figured it out! Hooray! Ok heres what I did for anyone who might have a similar problem. Get comfy this might take a while-

What happened was that at startup the  xorg.conf file automatically tries to detect the EDID from your monitor. The EDID is a configuration file build into the firmware of every monitor so when you plug it in, it automatically tells the video card its capabilities (horizontal sync, vertical sync, size etc...). Thats essentially how plug and play monitors work. 

Anyways, I used a program in Windows called "Powerstrip" which has the ability to retrieve the EDID information from the monitor. I ran it and found I was NOT able to establish a connection to it while I was using my dvi cable. It did however have a connection with my crt/vga cable. What does this mean? It means that during boot time, while I was using my dvi cable, xorg.conf could not retrieve the dvi EDID from my monitor (probably because it doesn't have one) and because of it, could not set the proper dvi display settings.

So...the fix
You need to manually disable xorg.conf from trying to retrieve the EDID from the monitor and specify your own EDID settings.

In your /etc/X11/xorg.conf file add the following lines:


[(Under Section "Device")]
	Option		"ConnectedMonitor" "DFP"
	Option          "UseEdidDpi" "FALSE"
	
*Note: using Option "Connected Monitor" "DFP" will tell it to override what the NVIDIA kernel module detects is connected to your video card. Using Option "UseEdidDpi" "False" disables xorg from detecting the EDID-dpi settings directly from your monitor. 


[(Under Section "Monitor")]
	
	DisplaySize     381 238.125
	Modeline 	"1440x900" 102.81 1440 1520 1672 1904 900 901 904 931
  	
*Note: This part is tricky, you need to figure out the Display size in dpi x dpi. I have a 19" 1440x900 widescreen so...

Here is the equation I used:
Calculate the wanted DisplaySize:
                My resolution is 1440x900
                pixelwidth = 1440
                pixelheigth = 900
                dpi = 96
                formula = pixelwidth/dpi*25.4 and pixelheight/dpi*25.4
                1440/96*25.4 and 900/96*25.4 =
        DisplaySize     381 238.125        <--this goes in your Xorg file under "monitor"

(Equation taken from [http://osdir.com/ml/linux.ubuntu.devel.xubuntu/2006-12/msg00240.html](http://osdir.com/ml/linux.ubuntu.devel.xubuntu/2006-12/msg00240.html))

Next, you need to find your Modeline. I ripped my modeline off this site and got lucky.
[http://www.nightstorm.com/bam/SuSE_92_On_SonyVAIO/XF86Config-dualMonitor](http://www.nightstorm.com/bam/SuSE_92_On_SonyVAIO/XF86Config-dualMonitor)
I just picked the first line I saw that had 1440x900 and put it in my xorg. worked


[(Under Section "Screen")]
	
	Option 		"UseEdidDpi" "FALSE"
	Option          "ExactModeTimingsDVI" "TRUE" 
	Option          "ModeValidation" "DFP-0: AllowNon60HzDFPModes, NoEdidModes, NoVesaModes, NoXServerModes"

*Note: Just add these in. You can read about them from the Nvidia Manual at:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html)
It just tells xorg to not look for the EDID info contained in the monitor.


I recommend before you add any of these lines in, make sure that the problem is that your computer unsuccessfully retrieves EDID information. 

For example: when running 'sudo dpkg-reconfigure xserver.xorg' (which is a wizard to reconfigure your xorg.conf) when it gets to the "Automatically detect Monitor" and you hit 'yes' for it to detect monitor settings, at that point it tries to retrieve the monitors EDID. If it comes up with the manufacturers name or model, your ok, it retrieved your edid, but if it ends up being 'Generic Monitor', then likely you have the same problem I had. Backup your xorg.conf before running this command btw.

If your computer did retrieve the EDID, then probably you only need to add this into your xorg.conf file.
[(Under Section Device)]
     Option "UseDisplayDevice" "DFP"        <--(or DFP-1 if your using your 2nd output slot)

OR...
[(Under Section Device)]
    Option "ConnectedMonitor" "DFP" 


I have also added in my final xorg.conf for you to look at to compare and learn.

For more info refer to the Nvidia Manual:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html)
or contact nvidia support at [email]linux-bugs@nvidia.com[/email]
Special thanks to Roland Hui at Nvidia support for providing me with help and info

---

