---
title: "resolution troubles"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by volgatha on 2007-10-01
I have a weird resolution problem. I have recently loaded Feisty onto my computer. I am using the nvidia driver and I am able to set the screen size to my desired resolution (1280x1024) through that. However, in Ubuntu's resolution adjuster, the highest resolution available is 1024x768. Though this wouldn't normally be a problem and I can change it perfectly fine through the nvidia settings, every time I restart my computer, it defaults to 1024x768 and I need to set it all over again. Any ideas? This is kind of weird.

---

### Post by overdrank on 2007-10-01
> **volgatha said:**
> I have a weird resolution problem. I have recently loaded Feisty onto my computer. I am using the nvidia driver and I am able to set the screen size to my desired resolution (1280x1024) through that. However, in Ubuntu's resolution adjuster, the highest resolution available is 1024x768. Though this wouldn't normally be a problem and I can change it perfectly fine through the nvidia settings, every time I restart my computer, it defaults to 1024x768 and I need to set it all over again. Any ideas? This is kind of weird.

Hi and if you use this command 
```
gksudo nvidia-settings
```
This will allow you to save your settings, Good luck!

---

### Post by overlord.gaurav on 2007-10-01
The screen resolutions that Ubuntu gives are the values given by you when you are installing ubuntu. These values are saved in /etc/X11/xorg.conf
Try adding the resolutions that you want to this file.

```
sudo gedit /etc/X11/xorg.conf
```

Under section: Section "Screen"  >>     SubSection     "Display" >>  Modes >> Add the resolution to all the Sub sections.
Reboot.

---

### Post by phidia on 2007-10-01
How did you install the nvidia driver? You probably want to look at your /etc/X11/xorg.conf file and check what setting you have there under "monitor". If, as you say, the highest rez you have through Preferences>screen resolution is 1024x768 you probably don't have the higger rez listed in your xorg.conf

---

### Post by overdrank on 2007-10-01
> **overlord.gaurav said:**
> The screen resolutions that Ubuntu gives are the values given by you when you are installing ubuntu. These values are saved in /etc/X11/xorg.conf
Try adding the resolutions that you want to this file.

```
sudo gedit /etc/X11/xorg.conf
```

Under section: Section "Screen"  >>     SubSection     "Display" >>  Modes >> Add the resolution to all the Sub sections.
Reboot.

Hi and you are correct though I would suggest using gksudo. :)

---

### Post by Pumalite on 2007-10-01
I agree.

---

### Post by gamerteck on 2007-10-01
To go along with **overlord.gaurav's** post; below is an example of the section you want to edit in your **/etc/X11/xorg.conf** file. It'll look a little different but an example of what you'll want to add I have highlighted in red.

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
                [COLOR="Red"]Modes           "1280x1024"[/COLOR]
        EndSubSection

```

---

