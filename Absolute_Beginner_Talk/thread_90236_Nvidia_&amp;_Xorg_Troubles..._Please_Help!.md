---
title: "Nvidia &amp; Xorg Troubles... Please Help!"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-11-14
I just installed Breezy on my higher-end computer with a 5200 Geforce Nvidia card installed (PCI).

It will not load the GUI and only stays in the bash window.
I have installed 'nvidia-glx' and 'nvidia-settings' but when i go to change the 'xorg.conf' no text shows up, just a bunch of options at the buttom such as '^G get help' '^O Write Out' ... ect.
I use the command 'sudo pico /etc/x11/xorg.conf' to open the xorg file.

When I press F5 to read the document it asks what file i want to read so i type in '/etc/x11/xorg.conf' and it tells me it cannot be found.

How do I use pico (or any other method) to get my nvidia card and setting installed when I do not have a GUI (GNOME)?

---

### Post by nitricacid on 2005-11-14
ok, I found out why no text was showing when I typed 'sudo pico /etc/x11/xorg.conf, figures i need to make the 'X' in /x11 capital.

Ok, so now my new question is...

How do I change the "Device" to reconize my Nvidia driver instead of y 'intel corp 82865G inegrated Graphics device' ?

Do I just change the description in the 'Identifier' to that of my nvidia card and change the 'driver' to nvidia?

---

### Post by nitricacid on 2005-11-14
You can all ignore this post.

I changed the name of the 'Device' from the 'intel blah' to 'nvidia', restarted my computer and GDM and GNOME started wonderfull.

I would like to know where the setting are for the Nvidia card though, so i can change some of the card settings themselves.

Thanks anyway :)

---

### Post by adam_kimber on 2005-11-14
[QUOTE=nitricacid]

How do I change the "Device" to reconize my Nvidia driver instead of y 'intel corp 82865G inegrated Graphics device' ?

Do I just change the description in the 'Identifier' to that of my nvidia card and change the 'driver' to nvidia?[/QUOTE]

Hi. 

You need to fiddle a little with your xorg.conf, and yes you change the identifiers and the driver - the key one to change is the driver -

This is what i have in my device section:

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra"        
       Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"        "1"
EndSection

This is waht i have in my screen section:

    Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra"

and so on

make sure the identifers match up and the driver is "nvidia". The nologo bit disables the nvidia splash screen upn the start of the display manager.

Adam

---

### Post by adam_kimber on 2005-11-14
Doh. I was working on the post when you posted again.

---

### Post by jrw6 on 2005-11-14
[QUOTE=nitricacid]
I would like to know where the setting are for the Nvidia card though, so i can change some of the card settings themselves.
Thanks anyway :)[/QUOTE]

```
sudo apt-get install nvidia-settings
```

Then run "nvidia-settings".  Save your modified settings from within the program.  To make these settings get restored every time you log into GNOME, go to System -> Preferences -> Sessions.  Go to "Startup Programs", and put an entry  in there which says "nvidia-settings -l".  Done!

---

