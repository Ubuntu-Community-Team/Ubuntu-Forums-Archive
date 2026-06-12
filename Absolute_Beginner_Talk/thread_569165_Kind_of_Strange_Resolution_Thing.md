---
title: "Kind of Strange Resolution Thing"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by snowlion on 2007-10-06
I use a resolution of 1024x768.

Whether the nvidia driver is installed or not, I am able to have a refresh rate of 85Hz.

Basically, after installing the nvidia driver, instead of it showing "85Hz" under the Refresh rate in Screen Resolution Preferences it instead replaces "85Hz" with "55Hz".  I can pretty much tell that the refresh rate has stayed the same and hasn't really gone down to 55Hz.  Pretty strange, I wonder why it does that.

---

### Post by ofb on 2007-10-06
You're not alone. What I've noticed from reading is this under-report has been common for years, though nobody mentions why. Something to do with the proprietary driver I guess -- no one can look inside to find out.

Your real rate will show up in nvidia-settings. Depending on your monitor, you may be able to use display's built-in settings panel to show the rate too. 

Bonus curiosity - under both Windows and Knoppix LiveCD, I get 100Hz by default, but only 85Hz with the Nviida driver in Ubuntu.  (Monitor has something to do with this. My previous display always had flicker with Knoppix.)

---

### Post by snowlion on 2007-10-09
I am also able to get 1024x768@100Hz under Windows but with Linux (and I think *BSD) I am only able to get up to 85Hz using this screen resolution.

---

### Post by laidback on 2007-10-09
What are these nvidia-settings? I'd like to look at them.

---

### Post by Wim Sturkenboom on 2007-10-09
If you can't achieve the max refresh rates, you can try the following

Make sure that HorizSync and Vertrefresh in the *monitor* section in /etc/X11/xorg.conf are set to reflect the capabilities of your monitor.
If that is not enough, add *option "UseEdidFreqs" "FALSE"* to the *device* section in etc/X11/xorg.conf.

---

### Post by ofb on 2007-10-09
> **laidback said:**
> What are these nvidia-settings? I'd like to look at them.

Enter 'nvidia-settings' in terminal. That should launch a Nvidia GUI.
----

Wim Sturkenboom, I've got a question about that. Here's the relevent portion of mine:

```
Section "Device"
        Identifier      "NVIDIA GeForce4 MX-440 SE"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"        "true"
EndSection

Section "Monitor"
        Identifier      "IBM G78"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce4 MX-440 SE"
        Monitor         "IBM G78"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

```

What happens if one needs to reboot with an inferior replacement monitor? Does Ubuntu detect that the G78 is not there, and use the generic "ServerLayout" settings instead?

Just asking because I had trouble along that line years ago with the OtherOS(tm). I couldn't use the small backup monitor till I reinstalled. That made me a big fan of PnP, and has left me wondering how Linux handles hardware changes, since it looks like the set-up is hard-coded into xorg.conf.

---

### Post by Wim Sturkenboom on 2007-10-10
As far as I know, you will have a problem in that case as you're now forcing X to use something that the monitor can't handle. 

If the old monitor has protection (messages like 'frequency out-of-range'), you can use it and switch to a console (e.g. by pressing <ctrl><alt><F1>, login, modify the settings in xorg.conf and restart X.

If the monitor does not have that protection, you have a chance of blowing up the elctronics in your monitor. In that case, you have some options to get it right (I have tested neither of them):
[LIST]
[*]I'm not sure what the recovery entry in grub exactly does as I've never used it. It might take you to a console or you might get a GUI with a low resolution; just try it out with your normal monitor. In both cases you're safe and you can reconfigure X by editing xorg.conf.
[*]Use a live CD and modify xorg.conf (the one on the HD).
[*]Boot without monitor connected, after boot press above key combination, connect monitor and follow the rest of the above instructions
[/LIST]

Re-install should not be necessary.

---

### Post by ofb on 2007-10-10
> **Wim Sturkenboom said:**
> If the monitor does not have that protection, you have a chance of blowing up the elctronics in your monitor.

Thank you. That's precisely what my paranoia was suggesting. I'll reward it by having it nag me to boot Knoppix first after unscheduled hardware changes. 

> Boot without monitor connected, after boot press above key combination, connect monitor and follow the rest of the above instructions

I didn't know you could hot-plug monitors. Does it matter if the monitor's power is On or Off during the break/connection? Same for both VGA and DVI?

> Re-install should not be necessary.

To be fair, it should not have been necessary in Windows, but that OS was generous with surprises. I think it was sometime around the 5 year mark that I stopped thinking I'd seen all the error modes.

---

### Post by laidback on 2007-10-10
ofb,

Many thanks, I have it.

Laidback

---

### Post by Wim Sturkenboom on 2007-10-10
> **ofb said:**
> I didn't know you could hot-plug monitors. Does it matter if the monitor's power is On or Off during the break/connection? Same for both VGA and DVI? In both cases, I would switch the monitor off while connecting if in doubt, but I have, however, often disconnected and reconnected monitors (VGA) while the equipment was still powered.

---

### Post by ofb on 2007-10-10
Thanks.

Extra: I use a KVM between similar machines. I've just noticed that if I boot one but don't switch to it until it has loaded, the refresh rate will be low. This is similar behavior to Windows where the PnP has not been able to  detect a montior, except the resolution is correct in Ubuntu. (In Win it would be a safe 640x or 800x.) So there's a certain amount of detection going on. I'll have to read up on how xorg.conf is handled at some point.

(For the curious, just restart Gnome with ctl-alt-backspace to have your correct settings applied with no fuss.)

---

