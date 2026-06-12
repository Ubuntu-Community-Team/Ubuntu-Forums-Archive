---
title: "Ubuntu 7.10 installation on Mac Mini questions"
date: 2007-11-22
forum: Apple Intel Users
---

### Post by blk97tt on 2007-11-22
I am looking to install Ubuntu 7.10 on a Intel 1.6 Ghz Core Duo Mini.  It will be hooked to a 1080p HDTV.  I don't have a need for any other OS, so I am not looking to dual boot.

Does everything work out of the box?  My main concerns are making sure that wifi, 1080p resolution and blue tooth work.  

I want to make sure I know what to expect before I attempt the installation.  Any tips or information would be appreciated.

Thanks in advance.

---

### Post by cyberdork33 on 2007-11-22
> **blk97tt said:**
> I am looking to install Ubuntu 7.10 on a Intel 1.6 Ghz Core Duo Mini.  It will be hooked to a 1080p HDTV.  I don't have a need for any other OS, so I am not looking to dual boot.

Does everything work out of the box?  My main concerns are making sure that wifi, 1080p resolution and blue tooth work.  

I want to make sure I know what to expect before I attempt the installation.  Any tips or information would be appreciated.

Thanks in advance.
What wifi card do you have? I think it is Atheros, and you will likely need to install madwifi if it doesn't work out of the box. If it is Broadcom, you might have a bit more trouble.

---

### Post by blk97tt on 2007-11-22
> **cyberdork33 said:**
> What wifi card do you have? I think it is Atheros, and you will likely need to install madwifi if it doesn't work out of the box. If it is Broadcom, you might have a bit more trouble.

How do I find out what wifi card I have in OS X?

Thanks

---

### Post by cyberdork33 on 2007-11-23
Not sure... Probably in System Profiler.

You can burn the Live CD and boot it up. This will give a good idea what what will work.

---

### Post by blk97tt on 2007-11-26
I decided to install Ubuntu 7.10 server and then installed the Gnome desktop.  I am running into a few issues now:

Video
I am connecting the Mini to a Sharp AQUOS 1080p TV via DVI to HDMI connector.  I don't have any restricted drivers installed.  The lspci command shows me that I have the 945GM chipset.  

When the computer boots up, I can see it trying out different resolutions and finally settle on 1920 x 1080 at the logon screen (if my display was powered on during the boot process).

If my display is powered off during the boot process, I get an error message "Ubnuntu is running in low graphics mode."  
Under "Screen and Graphics Preferences" window my screen model is set to "plug and play."  My resolution is set to 1920 x 1080.  

If I try to set the display to "Generic LCD Panel 1920 x 1080" and check the widescreen box, it doesnt give me a 1920 x 1080 option in the "resolution" drop down box.

The graphics card tab shows that it is using the "Intel-Experimental modesetting driver"

I need to be able to boot up correctly into 1920 x 1080 resolution with the display off.  How can I correct this?



Wifi
I have the Atheros AR5006EG chipset.  I was able connect via wifi without any problems with a Live CD.  After I installed Ubuntu to hard drive, I have not been able to get wifi to work.  Network Manager is not showing any Wireless connection option.

Please help!
Thanks

---

### Post by cyberdork33 on 2007-11-27
> **blk97tt said:**
> Video
I am connecting the Mini to a Sharp AQUOS 1080p TV via DVI to HDMI connector.  I don't have any restricted drivers installed.  The lspci command shows me that I have the 945GM chipset.  

When the computer boots up, I can see it trying out different resolutions and finally settle on 1920 x 1080 at the logon screen (if my display was powered on during the boot process).

If my display is powered off during the boot process, I get an error message "Ubnuntu is running in low graphics mode."  
Under "Screen and Graphics Preferences" window my screen model is set to "plug and play."  My resolution is set to 1920 x 1080.  

If I try to set the display to "Generic LCD Panel 1920 x 1080" and check the widescreen box, it doesnt give me a 1920 x 1080 option in the "resolution" drop down box.

The graphics card tab shows that it is using the "Intel-Experimental modesetting driver"

I need to be able to boot up correctly into 1920 x 1080 resolution with the display off.  How can I correct this?

Unfortunately, the new xorg drivers have to detect the resolution of the screen in order to make it available for selection. It sounds like the driver is operating correctly.

You can try to add other resolutions you want to your /etx/X11/xorg.conf in the appropriate section. Something like below. The newer xorg in Gutsy might just ignore this though...

```
   Section "Screen"
       Identifier    "Default Screen"
       Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
       Monitor        "Generic Monitor"
       DefaultDepth    24
   ...
       SubSection "Display"
           Depth        24
           ***Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"***
       EndSubSection
   EndSection
``` You might also try using the plain "Intel" driver rather than the experimental Intel driver.


> Wifi
I have the Atheros AR5006EG chipset.  I was able connect via wifi without any problems with a Live CD.  After I installed Ubuntu to hard drive, I have not been able to get wifi to work.  Network Manager is not showing any Wireless connection option.

Make sure to check the restricted drivers manager. If there is no option for your card there, you may need to install madwifi.

---

### Post by blk97tt on 2007-11-29
> **cyberdork33 said:**
> Unfortunately, the new xorg drivers have to detect the resolution of the screen in order to make it available for selection. It sounds like the driver is operating correctly.

You can try to add other resolutions you want to your /etx/X11/xorg.conf in the appropriate section. Something like below. The newer xorg in Gutsy might just ignore this though...

```
   Section "Screen"
       Identifier    "Default Screen"
       Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
       Monitor        "Generic Monitor"
       DefaultDepth    24
   ...
       SubSection "Display"
           Depth        24
           ***Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"***
       EndSubSection
   EndSection
``` You might also try using the plain "Intel" driver rather than the experimental Intel driver.




Make sure to check the restricted drivers manager. If there is no option for your card there, you may need to install madwifi.


I got my video problem resolved.  Here is what I did to do get my Mini to boot up when the display is powered off.  I modified my xorg.conf file with the following:

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        [COLOR="Red"]Option          "Monitor-TMDS-1" "dvi"[/COLOR]
EndSection

[COLOR="red"]Section "Monitor"
        Identifier      "dvi"
        Option          "Enable" "True"
EndSection[/COLOR]

My next project is to get my wifi working.

---

### Post by phrygius on 2007-12-11
@blk97tt:

Hello, I just recently put Ubuntu on a new Mac Mini too.  I tried hooking it up to my 1080p television for the first time last night and ran into some problems.  I notice it trying a few different resolutions during the boot process as well, but for me it does eventually settle on 1920x1080.

My problem is that the edges of the display are cut off (maybe 50 to 100 pixels on all four edges, just a guess).  Did you run into a similar problem at all?

Thanks,
phrygius

---

### Post by AriXmail on 2007-12-13
> **phrygius said:**
> @blk97tt:

Hello, I just recently put Ubuntu on a new Mac Mini too.  I tried hooking it up to my 1080p television for the first time last night and ran into some problems.  I notice it trying a few different resolutions during the boot process as well, but for me it does eventually settle on 1920x1080.

My problem is that the edges of the display are cut off (maybe 50 to 100 pixels on all four edges, just a guess).  Did you run into a similar problem at all?

Thanks,
phrygius

Hey phrygius,

Try going into your TVs menu options and changing some settings related to 16:9 and 4:3. I changed mine from wide zoom to full, which got rid of this problem for me :)

Good luck!

---

