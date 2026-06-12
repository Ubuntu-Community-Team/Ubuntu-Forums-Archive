---
title: "monitor size"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-04-14
Hi,

Switched on computer this morning and somehow landed in 480x600 or something. don't know how or what i did...
for this 17in. monitor i'm usually set at 1200x800 or something

Can somene tell me how to correct this, please,

--

sophtpaw

---

### Post by mrchrisblau on 2006-04-14
/etc/X11/xorg.conf

It will have a list of a bunch of different resolutions. If 1280x900 (or whatever your 17inch runs at) is not listed, add it. Then you should be able to go System > Pref > Screen Resolution and change the res.

---

### Post by sophtpaw on 2006-04-14
[QUOTE=mrchrisblau]/etc/X11/xorg.conf

It will have a list of a bunch of different resolutions. If 1280x900 (or whatever your 17inch runs at) is not listed, add it. Then you should be able to go System > Pref > Screen Resolution and change the res.[/QUOTE]

hi, thx but /etc/X11/org.conf is not the right command. 'd be grateful if you could dig the right one up or if there is another way of setting the size - this is unbearable as well as unworkable. Tried from bios and nada ; and there is nothing from System/preference or administration that seems that would do it either

--
sophtpaw

Actually, there is System/Preference/Screen resolution but it is set to default 640x480! with no options for change - great, so what is the point of that?

---

### Post by dermotti on 2006-04-14
run **sudo dpkg-reconfigure xserver-xorg**

there will be an option for resolution in there.

---

### Post by mrchrisblau on 2006-04-14
/etc/X11/xorg.conf is not a command, just the file name/location.

Heres what I would run:

login as root in the terminal (assuming you have the root account setup. If not, just do sudo).

then backup the file: 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then edit using gedit (or whatever text editor you have. I'd use vi if you're not in X, or  gedit if you are in X):
```
gedit /etc/X11/xorg.conf
```

Then scroll down until you see this:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "NEC 90gx2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Enter in the resolution that you want in the same place and way as you see the other resolutions (1600x1200 is just an example, use your res):

```
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```

Then save /etc/X11/xorg.conf.

Reboot.

Go System > Pref > Screen Resolution and there *should* be a selection box with your resolution in it.

If there isnt, you might want to try reinstalling your graphics drivers. This happend to me recently and all I needed to do was reinstall my nvidia drivers (can be downloaded on the nvidia website).

I hope this helps!

---

### Post by sophtpaw on 2006-04-14
[QUOTE=dermotti]run **sudo dpkg-reconfigure xserver-xorg**

there will be an option for resolution in there.[/QUOTE]
don't know the name of video driver

--
sophtpaw

---

### Post by mrchrisblau on 2006-04-14
[QUOTE=sophtpaw]don't know the name of video driver

--
sophtpaw[/QUOTE]

Ah, thats probably the problem then. I'd try reinstalling the video drivers.

What card do you have?

---

### Post by dermotti on 2006-04-14
use **vesa** as your driver for now until we get it working

---

### Post by mrchrisblau on 2006-04-14
50/50 shot here.. but worth a try anyway:

If you have an nVidia card here is a *great* howto on installing the latest drivers.
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)

---

### Post by sophtpaw on 2006-04-14
[QUOTE=mrchrisblau]50/50 shot here.. but worth a try anyway:

If you have an nVidia card here is a *great* howto on installing the latest drivers.
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)[/QUOTE]


your xorg.conf instructions revealed that this computer uses SIS

I then went back and followed Dermotti's dpkg reconfiguring instructions. I had to really blag it because there were alot of technical questions before i got to anything to do with the monitor. I was worried that in the process i would mess up other things, but i seem to be alright now.

Phew... back to normality. 640x480?? people still use that size? not a nice default setting to fall into. Alot of scrolling required : )

Thanks guys, 

--
sophtpaw

---

