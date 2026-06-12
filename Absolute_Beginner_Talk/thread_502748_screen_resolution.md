---
title: "screen resolution"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by bigeyedphish4134 on 2007-07-17
Resolution is currently 1024 x 768, but it is supposed to be 1280 x 1024.  The restricted driver for my nvidia card installed properly.

any ideas? thanks.

---

### Post by Likenota on 2007-07-17
i believe you have to edit the xorg.conf  file located in /etc/x11/  folder...

---

### Post by Al3xK3aton on 2007-07-17
Set it to 1280x1024 and turn it sideways. You may need to purchase a compatible monitor, but they are only a few hundred dollars.

---

### Post by bigeyedphish4134 on 2007-07-17
ah, i mis-typed it.  I meant 1280 x 1024.

---

### Post by bigeyedphish4134 on 2007-07-17
i found the xorg.conf file  - but i'm not sure what to change

---

### Post by Rohen on 2007-07-17
Yep, I'm having the same problem here.  Darn these noob situations!!!

I wasx messing around with some xorg config file... and I ended up changing my resolution from the nice 1280x1021 to the  1024x768.

What do I do?  :(

---

### Post by w4ett on 2007-07-17
sudo dpkg-reconfigure -phigh xserver-xorg

Will give you the interface to add/modify  resolutions and refresh rates to you xorg.conf.

---

### Post by milton1 on 2007-07-17
You could try the obvious, simple way first:
```
sudo nvidia-settings 
```

---

### Post by lepz on 2007-07-17
> **bigeyedphish4134 said:**
> i found the xorg.conf file  - but i'm not sure what to change

Type in 1280x1024 at the beginning of each mode line in "Screen" section, save and then close/restart.

---

### Post by Rohen on 2007-07-17
> **w4ett said:**
> sudo dpkg-reconfigure -phigh xserver-xorg

Will give you the interface to add/modify  resolutions and refresh rates to you xorg.conf.

Allright so I did some messing around and I got my resolution back...  My monitor is a SONY SDM S81, came with the VAIO.

Anyways, I'm still in a jam.  I have a SiS  65x/m650/740.  I don't think I have the right driver installed, because when I watch a movie it looks all choppy.  Some guy told me the problem is with the Kernel I have.  And that I have to switch to kernel < 2.6.21.3.

Does that sound about right?

Thanks!:o

---

### Post by w4ett on 2007-07-17
Well, what kernel and Nvidia card do you have installed?  Lets see whats up with the video now...it just might be an issue with the codecs you have installed....

---

### Post by Rohen on 2007-07-17
> **w4ett said:**
> Well, what kernel and Nvidia card do you have installed?  Lets see whats up with the video now...it just might be an issue with the codecs you have installed....

HI!):P

Kernel is: 2.6.20-16-generic

Video: SiS 65x/m650/740 PCI/AGP VGA Display Adapter 

Thanks for the help **w4ett**.  I really appreciate it!

:popcorn:

---

### Post by w4ett on 2007-07-17
Not a kernel problem, I don't think....let's check the video driver

Post the output of:

glxinfo   (for 3D Enable)

and then:

cat /etc/X11/xorg.conf

and let's have a look-see... :)

---

### Post by Rohen on 2007-07-17
Odd thing; when I type glxinfo, it signs me off my user.  Then I have to log back on. :confused:

"cat /etc/X11/xorg.conf," Gives me this:

[INDENT]Section "Files"
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
        Identifier      "Generic Video Card"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        VideoRam        64
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "SONY SDM-S81"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "SONY SDM-S81"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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
        Mode    0666[/INDENT]


Does this help? ](*,)

---

### Post by w4ett on 2007-07-17
Good news is that you are running the correct driver (SIS), problem is bad support for linux drivers.

The bad news is that is particularly bad driver with 2D support only (That I am aware of, anyway).

Have you enabled the codec packages in Synaptic ( in multiverse, I believe).  Also, make sure you have the maximum shared memory (Minimum 64 MB) enabled in your motherboard's bios settings. The more the better.

also, what

---

### Post by Rohen on 2007-07-17
> **w4ett said:**
> 

Have you enabled the codec packages in Synaptic ( in multiverse, I believe).  Also, make sure you have the maximum shared memory (Minimum 64 MB) enabled in your motherboard's bios settings. The more the better.



I guess I could try enabling max mem from my bios?  I mean I haven't touched my bios since I installed Ubuntu, maybe that would help out.  Any tips on how I would go about doing that? :-k

---

### Post by w4ett on 2007-07-18
> **Rohen said:**
> I guess I could try enabling max mem from my bios?  I mean I haven't touched my bios since I installed Ubuntu, maybe that would help out.  Any tips on how I would go about doing that? :-k

Using F1 or F2 at the boot (post) screen usually will log into your BIOS (some Mfgs call it SETUP).  Then find the section regarding your video chipset memory, and follow the prompt to adjust settings.

---

### Post by bigeyedphish4134 on 2007-07-18
> **milton1 said:**
> You could try the obvious, simple way first:
```
sudo nvidia-settings 
```

Did that, restarted, and it worked perfectly.

thanks guys!

---

### Post by algy on 2007-07-19
Each time I set my screen resolution to 1280 x 1024 it returns on reboot to 1024 x 768. I have used nvidia-settings (I have a Geforce 7300gt), I have followed the helpful instructions to edit the xconfig and I have ticked the box to apply the settings for this computer. None has done the trick.
Algy

---

### Post by Rohen on 2007-07-19
> **w4ett said:**
> Using F1 or F2 at the boot (post) screen usually will log into your BIOS (some Mfgs call it SETUP).  Then find the section regarding your video chipset memory, and follow the prompt to adjust settings.

When I tried to reboot the option it gives me is to press ESC for "menu."  Then there are four option.   I can choose to boot up two diff kernel versions, and also choose the safe mode for both of those kernels (4 options)

So I don't see an option of where I can change my video thing.#-o

The very first screen that appears when I boot up is the "SONY" and then for a split second a screen flashes, and then it goes to the Ubuntu boot

"press ESC for menu... (countdown 3, 2, 1...)"

](*,)  Any ideas?

---

### Post by w4ett on 2007-07-19
> **Rohen said:**
> When I tried to reboot the option it gives me is to press ESC for "menu."  Then there are four option.   I can choose to boot up two diff kernel versions, and also choose the safe mode for both of those kernels (4 options)

So I don't see an option of where I can change my video thing.#-o

The very first screen that appears when I boot up is the "SONY" and then for a split second a screen flashes, and then it goes to the Ubuntu boot

"press ESC for menu... (countdown 3, 2, 1...)"

](*,)  Any ideas?

<esc> is the key to enter Setup (Bios control panel)...press and wait on booting.  Then look for your video setting. They may be listed under Chipset Configuration, or something similar to that.  Set for max memory usage for your video.

---

### Post by algy on 2007-07-19
I appear to have solved this problem by enabling Video Bios Cacheable in the Bios.
Algy

---

### Post by w4ett on 2007-07-19
Super...

Please mark this thread as "SOLVED"

Good Luck!

---

