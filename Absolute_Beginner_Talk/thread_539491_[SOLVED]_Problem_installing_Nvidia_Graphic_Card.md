---
title: "[SOLVED] Problem installing Nvidia Graphic Card"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by jenson on 2007-08-31
Dear all,

Recently I have tried to install Google Earth, however, Google Earth prompt me to install my NVidia GeForce Go 5200 graphic card driver before I can proceed on installing Google Earth. Thus, I go to NVidia website and download the latest driver recommended for Linux and at first it's extracting well, when it's loading half way to install, it's telling me I need to login to root to install. 

Can I avoid enabling the root account and install from there but install with my current account instead?

Or is there any command that I left out? I follow strictly to the instructions found on the NVidia website.

Thanks.

Regards,
Jenson

---

### Post by Celegorm on 2007-08-31
There's an easier way to get the driver working. Look for restricted drivers management under either system or preferences. As far as the root account, anytime you need root access, simply type "sudo" in front of whatever command needs to be run as root (in the terminal, thats under applications->accessories->terminal), or "gksudo progname" to launch a program with root privileges, and then give it your password when it asks.

---

### Post by svalding on 2007-08-31
You'll find most times in linux that you will be required to become root to install anything to your system. 

As the previous poster mentioned, the easiest way to do this is to type 
```
 sudo <program> 
``` in the terminal window and suppy your root password when it asks. This will allow the driver to install to your system, without incident.

---

### Post by alienexplorers on 2007-08-31
The easiest way to install your nvidia graphics card is to use the ENVY script located at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Geekberg on 2007-08-31
You should be able to install the Nvidia drivers, and Nvidia restricted drivers in Synaptec package manager.  Then you will be able to access the Nvida control panel from your system menu or adminstrative tools and adjust the settings in the restricted drivers management.  

I would install the drivers this way instead of from OEM, this is how I enabled the features on my Nvidia Geforce FX 5800.

************************************************************
You can also try installing automatix instead of using the Synaptec manager. 

Automatix2 comes with a graphical interface, but in order to install Automatix2 there are a few steps we have to do on the command line. Go to Applications > Accessories > Terminal to open a command line window.

In the command line window, type in the following commands to install Automatix, then install the drivers. 

echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list

You might have to provide your password. Afterwards, run

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key

gpg --export --armor E23C5FC3 | sudo apt-key add -

and update the packages database: 

sudo apt-get update

Finally, install Automatix: 

sudo apt-get install automatix2

  Here is a link for help with automatix

[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6)

---

### Post by jenson on 2007-08-31
OMG, now I'm running on the LiveCD I just received from Canonical as I have somehow corrupted the X server. I follow the step by going to System, then Administration, then Restricted Driver Manager, I saw the NVidia graphic driver, and they prompt me to decide whether to enable it. And of course I enable it, upon completing the installation, I was prompted to restart the system.

After reboot it's telling me I cant start X-server. Oh no, now I'm stuck here...anyway to recover it? T_T

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-08-31
If you get into CLI (command interface):

```

sudo nano /etc/X11/xorg.conf

```

go to Section "Device"
and Driver  "nvidia" to "nv"

save (ctrl)+(o) and exit (ctrl)+(x)

---

### Post by jenson on 2007-08-31
> **Artificial Intelligence said:**
> If you get into CLI (command interface):

```

sudo nano /etc/X11/xorg.conf

```

go to Section "Device"
and Driver  "nvidia" to "nv"

save (ctrl)+(o) and exit (ctrl)+(x)

Hi Arficial Intelligence,

I will give it a try. so the first line sudo nano is to open the xorg file to edit?

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-08-31
yes the first line allow you to edit the xorg file from CLI.

---

### Post by Hospadar on 2007-08-31
Hey there! fear not, this is a common issue and is easily solved.  First off, just to get back into a GUI, the easiest way to do it would probably be to, on the command line ```
sudo dpkg-reconfigure xserver-xorg
```  you'll get a big ugly script thing, on the very first page there is a driver selection, you'll notice I suspect if you scroll down that the "nvidia" drivers are selected.

This means that the x-server is attempting to load the proprietary nvidia drivers you installed but something is not right with them.  So: you'll want to switch back to the default open source nvidia drivers by using space to select the "nv" option on this page.  then you can just default your way through the rest of the pages.  then restart your xserver with a ```
sudo /etc/init.d/gdm restart
```Now, assuming you are back in your desktop, go to Applications->add/remove and in the upper right corner select "all available applications" from the drop down menu then search for "envy" and install it.

**EDIT: all of the above can also be done with editing you xorg.conf as described above, so if that worked for you, then no biggie., also with either of these methods, don't do them off the livecd, do them off the terminal you get after x fails to start.**


Now, let's go back to the terminal and use envy to install the proprietary drivers and get your x config all set up properly.  do a ctrl-alt-F1 to get a text terminal (ctrl-alt-F7 get's back to gnome) and enter ```
sudo envy -t
```  this will open up a little dialog, use this tool to remove and clean the nvidia drivers, then install the nvidia drivers.  It will ask you if it can edit xorg.conf and restart gnome, you should let it do so.  Ideally this will then work just fine.  

To test it out, open up a terminal and type "glxgears" the gears shoud look smooth (not choppy).

Now you should be able to install google earth no problem

---

### Post by stchman on 2007-08-31
> **jenson said:**
> Dear all,

Recently I have tried to install Google Earth, however, Google Earth prompt me to install my NVidia GeForce Go 5200 graphic card driver before I can proceed on installing Google Earth. Thus, I go to NVidia website and download the latest driver recommended for Linux and at first it's extracting well, when it's loading half way to install, it's telling me I need to login to root to install. 

Can I avoid enabling the root account and install from there but install with my current account instead?

Or is there any command that I left out? I follow strictly to the instructions found on the NVidia website.

Thanks.

Regards,
Jenson

Best and easiest is to just enable the Restricted Driver for Nvidia.  Go to System--->Administration--->Restricted Driver Manager and enable the Nvidia driver and reboot.

Viola'

---

### Post by jenson on 2007-08-31
> **stchman said:**
> Best and easiest is to just enable the Restricted Driver for Nvidia.  Go to System--->Administration--->Restricted Driver Manager and enable the Nvidia driver and reboot.

Viola'

well, this way make my x-server failed to load properly. So I think I have no luck with that, not sure why. I will try the other way now.

I think I somehow cock it up again. I will repeat the step in CLI again. Gosh, third time have to do somehting in CLI, hopefully it will work. First time it works, but the resolution has some problem, so I follow the second solution to reconfigure the x-server, and then again, failed to load x-server. So now I need to do a complete reconfigure in CLI and see the outcome. Sigh..

Regards,
Jenson

---

### Post by jenson on 2007-08-31
> **Hospadar said:**
> Hey there! fear not, this is a common issue and is easily solved.  First off, just to get back into a GUI, the easiest way to do it would probably be to, on the command line ```
sudo dpkg-reconfigure xserver-xorg
```  you'll get a big ugly script thing, on the very first page there is a driver selection, you'll notice I suspect if you scroll down that the "nvidia" drivers are selected.

This means that the x-server is attempting to load the proprietary nvidia drivers you installed but something is not right with them.  So: you'll want to switch back to the default open source nvidia drivers by using space to select the "nv" option on this page.  then you can just default your way through the rest of the pages.  then restart your xserver with a ```
sudo /etc/init.d/gdm restart
```Now, assuming you are back in your desktop, go to Applications->add/remove and in the upper right corner select "all available applications" from the drop down menu then search for "envy" and install it.

**EDIT: all of the above can also be done with editing you xorg.conf as described above, so if that worked for you, then no biggie., also with either of these methods, don't do them off the livecd, do them off the terminal you get after x fails to start.**


Now, let's go back to the terminal and use envy to install the proprietary drivers and get your x config all set up properly.  do a ctrl-alt-F1 to get a text terminal (ctrl-alt-F7 get's back to gnome) and enter ```
sudo envy -t
```  this will open up a little dialog, use this tool to remove and clean the nvidia drivers, then install the nvidia drivers.  It will ask you if it can edit xorg.conf and restart gnome, you should let it do so.  Ideally this will then work just fine.  

To test it out, open up a terminal and type "glxgears" the gears shoud look smooth (not choppy).

Now you should be able to install google earth no problem

Now i'm back in GUI mode, however, my graphic seems to have problem now. I can't see the text clearly, and the image are just so cocky right now. This is terrible. I can't find the Envy in Sypnatic Package Manager though, do a search return nothing >.<"

Gosh.

Regards,
Jenson

---

### Post by jenson on 2007-08-31
i just downloaded it from the official website and installing it right now, hopefully it work out. so do I still issue Sudo envy -t after successfully installing it?

---

### Post by jenson on 2007-08-31
Ok, I just notice I can't go back to 1280 x 800 screen resolution now. It just makes the whole screen very blur and unpleasant to look at. My images look so funny now. Sigh...

---

### Post by Perfect Storm on 2007-08-31
I don't use Envy so I can't help you there.

When you installed the nvidia driver
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

Was the driver in the xorg.conf changed from "nv" to "nvidia"?

If the nvidia driver works perfectly it will most cases solve your resolution problem.

---

### Post by jenson on 2007-08-31
> **Artificial Intelligence said:**
> I don't use Envy so I can't help you there.

When you installed the nvidia driver
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

Was the driver in the xorg.conf changed from "nv" to "nvidia"?

If the nvidia driver works perfectly it will most cases solve your resolution problem.

Now the driver doesnt work even though it's changed to NV, it simple doesnt work if it is "nvidia", but once I login to the GUI by changing nvidia to nv, and reconfgure the xserver, it seems that the problem become worse? I'm not so sure. But to answer your questions, yes, when I run those commands, it changed from "nv" to "nvidia"

But at least now I dont think I can even boot into GUI mode, I can only boot into CLI right now...gosh...

Someone helps me please? Headache, and I hate to boot into that stupid Windows XP.

Oh, and the download not working anymore, the download speed become ultra slow, not sure whether is it due to my reconfiguration? Hm..and it's not in supported screen resolution, thus, make everything worse.. Does reinstall work? I mean does reinstall help to recover my Ubuntu and keep my files intact?

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-01
Change the driver to "vesa"
please post your xorg when in X (gui)
```
cat /etc/X11/xorg.conf
```

---

### Post by Club17 on 2007-09-01
Thank you Geekberg & Artificial Intelligence. Both solutions works. Have now desktop effects without Xserver crashe at login. :)

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> Change the driver to "vesa"
please post your xorg when in X (gui)
```
cat /etc/X11/xorg.conf
```

Hi AI,

It's working now but however, it does not support 1280 x 800 screen resolution. Hmm.. btw, here is my xorg config content:

```
jenson@Admin:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA GeForce FX Go 5200"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce FX Go 5200"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

Thanks.

Regards,
Jenson

---

### Post by jenson on 2007-09-01
Now I'm defaulted to 1024x768 hmm..I wonder how can I go back to 1280 x 800 with the correct refresh rate? When I try to change it, I can only see the max is 1024x768 which is available for me right now, other is lower resolution choices.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-01
Do you have your monitor specs? (usually found in its manual).

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> Do you have your monitor specs? (usually found in its manual).

what kind of spec? I'm using Toshiba Satellite M30 notebook computer, with 15.4" Wide screen LCD monitor. How to check the monitor spec? it's 60Hz refresh rate in Windows XP if I'm not wrong. the LCD monitor driver should be generic one?

Wait I will have to check the spec for the LCD monitor of the notebook computer and update here.

Thanks.

Regards,
Jenson

**EDIT**: Alright, don't think i can find anything about the LCD (TFT) monitor, since it's those generic type. The only problem should be the graphic driver now I suppose? Have to check which one support 1280 x 800 resolution. Hmm...

---

### Post by Perfect Storm on 2007-09-01
Okay, before we try something else try this:

```
gksudo nvidia-settings
```

go to **X Server Display Configuration** and set your resolution (this may take effect when restarting X).

---

### Post by jenson on 2007-09-01
```

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```

Above is all that I get after running the command, since the graphic driver is set to vesa?

I did see the window, but I cant locate the config, I attached the image for you here, please see the file attached.

---

### Post by jenson on 2007-09-01
btw, I tried sudo nvidia-glx-config enable, and they will automatically configure for me, is that right? But I'm not sure whether that will corrupt my X Server again or not.Thus, I don't dare to do a reboot right now.

Regards,
Jenson

**Edit:** After doing this, I run your command again to get the Nvidia Settings, it gives me the same error message I quoted for you in my previous reply.

---

### Post by Perfect Storm on 2007-09-01
Yeah, you must set the driver back to nvidia.

Hmm....the option in nvidia-settings must be on the newer driver.

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> Yeah, you must set the driver back to nvidia.

Hmm....the option in nvidia-settings must be on the newer driver.

Hi AI,

Do you mean I have to install nvidia-glx-new instead, from Synaptic Package Manager?

Thanks.

Regards,
Jenson

**EDIT:** Do I need to do a restart now? Since I'm requested to restart X server.

---

### Post by Perfect Storm on 2007-09-01
If it go wrong just do as last time change the driver back to vesa in Xorg



I'm going to read up on your nvidia card....so hold on.

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> If it go wrong just do as last time change the driver back to vesa in Xorg



I'm going to read up on your nvidia card....so hold on.

Ok, I will do it right now =)

Thanks for all the helps AI =)

I will update you for the progress later ;)

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-01
Ok, it seems there's a lot of trouble with the NVIDIA GeForce FX Go 5200 card. The solution I found was to get the latest driver. (should be solved in the next release of ubuntu, late oct.)

If you're fresh to do some command work, I'll guide you.

---

### Post by Perfect Storm on 2007-09-01
OK , download NVIDIA-Linux-x86-100.14.11-pkg1.run from here [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) to your Desktop.

```
sudo nano /etc/default/linux-restricted-modules-common
```

change **DISABLED_MODULES=""** to **DISABLED_MODULES="nv"**

```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.00.14.11-pkg1.run
sudo /etc/init.d/gdm start
```

Note that gdm stop command will take you out of X and you'll be in CLI only. So you might print it out.

---

### Post by jenson on 2007-09-01
Cool! By installing the new nvidia-glx-new driver, it works perfectly for me, even with the Restricted Nvidia Driver enabled automatically to make the graphic card working now. Nice man! Thanks for the great helps, AI, I don't even need to use any other third party application to configure it.

I will try whether I can install Google Earth later :lolflag:

Btw, does that mean I might miss out my audio driver too? Since Nvidia is not configured properly. Hmm..I remember my driver is somehting like AC97 driver or what.

Thanks.

Regards,
Jenson

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> OK , download NVIDIA-Linux-x86-100.14.11-pkg1.run from here [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) to your Desktop.

```
sudo nano /etc/default/linux-restricted-modules-common
```

change **DISABLED_MODULES=""** to **DISABLED_MODULES="nv"**

```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.00.14.11-pkg1.run
sudo /etc/init.d/gdm start
```

Note that gdm stop command will take you out of X and you'll be in CLI only. So you might print it out.

Hi AI,

So this will try to see whether it can make my NVIDIA graphic card works close to 100% with Ubuntu Feisty Fawn?

I will now try to do it according to your commands given.

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-01
You don't have sound on Ubuntu?


By the way, using the latest driver from nvidia, when ubuntu kernel get patch you might need to run the nvidia installer again.

---

### Post by Perfect Storm on 2007-09-01
> **jenson said:**
> Hi AI,

So this will try to see whether it can make my NVIDIA graphic card works close to 100% with Ubuntu Feisty Fawn?

I will now try to do it according to your commands given.

Thanks.

Regards,
Jenson

It should (well at least with my card ;) )

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> You don't have sound on Ubuntu?


By the way, using the latest driver from nvidia, when ubuntu kernel get patch you might need to run the nvidia installer again.

I have sound right here, just not sure whether by installing it would make any improvement on sound quality or not. But well, all my mp3 and the music player are serving me right, so I don't think I need to even bother about the sound driver?

I will now proceed to running your commands now.

Stay tuned! Haha...

Regards,
jenson

---

### Post by jenson on 2007-09-01
Oooh..it takes some time to finish all those things you asked me to do, including downloading and installing them.. I will follow strictly and wait for the outcome. You should be able to see the outcome soon.

Hope this thread will help others who are having same or similar problems like me too >.< "

---

### Post by jenson on 2007-09-01
btw, here is the screenshot for the nvidia settings before I run those command, it is working right now..I'm still downloading the files in Terminal.

---

### Post by Perfect Storm on 2007-09-01
When the problem is solved, you should check my tips and tricks regarding eyecandy:

[http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html](http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html)

and 

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> When the problem is solved, you should check my tips and tricks regarding eyecandy:

[http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html](http://polarbeardk.blogspot.com/2006/11/gnome-eyecandy.html)

and 

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

Hi AI,

I always like to learn how to tweak my Ubuntu, so I would not miss out your tutorials ;)

Btw, I'm still running the first command until now...always cannot download completely, I wonder why is it so. Hmm.. have been trying and trying for more than 3 times now. I hope it will eventually finish the downloads for me.

Regards,
Jenson

---

### Post by jenson on 2007-09-01
I have aborted the download, as it seems like it will never get downloaded properly. Always been half way through and give me errors. Hmm.. Have to keep on retrying and retrying, again and again. Quite tiring. Wonder is there any better to do it? Else I will try it again later.. Geesh, I have been running the same commands, again and again :lolflag:

---

### Post by Perfect Storm on 2007-09-01
Sorry I can't help you there :-/


But a good rule is. If it aren't broke don't fix it. If the default driver works use it.

---

### Post by jenson on 2007-09-01
> **Artificial Intelligence said:**
> Sorry I can't help you there :-/


But a good rule is. If it aren't broke don't fix it. If the default driver works use it.

HI AI&#65292;

Ok, got it. Since it's working just fine, so I think I will just leave it as it is now since I managed to install Google Earth too. I will now trying to do what's in your tutorial now.

My current Ubuntu is only tweak with themes and wallpaper. I would like to see what else i can do with your tutorials.

Btw, is 32MB Video Memory enough for Beryl and all the tweaks in your tips?

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-02
Should be ok.

but as always, the bigger the better.

---

### Post by jenson on 2007-09-02
> **Artificial Intelligence said:**
> Should be ok.

but as always, the bigger the better.

Hey AI,

Thanks for the great helps! Now I just get a Creative Zen Stone Plus 2GB music player. I will need to dig out some information from other threads on how to use it on Ubuntu, or perhaps you have any idea? ^^

Sorry to trouble you so much, you have been very helpful and kind to me =)

Thanks a million.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-02
Can't help you there, I don't own a music player :)

If you run into trouble, just start a new thread.


regards
A.I. Dude

---

### Post by jenson on 2007-09-02
> **Artificial Intelligence said:**
> Can't help you there, I don't own a music player :)

If you run into trouble, just start a new thread.


regards
A.I. Dude

Okie dokie, roger that A.I. Dude :)

Regards,
Jenson

---

### Post by Hanselang on 2007-09-07
Great work. 
I've installed Nvidia with Envy and activated Compiz. 
Not after alot of hair ripping trying to get Ubuntu up and running on RAID0 (Using IDE atm)

Thanks AI

---

### Post by jenson on 2007-09-19
Hmm, same problem comes back after I reformat my notebook and squeeze the XP partition and increase my Ubuntu partition. Now I have the same old problem after I enabled NVIDIA driver for 3D Acceleration in the Restricted Driver Manager. Now trying to get it back but it seems that all the commands just won't run properly and give me all sorts of funny errors like this and that are not installed.

I will keep you guys updated and ask for helps again when needed.

P/S: AI, might need your expertise on this again >.<"

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
I need the error output.

---

### Post by jenson on 2007-09-20
> **Artificial Intelligence said:**
> I need the error output.

Hi AI,

I will output it later of the day as I'm at work right out, but I did go to the xorg.conf to change the driver from "nvidia" to "nv" but this time round, it doesn't work. What error log you need? Do you mean the syslog?

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
Anything you provided. Also which step you did.

---

### Post by jenson on 2007-09-20
ok attached is my nvidia-installer log and xorg, dmesg, and syslog, zipped in a folder called files and have made them into zip archieve.

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
From Nvidia log:
> ERROR: You do not appear to have libc header files installed on your system. 

```
sudo aptitude install libc6-dev
```

Better yet;

```
sudo aptitude install build-essential
```
Which grant full basic compiling tool.

---

### Post by jenson on 2007-09-20
> **Artificial Intelligence said:**
> From Nvidia log:


```
sudo aptitude install libc6-dev
```

Better yet;

```
sudo aptitude install build-essential
```
Which grant full basic compiling tool.

ahh, no wonder. These are the files that they mentioned I don't have when I try to run the same old commands you shown me here previously. Gosh..now I learn something new again. Sorry for being such a noob, I will try it out and update you again =)

Thanks a lot AI.

Regards,
Jenson

---

### Post by jenson on 2007-09-20
Hi AI,

What's next after this?repeat the installation of NVIDIA driver after stopping the gdm?

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
Have you also install the other stuff which is explained earlier in this thread?

---

### Post by jenson on 2007-09-20
> **Artificial Intelligence said:**
> Have you also install the other stuff which is explained earlier in this thread?

yes, except for the Envy :)

Now ready to do the NVIDIA installation, but do I need to set the driver back to Nvidia first?

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
nope, but you can always change it back and forth if it doesn't work.

---

### Post by jenson on 2007-09-20
> **Artificial Intelligence said:**
> nope, but you can always change it back and forth if it doesn't work.

ok, roger that. Your avatar is a female robot looking towards the left?

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-20
Yeah, it's from a game that's will be available for linux soon, a MMORPG;

[http://www.wakfu.com/](http://www.wakfu.com/)
(require flash)

---

### Post by jenson on 2007-09-20
> **Artificial Intelligence said:**
> Yeah, it's from a game that's will be available for linux soon, a MMORPG;

[http://www.wakfu.com/](http://www.wakfu.com/)
(require flash)

I C, that you would great! Btw, why doesn't GuildWars make itself available to Linux, I hate it, have to login to Windows XP to play.

Jenson

---

### Post by Perfect Storm on 2007-09-20
You could try with wine or Cedega.
Or if you're willing to change to Space MMO, EVE-Online will be be available for linux (Ubuntu and OpenSuse), based on Cedega engine (no extra cost, you pay the same as windows users do).

---

### Post by Ascado on 2007-09-20
Hello everybody.

After trying to install drivers for my nvidia card i read this thread today. I managed to install the drivers using envy (tried yesterday.. didnt work so well, had to reinstall).

The only problem is that i cant configure my monitor correctly. I only have the options for an lcd screen (e.g. refresh rate 55 or 60, only low resolutions or widescreen..)

I have tried the nvidia xserver settings (the grapical ui) where it even states my screen as an crt, but gives me only the options of 1024x768 and below or 1280x800.

The driver version is 100.14.19

Any hints? (by the way, im a complete linux beginner if you havent already guessed ^^)

---

### Post by Perfect Storm on 2007-09-20
> **Ascado said:**
> Hello everybody.

After trying to install drivers for my nvidia card i read this thread today. I managed to install the drivers using envy (tried yesterday.. didnt work so well, had to reinstall).

The only problem is that i cant configure my monitor correctly. I only have the options for an lcd screen (e.g. refresh rate 55 or 60, only low resolutions or widescreen..)

I have tried the nvidia xserver settings (the grapical ui) where it even states my screen as an crt, but gives me only the options of 1024x768 and below or 1280x800.

The driver version is 100.14.19

Any hints? (by the way, im a complete linux beginner if you havent already guessed ^^)

First try making the changes with;
```
gksudo nvidia-esstings
```

restart X

if it doesn't work;
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

(remember that [space] is to select and deselect, a common mistake new users make annd [return] to move on)

---

### Post by Ascado on 2007-09-20
Thanks for the quick reply.

The first command takes me to the nvidia control panel (which doesnt allow me to make the changes i need)

The second sets of commands takes me to a black screen, but nothing works from there. First i tried the "sudo dpkg-reconfigure -phigh xserver-xorg" (nothing)

Then the gdm start but it wouldnt restart.

---

### Post by Perfect Storm on 2007-09-20
try first with <ctrl>+<alt>+<F1> before entering the codes.

---

### Post by Ascado on 2007-09-20
Aha, that got me the resolution i wanted. Thanks so much.

But i still cant set the refresh rate to more than 50hz. (tried the system monitor settings as well as the nvidia settings tab).

---

### Post by Perfect Storm on 2007-09-20
Any chance you running compiz or beryl?

If not;
Do you have your monitor specs, more specific its Horizontal scan range and Vertical scan range.

---

### Post by Ascado on 2007-09-20
Neither compiz nor beryl. I just installed the latest ubuntu from the install cd yesterday.

Monitor specs are

Horizontal 30 - 96 kHz
Vertical 50 - 160 Hz

Other specs under [link sorry, its german.. the english version of the monitor seems different]("http://monitor.samsung.de/article.asp?artid=DD74D67A-9516-4F22-87BD-151A1CD734BF&show=specs")

---

### Post by Perfect Storm on 2007-09-20
ok.

please post your xorg.conf

```
cat /etc/X11/xorg.conf
```

---

### Post by Ascado on 2007-09-20
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "Standardgrafikkarte"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Standardgrafikkarte"
        Monitor         "Standardbildschirm"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666


Looks like the scan ranges are wrong?

---

### Post by Perfect Storm on 2007-09-20
Aye;

edit the xorg;

```
sudo nano /etc/X11/xorg.conf
```

change;
```

HorizSync 28-64
VertRefresh 43-60

```
to
```

HorizSync 30-96
VertRefresh 50-160

```

save = [ctrl]+[o]
exit = [ctrl]+[x]

restart X

---

### Post by Ascado on 2007-09-20
strange.. when i try to enter that file after the ctrl alt f1 and stuff it is empty.

when i open it with the editor in linux its all there (but i cant save the changes there)

*edit* i also have 2 more xorg.conf files in there (with filename extensions that look like date and time) plus backups for these.

---

### Post by Perfect Storm on 2007-09-20
you can edit the xorg.conf with nano while in gui (in X) when it comes to such things like this. You just need to restart X afterwards.

---

### Post by Ascado on 2007-09-20
i still get a blank file after that. when i tried entering the monitor part and saving it i got an "no such file exists" error message.

i cant seem to open the correct xorg.conf file. Could that be because of the other 2 xorg.conf files in there? one named xorg.conf.20070920203534, the other xorg.conf.20070920204141.

Going to sleep now, will check back here tomorrow. Thanks for all your help.

---

### Post by jenson on 2007-09-20
Hi AI,

I give up on trying, but reformat my Ubuntu again. Now I'm back inside with all the default settings, but managed to install build-essential and the libc6-dev from the Synaptic and installed the nvidia-glx-new and nvidia-glx-new-dev too. 

But nothing seems to be configuring to the correct one.

I did gksudo nvidia-settings, but this is what I get:

```

jenson@Ubuntu:~$ gksudo nvidia-settings
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```

and this is my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks.

Regards,
Jenson

PS: Very sorry to trouble you again, may I know what's my next step? What I mentioned on top are those I have installed including 190 updates.

---

### Post by Perfect Storm on 2007-09-20
> **Ascado said:**
> i still get a blank file after that. when i tried entering the monitor part and saving it i got an "no such file exists" error message.

i cant seem to open the correct xorg.conf file. Could that be because of the other 2 xorg.conf files in there? one named xorg.conf.20070920203534, the other xorg.conf.20070920204141.

Going to sleep now, will check back here tomorrow. Thanks for all your help.

Are you sure you're typing the command correct? Remember linux is case sensitive.

---

### Post by Perfect Storm on 2007-09-20
> **jenson said:**
> Hi AI,

I give up on trying, but reformat my Ubuntu again. Now I'm back inside with all the default settings, but managed to install build-essential and the libc6-dev from the Synaptic and installed the nvidia-glx-new and nvidia-glx-new-dev too. 

But nothing seems to be configuring to the correct one.

I did gksudo nvidia-settings, but this is what I get:

```

jenson@Ubuntu:~$ gksudo nvidia-settings
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```

and this is my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks.

Regards,
Jenson

PS: Very sorry to trouble you again, may I know what's my next step? What I mentioned on top are those I have installed including 190 updates.


I thought you going to get the latest nvidia driver, it seems to work best with your card.

ok, edit this part
```
Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```

to 

```
Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
```

---

### Post by Ascado on 2007-09-21
> **Artificial Intelligence said:**
> Are you sure you're typing the command correct? Remember linux is case sensitive.

I feel a little dumb right now  :)

It works perfectly now, thank you so much.

---

### Post by jenson on 2007-09-21
> **Artificial Intelligence said:**
> I thought you going to get the latest nvidia driver, it seems to work best with your card.

ok, edit this part
```
Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```

to 

```
Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
```

Hi AI,

So I changed it from nv to nvidia, and then install the Nvidia's latest driver?

Btw, can I just skip those steps since I have installed Libc6-dev and built-essential?

Do I still need to remove those nvidia-settings, etc etc?

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-21
Yes, you don't need to install the driver from synaptic/aptitude/apt-get if you're going to install the driver from nvidia.com

---

### Post by jenson on 2007-09-23
> **Artificial Intelligence said:**
> Yes, you don't need to install the driver from synaptic/aptitude/apt-get if you're going to install the driver from nvidia.com

Hi AI,

Alright, so does that mean after I have installed Libc6-dev and Built-essential, I can directly go to NVIDIA site to download the latest driver for installation?

So, again, I would have to sudo /etc/init.d/gdm stop, then sudo sh NVIDIA-Linux-x86-xxxxxx-pkg1.run, then after that sudo /etc/init.d/gdm start?

Or I can do --> sudo /etc/init.d/gdm restart? instead of sudo /etc/init.d/gdm start?

Thanks.

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-23
It's start

---

### Post by jenson on 2007-09-24
> **Artificial Intelligence said:**
> It's start

Hi AI,

Okie dokie, roger that.

Regards,
Jenson

---

### Post by jenson on 2007-09-28
Ok, after much troubles of configuring the NVIDIA graphic card, I've settled down with the default settings of my graphic card, but I managed to installed the nVidia graphic card, still giving me the same problem of unable to load X-server after the nVIDIA configure my xorg.conf for me.

Thus, seeing that the defaults settings changes made to my xorg.conf is causing my problem in loading my Ubuntu, I've decided to change the driver in the xorg.conf back to the working one, and now though my nvidia-settings still disallow me from doing configuration, at least, my restricted driver is still in use, but not enabled.

I will post my xorg.conf later at night and to see what you guys can help me with it, will you?

I've installed the latest glx driver for my Ubuntu too, but it doesn't seems to help me either. Normally, if I've managed to configured it properly, like what I have done with the helps of AI and some other forum members, it would display a nVIDIA logo before the login screen is displayed for me to key in my username and password, it really impressed me when it's finally done, now it seems to me that, I have to check what's wrong again since everything is just not working well, though I can always use the default settings for me (but I like to see the nVIDIA logo, of course it also means that my graphic card supports 3D acceleration and can install any application that make use of 3D acceleration supports, and further allow me to change the display settings).

I really hope to get it back like what it used to be :(

Regards,
Jenson

---

### Post by Perfect Storm on 2007-09-28
You could, if you want to, invest in a newer nvidia video card.
The one I have is a GT6600 GTS 256mb, never have trouble with it and it's cheap (because newer models is out there) and powerful.

---

### Post by jenson on 2007-09-28
Okie, I will heed to your advice then. But not so soon for upgrading =) Furthermore, it's running on my notebook right now. So I can't really upgrade the graphic card that come with it, since I was told by the vendor, that my graphic card is not upgradeable since they have mounted it to the motherboard.

Regards,
Jenson

---

### Post by Newbie1978 on 2007-10-02
Hello everybody! I have the same problem installing the graphic card geforce4 mx4000, any ideas for me? thanks for the help

---

### Post by Perfect Storm on 2007-10-02
Just use one of the descriptions in this thread to install the driver.

---

