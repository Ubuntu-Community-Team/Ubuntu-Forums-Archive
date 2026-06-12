---
title: "[SOLVED] After gutsy upgrade I only get a blank screen after login"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by bldgengineer on 2008-02-29
a few months ago I upgraded from fiesty to gutsy and from the start I've had this problem: Everything loads fine but after I login I get nothing but a blank white screen. I tried going to the nv driver with no luck. :confused:

here's my setup:
2.4ghz C2D, 2gb ram, (2)nvidia 8600gts

Any help would be greatly appreciated

---

### Post by Scarath on 2008-02-29
Have you checked your /etc/X11/xorg.conf to see if everything is still as it should be?

---

### Post by rbrittner on 2008-02-29
I agree, boot in recovery mode and check your xorg file.  First I would try this though.  Boot in recovery mode (hit esc when prompted) then once it's booted type the following

sudo dpkg-reconfigure xserver-xorg

this will reconfigure it to what it was when you first installed. 

If you don't want to go that route, boot in recovery and type the following

nano /etc/X11/xorg.conf

that code allows you to edit your xorg (the video driver settings)

---

### Post by bldgengineer on 2008-02-29
Yes and it looked like everything was alright(to me anyway) but I had this problem before during a driver upgrade for the graphics card with fiesty and I had to go back to using the nv driver for it to work. After that, I just manually reinstalled the drivers from nvidia to get it working again. This time though, even after switching to the nv default driver I just get the same result, a blank white screen after I login

---

### Post by Scarath on 2008-02-29
Also lots of people have problems with the 8*** series nvidia cards with the ubuntu restricted drivers. Try using the ones from nvidia if possible?

[[edit never mind u beat me to it :D]]

Its my catch phrase but have you tried using Envy?

---

### Post by bldgengineer on 2008-02-29
yeah thats what I used when fiesty upgraded the driver I initially installed when I first installed ubuntu. Are there any apt get's that I might be able to do in the command prompt for envy?

---

### Post by bldgengineer on 2008-02-29
ok after a little bit of fooling around I stumbled across the textual version of envy and proceeded to reinstall and received a question about attempting to update the kernal since there was an update(I figured why the hell not, what I had to begin with wasnt working at all:)) so I did and got it to work until the system asked me to reboot(I was so happy that I actually got into the GUI!) then I got the message " cannot launch graphical configuration tool because display config-gtk is not installed" :(

I had to reboot to system recovery mode, login in the command prompt and tried the sudo dpkg-reconfigure xserver-xorg command and followed the instructions. 

Now I'm here, typing this in ubuntu but everything seems to be moving slower(windows opening slow, mouse scroll over is moving slow etc etc) and I don't have any sound(I did when I had fiesty).

I went to Update manager and I'm going to attempt a partial update like it recommends and see what happens. If it works I'll see you in Ubuntu :) if not, I'll see you in windows :(

---

### Post by bldgengineer on 2008-02-29
so here I am replying from windows:(.....

After all the updates were downloaded and installed, I was asked to reboot the system which I did and once again I saw something saying "cannont show progress meter" or the like and when the login screen was suppose to load, I received a window that I received before stating "Cannot Launch graphical configuration tool because display config-gtk is not installed"

So I loaded through the recovery mode and logged in and tried reinstalling the nvidia driver through envy -t and received the message "envy cannot work with your operating system" or something close to it. 

My new kernel is 2.6.22-14-386 does anyone know a way around this? I would have been perfectly happy just working out the sound issue first....

Its a good thing I really like Ubuntu plus I like learning new things like this anyway :)

---

### Post by bldgengineer on 2008-03-01
well I was able to get back in using the older driver from nVidia(the newer driver wouldn't d/l for some reason). Everything seems to working, graphically. I still don't have sound for some reason. Gutsy says I don't have a soundcard even though fiesty was always able to see it. Any ideas?

---

### Post by Scarath on 2008-03-01
Nice to hear you got your graphics running again.

Has your sound ever worked? I have never been able to get my on board sound to work with ubuntu so I got a [USB sound card]("http://sounden.terratec.net/modules.php?op=modload&name=News&file=article&sid=230") and its been fine ever since :D

---

### Post by erginemr on 2008-03-01
Your problem is quite enigmatic, a lot of things can happen that may have caused problems in graphics and loss of sound. As far as I remember, even the developers of Envy suggest to uninstall the binary driver first before making a distribution upgrade, as it might cause  incompatibilities with the new kernel.

In this context, I think you should back up what you can and restart with a fresh install of Gutsy. But first, a few things to ask/try before taking this step:

1) Is your graphics working OK now? Are you happy with the performance (any more sluggish windows)? And have you gotten rid of the ominous "display config-gtk is not installed" message? can you please post your "xorg.conf" file here by using:
```
gedit /etc/X11/xorg.conf
```

2) What is the brand of your sound card? Is it onboard or PCI? What is the outcome of the following command on the terminal:
```
lspci | grep -i audio
``` 

3) In an effort to make your sound card work again, you may try what I have suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=710581](http://ubuntuforums.org/showthread.php?t=710581)
Here is the original site where this trick is reported to work for many people:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

4) Honestly, I don't expect your problems will be over. Murphy's rule applies again. Even Ubuntu developers warn people that upgrading between versions is not the best way. I strongly think that during the update process, something has been irrevocably broken. 
The best way in my humble opinion, is for you to salvage all you can (your "/home/your_name" folder for your personal files and the "/etc" folder for some important settings) to a removable medium (or another hard drive) and do a clean install from the Gutsy Live CD.

5) Speaking of which, you should first make sure that Gutsy Live CD can recognize your sound card, that is, you can hear sounds when running from the Live CD. 

Good Luck.

---

### Post by Myglaren on 2008-03-01
I experimentaly upgraded although I had the discs here just in case.  Worked a treat.

---

### Post by bldgengineer on 2008-03-01
Here is my xorg.conf file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 8600"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 8600"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
  
```

And this is what I get after lspci | grep -i audio

```
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```

My audio is onboard on an nVidia motherboad. Everything seems to be working great right now. Nothing is acting slow I've even got the desktop effects with no problems, except this funky sound issue

---

### Post by bldgengineer on 2008-03-01
I just put in 
```
aplay -l
```

and received this
```
aplay: device_list:204: no soundcards found...
```

---

### Post by erginemr on 2008-03-02
OK, how about these:
> 3) In an effort to make your sound card work again, you may try what I have suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=710581](http://ubuntuforums.org/showthread.php?t=710581)
Here is the original site where this trick is reported to work for many people:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

> 5) Speaking of which, you should first make sure that Gutsy Live CD can recognize your sound card, that is, you can hear sounds when running from the Live CD. 

---

### Post by erginemr on 2008-03-02
Here is a thread with a similar problem:
[http://ubuntuforums.org/showthread.php?t=584755](http://ubuntuforums.org/showthread.php?t=584755)

but there the onboard audio was HDA Intel. But it teaches us one thing though;
To focus on the files
```
/etc/modprobe.d/alsa-base
```
and
```
/etc/modules
```

You should maybe boot from the Live CD, get this file on a USB pen drive and compare it with the one installed to find out that magic line.

---

### Post by erginemr on 2008-03-02
OK. Another read:
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Unfortunately sound is not my *forte*, but I still hope that we shall solve this.

---

### Post by bldgengineer on 2008-03-02
I'm downloading the livecd now and will give it a try after it gets burned and let you know what happens...

---

### Post by bldgengineer on 2008-03-02
ok, I'm on the LiveCD and sound works great. I went into System>Preferences>Sound and under Default mixer tracks its showing me Device HDA NVida (Alsa mixer)

---

### Post by erginemr on 2008-03-02
Great! Now, grab those two files I mentioned before to a removable medium, boot your system normally and either copy them over your installed system (by taking a copy of the originals first of course) or inspect and compare them with the ones on your system to find out the correct parameter.

I hope you are good at CLI to backup and copy your files with necessary permissions, because you will need that.

If this doesn't work, you may still install the backport drivers package by referring to:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by bldgengineer on 2008-03-02
Finally got sound working and didn't even have to do a fresh install! :D

All I did was follow the last website you gave me and went through synaptic package manager and found the 386 backport modules and made sure my unsupported updates were enabled, rebooted and WOOOHOOO! SOUND!!!

Thanks so much for all of your help!!!

---

### Post by erginemr on 2008-03-02
Great news! I am very glad that you have solved it. Way to go now! :KS

By the way, did you have a chance to look at those config files? But anyway, forget about it as long as your system works. Don't fix if ain't broken, right? ;)

---

