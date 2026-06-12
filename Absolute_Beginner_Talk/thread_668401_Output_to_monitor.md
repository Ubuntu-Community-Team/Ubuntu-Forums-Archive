---
title: "Output to monitor"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by mike_g on 2008-01-15
My laptop screen broke :( 

I connected a monitor which works if I boot in safe mode, but when loading gnome a message appears on the screen saying "Input signal out of range", then it goes to sleep. 

Do I need drivers for it or something? Or how else could I get it to work? 

Cheers.

---

### Post by leonidas666 on 2008-01-15
I have the same configuration (laptop with broken lcd + external monitor, although i bought the laptop like this from ebay with the intention of running it like this...). My experience is that it can be a bit complicated to get the external monitor to work properly.

What happened in my case:
- the lcd might be broken, but the control logic still works, so the laptop thinks that you are actually running it with the lcd. The resololution and refresh rate is set according to the internal lcd, so you get some strange effects on the external monitor.
- to solve my problem, i had to change the xorg.conf file so that the driver is ignoring the lcd, and only looks at the external monitor. In my case (nvidia driver)
```
	Option		"ConnectedMonitor"	"CRT-0"
```
was the necessary option in the device section. Additionally, i had to specify the size of my external display manually (otherwise my display was running at the resolution of the internal display).

So what you should do: find out which driver you are using (look at the device-section in your xorg.conf), and then find out what extra options your driver has to disable the internal display. You can start by reading the manpage of your driver.

---

### Post by leonidas666 on 2008-01-15
And another thing: If you have some setting which controls the display output in your bios, like "Primary Screen : internal/external" or something like that, you can also try to change it if it has any effect.

---

### Post by mike_g on 2008-01-15
Thanks. I have an ATI GPU. Its a Radeon mobility U1. I had a look at the Radeon man page for, but the options it lists don't seem to include and for setting the ConnectedMonitor.

Anyway I opened the xorg.conf file and heres what seemed to be the relevant content in it:  
```
Section "Device"
    Identifier     "ATI Technologies Inc Radeon Mobility U1"
    Driver          "ati"
    BusID          "PCI:1:5:0"
    Option         "UseFBDev"                 "true"
End Section

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync   28-50
    VertRefresh  43-75
End Section

Section "Screen"
    Identifier       "DefaultScreen"
    Device           "ATI Technologies Inc Radeon Mobility U1"
    Monitor          "Generic"
    DefaultDepth 24
    SubSection     "Display"
        Modes    "1024x768"
    EndSubSection
EndSection
```

My external monitor supports the same maximum resolution, so I dont think thats a problem. Maybe its the hetage or something.

Anyone got any idea what I should change in this? 

I tried adding the line:
    **Option "ConnectedMonitor"  "LCD-1"**
To the monitor subsection as a random guess, but that dident seem to work.

Edit:
> And another thing: If you have some setting which controls the display output in your bios, like "Primary Screen : internal/external" or something like that, you can also try to change it if it has any effect.
Ok cool I'll have a look in my BIOS too.

---

