---
title: "No X after Gutsy install!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nabl on 2007-10-19
I just installed Kubuntu 7.10, and when I restarted the computer all that came up was a giant terminal. I think it is an error with the video card drivers, as it says
```
Fatal server error:
no screens found
```
when I try startx... I don't know what to do, being a linux newbie. :(

I think I may need to reinstall the nVidia drivers, but I don't know how from the terminal.

Thanks in advance for your help! :)

---

### Post by rickycodie on 2007-10-19
try to reconfigure x

sudo dpkg-reconfigure xserver-xorg

---

### Post by nabl on 2007-10-19
I tried that now... It's still saying that same thing. :( One of the options asked for the maximum resolution, but it's still trying to use a higher resolution than the screen can handle, if I'm understading this correctly...

My screen also gives and error:
```
Out of scan range
Resolution > XGA
```

Thanks again for your help...

---

### Post by nabl on 2007-10-19
I tried a couple other things, but it's still not working... :( Please help! (Thanks!)

---

### Post by RomeReactor on 2007-10-19
Hi. When you ran the dpkg-reconfigure command, did you accept all the defaults the system showed you? the only thing you probably should change (if it's not the default) is when it asks which video driver to use; if you do have an nVidia card, select the **nv** driver.

Please post the output of these commands:
```
sudo lshw -C dislpay
```
(this one will ask for your password); and:
```
cat /etc/X11/xorg.conf
```

Installing the proprietary nVidia drivers may not be possible right now; the servers are under a full load, it seems.

---

### Post by kshane on 2007-10-19
> **RomeReactor said:**
> 

Installing the proprietary nVidia drivers may not be possible right now; the servers are under a full load, it seems.

Use the Utah servers.  They seem to be doing ok...

Kevin

---

### Post by nabl on 2007-10-19
> **RomeReactor said:**
> Please post the output of these commands:
```
sudo lshw -C dislpay
```
(this one will ask for your password);
Description: VGA compatible controller
product: NV20 [GeForce3 Ti 200]
vendor: nVidia corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: pm agp apg-2.0 cga bus_master cap_list


> and:
```
cat /etc/X11/xorg.conf
```

Installing the proprietary nVidia drivers may not be possible right now; the servers are under a full load, it seems.
This output is even longer, so I can't see it all. Here's the screen section, though.

Section "Screen"
Identifier     "default screen"
Device:    "nvidia corporation nv20 [geforce3 ti 200]"
Monitor    "SDM-S51"
DefaultDepth    "24"
Subsection "Display"
      Modes     "1024 x 768"    "800 x 600"    "640 x 480"
EndSubSection

---

### Post by nabl on 2007-10-19
> **kshane said:**
> Use the Utah servers.  They seem to be doing ok...

Kevin
How do I change the repositories through the terminal?

---

### Post by nabl on 2007-10-19
Hooray! I don't know what happened, but it's working now! :) I just went through the dpkg-reconfigure command one more time, and selected all defaults as you recommended. Then I did startx and it worked!!! I restarted it, too, and it started automatically, so I think I got it. Thank you so much! :) My mouse isn't working now (I think the default for that was incorrect in dpkg-reconfigure), but I'll work on that tomorrow. I'll sleep well tonight. :)

Thanks to all of you! I REALLY appreciate it! This place is great! I'll be sure to post any questions I have (I'm sure I'll have plenty) here in the future. :)

---

### Post by RomeReactor on 2007-10-19
> **nabl said:**
> This output is even longer, so I can't see it all.

Forgot about that. Try this:
```
less /etc/X11/xorg.conf
```
and use the "down" arrow on your keyboard to scroll down to **Section  "Device"**. Please post that. To quit viewing the file in the terminal, press **Q**.

EDIT: Glad you got it working!

---

