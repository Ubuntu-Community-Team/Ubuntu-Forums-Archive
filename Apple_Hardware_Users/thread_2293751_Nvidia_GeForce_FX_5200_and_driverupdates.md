---
title: "Nvidia GeForce FX 5200 and driverupdates"
date: 2015-09-07
forum: Apple Hardware Users
---

### Post by dhiffucium on 2015-09-07
The Nouveau driver doesn't work for the Nvidia Geforce FX 5200 graphics card, so I want to use the driverupdates-powerpc64 boot option to load the nvidia proprietary driver from a cd. How can I get a PowerPC version of that driver (I think I need the nvidia-173 driver?) and what do I have do do with it to make the live cd load this driver?

---

### Post by Bashing-om on 2015-09-07
dhiffucium; Yuk !

You may have a problem - old hardware no longer supported Nvidia -
It has to be 173 series because it's the last to support Geforce 5/FX cards .... The 173.xx proprietary driver is not going to work on Ubuntu 14,04 + with HWE nor 15.04. The Xserver is too new and Nvidia is not releasing any new versions of the 173 series.
The latest version of Ubuntu that will support the 173.xx driver is Ubuntu 14.04.1 .
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

Sad news
[INDENT][INDENT]but that is the way it is
[/INDENT][/INDENT]

---

### Post by dhiffucium on 2015-09-08
So all I can do is wait and hope for the Nouveau developers to figure out how this thing works.

---

### Post by Bashing-om on 2015-09-08
dhiffucium; Hello;

I am not familiar with Macs, but the open source driver 'nouveau' should work fine, Maybe clean up the system and (re-)install the nouveau driver ? If you want to use the proprietary 173 driver one can (RE-)install the operating system on release 14.04.[color=red]1[/color]; as that kernel and Xserver stack does support that driver. Release 14.04.1 will have full support 'til April of 2019 .

All in what you want to do
[INDENT][INDENT][INDENT]is how we do it
[/INDENT][/INDENT][/INDENT]

---

### Post by dhiffucium on 2015-09-09
No, the nouveau driver does not work. The screen freezes before any graphics show up when attempting to install Ubuntu Mate from the live cd. 

By adding 'nouveau.modeset=0', which disables nouveau, to the boot arguments I can get to a desktop with 8-bit color-depth and the colors inverted (no, not really inverted; the light grey becomes magenta or black, sometimes green, and the dark green, almost grey, becomes brown, light green becomes beige, white text stays white, the mouse cursor is dark blue and everything has a red background/outline that makes it even harder to read). [https://www.dropbox.com/s/cnyg63t8vwyc6pr/2015-09-09%2013.15.39.jpg?dl=0](https://www.dropbox.com/s/cnyg63t8vwyc6pr/2015-09-09%2013.15.39.jpg?dl=0)
The screensaver shows the floating Mate logos in red, blue, cyan, magenta and white, on a black background. [https://youtu.be/GnMqpjqRj_s](https://youtu.be/GnMqpjqRj_s)

According to [http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/) the nouveau driver doesn't work on the NV34.

---

### Post by dhiffucium on 2015-09-15
I typed "live video=offb:off nouveau.modeset=0 single" at the yaboot prompt, waited a few minutes after the crazy fan noise stopped and then, blindly, typed "modprobe nvidiafb mode_option=1600x1200-32" and the screen changed and the text appeared on the screen. Then I typed (not blindly anymore) "systemctl default" and it finally worked ok. The installer doesn't work in 8 bit color, so the mode_option is important. I managed to install Ubuntu MATE, but it still has append="quiet splash video=offb:off single" in /etc/yaboot.conf so I have to repeat the blind typing (but now with the correct keyboard layout, making it a lot easier) every time I reboot. What do I put instead to make it work?

Also, the colours are still not quite right, but the system is mostly usable anyway. See this screenshot: [https://drive.google.com/open?id=0BzkXalizNXD2NHlyTjEzekxRd1E](https://drive.google.com/open?id=0BzkXalizNXD2NHlyTjEzekxRd1E)

---

### Post by Bashing-om on 2015-09-15
dhiffucium; Hey ;

Mind you I do not know Macs;
Have you seen:
[http://ubuntuforums.org/showthread.php?t=2131644&page=5](http://ubuntuforums.org/showthread.php?t=2131644&page=5)

Looks to be an informative thread coping with Nvidia hardware on Macs.

[INDENT][INDENT]maybe ?
[/INDENT][/INDENT]

---

### Post by dhiffucium on 2015-09-16
This is my Xorg.0.log after the modprobe. I don't know why it refers to NV32 when it is a NV34 card. 

[ATTACH]264451[/ATTACH]

---

### Post by Bashing-om on 2015-09-16
> 
<snip>
91.479] (==) Matched nvidia as autoconfigured driver 0
<snip>
91.481] (II) LoadModule: "nvidia"
[    91.492] (WW) Warning, couldn't open module nvidia
[    91.492] (II) UnloadModule: "nvidia"
[    91.492] (II) Unloading nvidia
[    91.492] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    91.492] (II) LoadModule: "nouveau"
<snip>

For starters, while I study the remainder of the file, tells us that the driver did not build. Soon we must consider purging Nvidia and rebuilding an appropriate driver.

I be back to the keyboard soonest I am able, a couple of hours .

[INDENT][INDENT]got to have the driver
[/INDENT][/INDENT]

---

### Post by abtabt on 2015-09-16
> **dhiffucium said:**
> I typed "live video=offb:off nouveau.modeset=0 single" at the yaboot prompt, waited a few minutes after the crazy fan noise stopped and then, blindly, typed "modprobe nvidiafb mode_option=1600x1200-32" and the screen changed and the text appeared on the screen. Then I typed (not blindly anymore) "systemctl default" and it finally worked ok. The installer doesn't work in 8 bit color, so the mode_option is important. I managed to install Ubuntu MATE, but it still has append="quiet splash video=offb:off single" in /etc/yaboot.conf so I have to repeat the blind typing (but now with the correct keyboard layout, making it a lot easier) every time I reboot. What do I put instead to make it work?

Also, the colours are still not quite right, but the system is mostly usable anyway. See this screenshot: [https://drive.google.com/open?id=0BzkXalizNXD2NHlyTjEzekxRd1E](https://drive.google.com/open?id=0BzkXalizNXD2NHlyTjEzekxRd1E)


hi start with to add in yaboot

append="quiet splash video=offb:off nomodeset"      

and do 

sudo ybin -v


unhasch

nvidiafb in   etc/modprobe.d/fbdev-blacklist.conf  and in      etc/modprobe.d/blacklist-framebuffer.conf    
make a

put this in xorg.conf

  Section "Screen"
  Identifier "Screen0"
  DefaultDepth  16
 Modes   "1024x768"
EndSection


then reboot 

and if you get a god desktop feel free to change the values

if all ok can you post hw file 

sudo lshw -short

---

### Post by Bashing-om on 2015-09-16
dhiffucium; Hey !

I have to question if Nvidia is even a part in this equation.
I find no direct reference to Nvidia - maybe I missed it (?) - I had expected to see the hardware identified - in your Xorg.0.log file.
What we have:
> 
90.825] (--) PCI:*(0:240:16:0) 10de:0321:10de:0010 rev 161, Mem @ 0x91000000/16777216, 0x98000000/134217728, BIOS @ 0x????????/131072
 shows one display source. Let's identity what it is:
```

lspci -nnk | grep -iA3 vga
sudo ubuntu-drivers devices

```
With the 'lspci' output we cross reference to what the system has set in " /usr/share/misc/pci.ids " .

Now once we know what the hardware is, then go about our way to install the graphics driver.

[INDENT][INDENT]just my thoughts on the matter
[/INDENT][/INDENT]

---

### Post by dhiffucium on 2015-09-17
> **Bashing-om said:**
> dhiffucium; Hey !

I have to question if Nvidia is even a part in this equation.
I find no direct reference to Nvidia - maybe I missed it (?) - I had expected to see the hardware identified - in your Xorg.0.log file.
What we have:
 shows one display source. Let's identity what it is:
```

lspci -nnk | grep -iA3 vga
sudo ubuntu-drivers devices

```
With the 'lspci' output we cross reference to what the system has set in " /usr/share/misc/pci.ids " .

Now once we know what the hardware is, then go about our way to install the graphics driver.
[INDENT][INDENT]just my thoughts on the matter
[/INDENT]
[/INDENT]

offensiv@tidning07:~$ lspci -nnk | grep -iA3 vga
0000:f0:10.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5200 Ultra] [10de:0321] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:0010]
    Kernel driver in use: nvidiafb
0001:00:00.0 Host bridge [0600]: Apple Inc. U4 PCIe [106b:0056]
offensiv@tidning07:~$ sudo ubuntu-drivers devices
[sudo] password for offensiv: 
offensiv@tidning07:~$

---

### Post by dhiffucium on 2015-09-17
> **abtabt said:**
> hi start with to add in yaboot

append="quiet splash video=offb:off nomodeset"      

and do 

sudo ybin -v


unhasch

nvidiafb in   etc/modprobe.d/fbdev-blacklist.conf  and in      etc/modprobe.d/blacklist-framebuffer.conf    
make a

put this in xorg.conf

  Section "Screen"
  Identifier "Screen0"
  DefaultDepth  16
 Modes   "1024x768"
EndSection


then reboot 

and if you get a god desktop feel free to change the values

if all ok can you post hw file 

sudo lshw -short

I changed the yaboot conf and ybin. 
I commented out "blacklist nvidiafb" in blacklist-framebuffer.conf. 
I created a new file named 10-screen.conf in /usr/share/X11/xorg.conf.d with your configuration and rebooted. 
It didn't work because Modes can't be in the Screen section. It goes in the Display subsection. I added it there and then it worked. 
I did some other changes and now the file looks like this: 
```
Section "Screen"
Identifier "Screen0"
DefaultDepth 24
SubSection "Display"
Modes "1600x1200"
EndSubSection
EndSection

```
There is still something weird with the colours. It looks like before, but X starts automatically without any modprobe.

---

### Post by Bashing-om on 2015-09-17
dhiffucium; And ....

We have come full circle back to old hardware:
> 
The 173.14.xx driver supports the following set of GPUs: 
Note: Support for the 173.14.xx series is discontinued. No further releases from this series are planned.
<snip>
GeForce FX 5200 Ultra	0x0321

Nvidia: It has to be 173 series because it's the last to support Geforce 5/FX cards .... The 173.xx proprietary driver is not going to work on Ubuntu 14,04.3/15.04. The Xserver is too new and Nvidia is not releasing any new versions of the 173 series.
The latest version of Ubuntu that will support the 173.xx driver is Ubuntu 14.04.[color=red]1[/color]

Not to say one could not tweak on Nvidia's config file and get something workable, but I have little experience doing so in such a situation as this is.

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by abtabt on 2015-09-17
hi 

> **dhiffucium said:**
> I changed the yaboot conf and ybin. 
I commented out "blacklist nvidiafb" in blacklist-framebuffer.conf. 
I created a new file named 10-screen.conf in /usr/share/X11/xorg.conf.d with your configuration and rebooted. 
It didn't work because Modes can't be in the Screen section. It goes in the Display subsection. I added it there and then it worked. 
I did some other changes and now the file looks like this: 
```
Section "Screen"
Identifier "Screen0"
DefaultDepth 24
SubSection "Display"
Modes "1600x1200"
EndSubSection
EndSection

```
There is still something weird with the colours. It looks like before, but X starts automatically without any modprobe.

post our  Xorg.0.log  (  for  Modes "1600x1200"    DefaultDepth 24)

 i never  use  /usr/share/X11/xorg.conf.d

i only use       /etc/X11/xorg.conf          (if xorg.conf not exist make it)

did you not have    /etc/modprobe.d/fbdev-blacklist.conf  ?????

did you tried 

DefaultDepth 16 , Modes "1024x768"    ??? 

post our  Xorg.0.log   (DefaultDepth 16 , Modes "1024x768" )



whats ubuntu      Lubuntu,Ubuntu ,Mate  version ????

---

### Post by Saml01 on 2015-09-18
I followed the instructions here: [[PPC] Power Mac G5 + Nvidia Card Guide - Page 2]("http://ubuntuforums.org/showthread.php?t=2292210&page=2&p=13358333&posted=1#post13358333") for my Imac G5 and so far its been pretty stable with nouveau. Might be something worth trying.

---

### Post by dhiffucium on 2015-09-21
> **abtabt said:**
> hi 



post our  Xorg.0.log  (  for  Modes "1600x1200"    DefaultDepth 24)
[ATTACH]264564[/ATTACH]> **abtabt said:**
> 
 i never  use  /usr/share/X11/xorg.conf.d

i only use       /etc/X11/xorg.conf          (if xorg.conf not exist make it)
That is OK, it will produce the same result. > **abtabt said:**
> 
did you not have    /etc/modprobe.d/fbdev-blacklist.conf  ?????
Yes, but there is nothing about nvidiafb in that one. > **abtabt said:**
> 
did you tried 

DefaultDepth 16 , Modes "1024x768"    ??? 
Yes, it was the same but with different resolution. > **abtabt said:**
> 
post our  Xorg.0.log   (DefaultDepth 16 , Modes "1024x768" )
[ATTACH]264568[/ATTACH]> **abtabt said:**
> 


whats ubuntu      Lubuntu,Ubuntu ,Mate  version ????
This is Ubuntu MATE 15.04.

---

### Post by rsavage on 2015-09-21
> **dhiffucium said:**
> 
This is Ubuntu MATE 15.04.

Well that's your problem right there.

---

### Post by dhiffucium on 2015-09-21
[ATTACH=CONFIG]264566[/ATTACH]
This is a PNG image. 
[ATTACH=CONFIG]264565[/ATTACH]
This is a SVG version of the same image in the same web browser. 

Why can I have the correct colors on vector graphics but not on raster graphics? The raster graphics always has 100 percent in the blue channel, but there is no problem with vector graphics.

---

### Post by dhiffucium on 2015-09-21
> **rsavage said:**
> Well that's your problem right there.

That was not a very helpful answer. Can you elaborate? Are you suggesting that I re-install Mac OS X 10.5.8? Because that is the latest version that will run on this processor.

---

### Post by rsavage on 2015-09-21
> **dhiffucium said:**
> That was not a very helpful answer. Can you elaborate? Are you suggesting that I re-install Mac OS X 10.5.8? Because that is the latest version that will run on this processor.

Ubuntu-mate 15.04 for PowerPC should never have been released.  It is a complete joke that it was, considering it has a critical bug i.e. it is missing the yaboot package.  I'm amazed you got it to install and boot at all.  Having bugs on a release is fine, it has been the way with all recent PowerPC releases, but in the past we've always documented them and tried to provide a workaround.  Ubuntu-mate did not do this.  That is why there is no link to 15.04 on any of the PowerPC documentation.

Having said that, if you are selfish and stuck in the past then Ubuntu-mate is the distro for you - you'll fit right in with the majority of its user base.

---

### Post by dhiffucium on 2015-09-22
> **rsavage said:**
> Ubuntu-mate 15.04 for PowerPC should never have been released.  It is a complete joke that it was, considering it has a critical bug i.e. it is missing the yaboot package.  I'm amazed you got it to install and boot at all.  Having bugs on a release is fine, it has been the way with all recent PowerPC releases, but in the past we've always documented them and tried to provide a workaround.  Ubuntu-mate did not do this.  That is why there is no link to 15.04 on any of the PowerPC documentation.

Having said that, if you are selfish and stuck in the past then Ubuntu-mate is the distro for you - you'll fit right in with the majority of its user base.
It is not missing the yaboot package. I had no problem with booting and installing once I got the color depth high enough for Ubiquity to work. This is only a graphics problem, yaboot is working. 

If you have a problem with how Ubuntu Mate documents bugs, I suggest you discuss it with Martin Wimpress. He is very reasonable.

---

### Post by abtabt on 2015-09-22
dhiffucium

15.04 Ubuntu-mate PPC 

did have some tubble with Xorg  and mesa (downgrade xorg etc helpt but  !!!)

so my sugg is down load Lubuntu 12.04 live cd and try it, or 14.04 live cd  ( but 12.04 still active and i use it more then 14.04 )

or make USB or FW disk live      (dd copy) 

if same Xorg trubble then the card dont like linux 

if you have OSX installed its sometime need to be set like 1024x768 tusend couler and you must have same on the linuxside

when you use fbdev, nvidiafb etc

---

