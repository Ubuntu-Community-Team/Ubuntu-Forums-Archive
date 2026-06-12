---
title: "No screen after install on 700mhz eMac"
date: 2005-04-16
forum: Apple PPC Users
---

### Post by leach on 2005-04-16
Hi, I'm try to install Ubuntu on to my eMac (the 700mhz original model) but after I'm done installing I boot it up it loads, makes the little drum noise and nothing appears on the screen. I'm new to linux and any help with this would greatly appreciated.

---

### Post by Brian McConnell on 2005-04-16
I had a 700mhz emac and ran Ubuntu on it last year....

So, your install is okay?
Boot-up seems normal until the part where you should have a graphical login screen?
If so, try option+apple+delete (the the delete next to the =/+ key) to retstart the X server. I know I've had this problem with Linux and mac before.....

---

### Post by Rxke on 2005-04-16
The drums sound signifies you got to the loginscreen, so everything is 'allright', except your videosettings, I guess.

are you sure, when installing, you did uncheck all videoresolutions that are higher than your monitor can handle? I a lot of cases, your graphics card can generate higher resolutions-refresh rates than your screen can, and the install process tries to use the highesst settings your card can manage, regardless of your monitor capabilities.

I'm quite new to Linux, too, so i can't help much further than to tell you you haave at least gotten to the loginscreen... Someone else will have to tell you how to set your monitorsettings after an install, when you can't see a thing:(

---

### Post by leach on 2005-04-16
[QUOTE=Brian McConnell]I had a 700mhz emac and ran Ubuntu on it last year

So, your install is okay?
Boot-up seems normal until the part where you should have a graphical login screen?
If so, try option+apple+delete (the the delete next to the =/+ key) to retstart the X server. I know I've had this problem with Linux and mac before.....[/QUOTE]


 ok, when the screen goes blank I press option+apple+delete and I get a brief look at the ubuntu text login for about one or two seconds and it goes blank again, what does this mean?

---

### Post by leach on 2005-04-16
Edit:  After pressing option+apple+delete quite a few times in a row I managed to bring up the error message:

"I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the Problem?"

then it shows me the X server output and I go back to the text login screen but now I can see it without it going away but still no GUI

---

### Post by leach on 2005-04-16
I've been trying for weeks and haven't been able to get Ubuntu or any other Linux distribution to run X windows on my eMac and through a lot of searching on Google it appears that just about everyone and their dog with the original 700mhz model eMac is having the same problem which leaves me to ask, has anyone at all been able to install Linux and run X windows on the original eMac? If you have please tell me what distribution you used and how you did it, as I'm beginning to think I'm wasting my time trying to run Linux on my eMac. Thanks.

---

### Post by Ptero-4 on 2005-04-18
[QUOTE=leach]I've been trying for weeks and haven't been able to get Ubuntu or any other Linux distribution to run X windows on my eMac and through a lot of searching on Google it appears that just about everyone and their dog with the original 700mhz model eMac is having the same problem which leaves me to ask, has anyone at all been able to install Linux and run X windows on the original eMac? If you have please tell me what distribution you used and how you did it, as I'm beginning to think I'm wasting my time trying to run Linux on my eMac. Thanks.[/QUOTE]
 I got a rather simple trick. Boot your eMac into OSX (Jaguar or Panther), install XDarwin (the x.org based one), then copy your /etc/X11/xorg.conf to a partition or disk that you can access from ubuntu. And then reboot into ubuntu and copy the xorg.conf on top of your original xorg.conf.

---

### Post by leach on 2005-04-18
Maybe I've messed up and didn't understand your instructions but I installed XDarwin and in appears I dont have the file X11 in the /etc/X11/xorg.conf directory, Ubuntu told me the same thing before when I tried to follow the instructions found here: [http://ubuntuforums.org/showthread.php?t=924](http://ubuntuforums.org/showthread.php?t=924)
But then again maybe I'm just messing up the instructions, this is my first experience with linux and I'm than just a tad confused.

---

### Post by Len on 2005-04-19
[http://ubuntuforums.org/archive/index.php/t-22898.html](http://ubuntuforums.org/archive/index.php/t-22898.html)

At least his Xorg.conf seems to work.

Make a backup of your original xorg.conf in case you edit some stuff you really shouldnt:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```
Edit your xorg.conf and try to fill in the horizontal sync and vertical refresh of the user that made that other post.
```
sudo nano /etc/X11/xorg.conf
```
You could also google around for the correct values. Do not try to make them up though,  you *could* damage your monitor (although I've never seen it happen).

---

### Post by dkg on 2005-06-10
[QUOTE=leach]Hi, I'm try to install Ubuntu on to my eMac (the 700mhz original model) but after I'm done installing I boot it up it loads, makes the little drum noise and nothing appears on the screen. I'm new to linux and any help with this would greatly appreciated.[/QUOTE]
 i am working with an eMac 700MHz with a nVidia GeForce2 MX graphics card as well, and i got the same behavior you described initially.

There are a couple problems, and i haven't been able to resolve them all:

[list]
[*]**which monitor to use?**
this machine uses the 'nv' x.org video driver.  with the GeForce2 MX, this driver supports output to either of the two monitor ports (there's the builtin monitor and the little weird apple-specific monitor port back behind the ethernet port, which you have to buy [one of these](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=M8639G/A) to connect a regular monitor).

The nv driver is supposed to autodetect the right one, but it doesn't (at least in my experience).  You can tell it to use the builtin monitor with this line in the "Device" section (Crtc stands for "cathode ray tube console", i believe):
```
	Option		"CrtcNumber" "1"
```


[*]**bitdepth on builtin Crtc**
i've found that using an external monitor (i.e. CrtcNumber "0") works just fine with 24bit color, so it's not like this driver is incapable of driving the card.

but when i use CrtcNumber "0", the video card does something really goofy with the video data.  i think the computer feeds the video data to the card as whatever bitdepth you specify, but the card seems to be stuck only displaying 8bit video.  You can work around that (in a very feeble and disappointing fashion) by telling the computer to only feed 8bit data to the card.  In the "Screen" section, add this line:
```
	DefaultDepth	8
```

[*]**non-existent HWCursor on builtin Crtc** 
when running through the builtin screen at 8bits, the mouse also doesn't show up.  This is because by default, the nv driver asks the card to display the mouse (this is known as "HWCursor").  You can ask the nv driver to explicitly draw the mouse with this line in the "Device" section:
```
	Option		"HWCursor" "off"
```
[/list] 

i'm attaching my xorg.conf to show you where i got to.  if you figure out how to make this machine work at 24bpp on the builtin monitor, please post how you did it!

---

### Post by wmarco on 2005-07-20
This is how to get Ubuntu's X.Org operating smoothly on an eMac 700Mhz with a NVidia Geforce 2MX:

1. First make sure you are using X.org (Ubuntu Hoary).
The older Ubuntu Warty distribution's XF86 nv driver is does not seem
to work at all (even with the proper mode lines).

2. A charming program called parse-edid by John Fremlin will allow you to get the necessary mode lines for your xorg.conf file that actually work with the built-in monitor. If you have the eMac listed above you can just see my xorg.config below, however I do suggest you read how I obtained those mode lines for future reference.


After installing Ubuntu Hoary do this:
 sudo apt-get install gcc
 wget [http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz](http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz)
 tar -xvvzf read-edid-1.4.1.tar.gz
 cd read-edid-1.4.1
 ./configure
 make parse-edid


Now that you have parse-edid compiled you can get the EDIDs (Extended Display Identification Data) of the built-in eMac monitor by pulling them off the /proc's folder representation of the Open Firmware device tree. 


 .parse-edid /proc/device-tree/pci/NVDA,Parent/NVDA,Display-A@0/EDID

The output from read-edid will look like this:

./parse-edid: parse-edid version 1.4.1
./parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "iMac"
        VendorName "APP"
        ModelName "iMac"
        # Block type: 2:0 3:fd
        HorizSync 71-73
        VertRefresh 70-140
        # Max dot clock (video bandwidth) 130 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1024x768"      # vfreq 88.995Hz, hfreq 72.086kHz
                DotClock        99.190000
                HTimings        1024 1072 1168 1376
                VTimings        768 769 772 810
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1280x960"      # vfreq 71.932Hz, hfreq 72.075kHz
                DotClock        122.240000
                HTimings        1280 1328 1424 1696
                VTimings        960 961 964 1002
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
EndSection

3.  Now you now have the necessary modes to drive the video card with. Just copy them over to your xorg.conf.



Here is an excerpt from a working and fully functional xorg.conf :



Section "Device"
 Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
 Driver  "nv"
 BusID  "PCI:0:16:0"
EndSection

Section "Monitor"
 Identifier "iMac"
 Option  "DPMS"
 HorizSync 71-73
 VertRefresh 70-140
 ModeLine     "1024x768"      99.190000 1024 1072 1168 1376 768 769 772 810 +hsync +vsync
 ModeLine "1280x960" 122.24 1280 1328 1424 1696 960 961 964 1002 +hsync +vsync

EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
 Monitor  "iMac"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x960" "1024x768"
 EndSubSection
EndSection

Good luck!

regards,

Warren Marco

      :roll:

---

### Post by dkg on 2005-07-22
wmarco, you are my new favorite person.  I didn't know about the read-edid package before (i'd seen it fly by during debian sarge installs, and never thought to look into it).  it's a very nice piece of work.

It didn't work for me immediately, because of the changes that i had made and reported earlier.  In particular, having set the CrtcNumber to 1 in the "Device" section caused X11 to continue to screw up.  Removing the CrtcNumber option and inserting the correct Monitor settings (thanks to parse-edid) lets the display work cleanly. 

And re-setting the DefaultDepth to 24 like you have it makes everything much prettier, of course, since it allows for more colors.

I think what was probably happening was that the nv driver tried to find a local monitor attached that met the specifications in my earlier, broken monitor configuration.  It rejected the builtin monitor because it didn't meet the specs, so it used the device plugged into the external port instead.

At any rate, this is now working for me and i'm very very pleased.  i've got both a functioning machine and a new tool (read-edid) to play with!

Thanks again, wmarco.

---

### Post by leach on 2005-08-13
I had given up on trying to get linux to run on my mac and forgot about this thread, then I was going through my bookmarks and found a link to this thread and decided to try again. However I am still having some trouble getting it to work. I've followed the instructions posted but whenever I try to edit or access Xorg.conf it tells me that it doesn't exist. I've downloaded the xorg.conf previously posted and edited it so it will work (hopefully). Now If I burnt this file to a CD could someone tell the commands I need to type in to move it from the CD to it's proper place? Or could someone tell me if I've been looking in the wrong directory for xorg.conf. /etc/X11/xorg.conf is where I've been looking. Thanks.

---

### Post by leach on 2005-08-13
I feel like a retard, this whole time as far back as April I've been typing in the directory wrong, instead of etc everytime I've typed in ect. I've only just noticed it by chance. It works now and I feel like a moron but thanks for all the help, I was just stumbling around in the dark.

---

### Post by ubonetu on 2005-10-06
I'm sorry, I posted here without reading the whole thread (sounds like you were close to a real solution).  I did find this on a French site and it works great on Ubuntu on my 700 eMac:

[ATTACH]2727[/ATTACH]

Just do control-alt-F1 to kill the X server and swap it for your /etc/xorg.conf.

You could also wget it:
```

wget www.wardbones.com/linux/xorg.conf_working.txt

```


Ubonetu

---

### Post by ubonetu on 2005-10-06
Okay, for anybody doing this without a burnable drive or an Ubuntu only system I thought it would be nice to put this up on my site.  Just get to a terminal in the /etc/X11/ directory and enter:
```

sudo wget www.wardbones.com/linux/xorg.conf_working.txt
sudo cp xorg.conf xorg.conf_orig
sudo cp xorg.conf_working.txt xorg.conf

```
now exit the rescue disk or reboot (actually, you won't need the "sudo"s if you use the rescue disk).

The only problem with this .conf file is I find the 3d rendering (like screensavers) to be very slow as compared to my PC laptop so I suspect that there is something about the driver or the .conf that could improve.  The good part is that it has 1280x960 resolution :) 

I hope this helps you all (it saved my system).
bones

---

### Post by Xamoelp on 2006-06-23
Hi, I've had Fedora Core 4 Running on my eMac 1.42ghz before today. Make sure you back up before you try it because it will wipe your HDD fully if you chose to format. Download fedora 4, but please not Fedoracore 5 is out so you could try that aswell. I ran it after the install for a couple of hours, got bored and Upgraded to Mac OSX again. I shall try 5 on an old iMac but I am not going to try it on the eMac.    If you don't want the hastle of buggering around with your main HDD, I suggest the use of an external Firewire HDD (firewire is bootable, USB/USB2 is not). On this you can (in theory) install the Linuxes you choose and run them without pissing Mac OS off, bear in mind, it will be slow running an OS off a firewire device, the eMac only has firewire 400, not 800 so this is slower than USB2. 

Hope this babble has been useful

---

### Post by 61_revisited on 2006-07-26
I'm having the same issue as the first poster in this thread but can't seem to resolve it.  I've only used one other Linux distribution (Yellow Dog) but it would let me set up the video settings after it errored initially.  I've read through this thread and several others but can't seem to get any of the solutions to work.

The only thing I've been able to do is access sudo nano /etc/x11/xorg.conf (after logging in through the text after ctrl- option- F1)

But it just comes up to a blank screen with command choices but seemingly nothing in the file itself. I'm totally unfamiliar with the commandline so I might be screwing that up.  If anyone feels like walking me through this, the help would be greatly appreciated.

](*,)

---

