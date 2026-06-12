---
title: "Using bcm5974 for tap click"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by jaspertandy on 2008-11-10
Hey,

I'm brand new to Ubuntu, so please be gentle.

I'm trying to enable tap-click in Ubuntu on a Macbook Pro but I can't seem to do it and I don't really know what I'm doing! I'm using Intrepid and the page at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) says I don't need to do anything other than install the package, but it's not working. I've tried adding some stuff to my xorg.conf but it didn't do anything!

output from /usr/src/bcm5974-1.1.0/scripts/bcm5974-diagnostics:

```

* Kernel version: 2.6.27-7-generic
* Synaptics version: 0.15.2-0ubuntu7
* USB device: Bus 006 Device 003: ID 05ac:0231 Apple, Inc.
* /lib/modules/2.6.27-7-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: no such file, good
* /lib/modules/2.6.27-7-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
Can't access shared memory area. SHMConfig disabled?
* synaptics: configuration NOT readable

```

any help would be really good, I'm very lost, but this is important to me :)

---

### Post by bryonak on 2008-11-10
Ok, trying to be gentle...

Follow [this here]("http://ubuntuforums.org/showpost.php?p=6137257&postcount=5") closely and please report.

The xorg.conf mentioned there refers to the file /etc/X11/xorg.conf. You can edit it by pressing Alt+F2 and typing 'gksudo gedit'. This will give you an "administrator text editor" so you can hit the 'open' button, go to File System -> etc -> X11 -> xorg.conf

To move files to restricted locations, press Alt+F2 and type 'gksudo nautilus' (guess what? "administrator file browser" ;)). Then navigate to where you wish.

Use gksudo applications with caution, you may break vital parts of the system. Best close them right after you're done with a specific task.

Any more questions/uncertainities? Just ask.

---

### Post by jaspertandy on 2008-11-10
hey, thanks :)

That didn't work - removed everything from xorg.conf that was to do with mice, added that file to /etc/hal/fdi/policy/ and restarted hal. Also restarted X just to be on the safe side. It didn't work. tap click and two-finger right click still isn't doing anything. Anything I can do to see what's going wrong?

---

### Post by cyberdork33 on 2008-11-10
> **jaspertandy said:**
> Hey,

I'm brand new to Ubuntu, so please be gentle.

I'm trying to enable tap-click in Ubuntu on a Macbook Pro but I can't seem to do it and I don't really know what I'm doing! I'm using Intrepid and the page at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) says I don't need to do anything other than install the package, but it's not working. I've tried adding some stuff to my xorg.conf but it didn't do anything!

output from /usr/src/bcm5974-1.1.0/scripts/bcm5974-diagnostics:

```

* Kernel version: 2.6.27-7-generic
* Synaptics version: 0.15.2-0ubuntu7
* USB device: Bus 006 Device 003: ID 05ac:0231 Apple, Inc.
* /lib/modules/2.6.27-7-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: no such file, good
* /lib/modules/2.6.27-7-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
Can't access shared memory area. SHMConfig disabled?
* synaptics: configuration NOT readable

```

any help would be really good, I'm very lost, but this is important to me :)

Well, you are in luck. The creator of that page is a regular user here. He should be along...

It would help if you could be more specific in identifying your Mac version number. You can see how to do this (as well as be directed to the proper documentation for you particular version) if you check the information in the "Before You Post" link in my signature.

---

### Post by jaspertandy on 2008-11-11
yeah, I have been lurking for a little while reading the monster of a thread that's linked to from the Penryn page on the wiki, but no-one seems to be having the same problem as me so I thought I'd sign up and ask instead. I went through most of the pages until I stopped understanding what people were talking about (I've got a fairly good understanding of unix and CLI, but obviously only through an OSX background) and nothing there even showed any sign of working (bearing in mind that the only sign I was looking for was tap-click!

---

### Post by kosumi68 on 2008-11-11
jespertandy,

If you installed fdi file from bryonak, here are two lines to modify and test:
```

 <merge key="input.x11_options.SHMConfig" type="string">true</merge>
 <merge key="input.x11_options.MaxTapMove" type="string">100</merge>

```

---

### Post by jaspertandy on 2008-11-11
ok, maybe I'm missing something here. Here's what I've done so far:

1. Installed bcm
2. Downloaded byronak's fdi file
3. modified as per kosumi
4. restarted hal

what am I missing? Do I need to do something with xorg.conf and restart X?

---

### Post by kosumi68 on 2008-11-11
> **jaspertandy said:**
> ok, maybe I'm missing something here. Here's what I've done so far:

1. Installed bcm
2. Downloaded byronak's fdi file
3. modified as per kosumi
4. restarted hal

what am I missing? Do I need to do something with xorg.conf and restart X?

If you would like to attach your xorg.conf here, that would be good, since the details of it is important here. And yes, restart X. :-)

---

### Post by jaspertandy on 2008-11-11
This includes what I copied from the link in my first post to try and enable tap clicking:

```

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto-dev"
	#Option		"CorePointer"

        # exclusive grabbing of device
        Option		"GrabEventDevice"	"1"

        # simulate right button
        Option		"MultiFingerButton"	"2"

        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"

        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" 

        # set to 0 if you don't want horizontal scrolling
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "40"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers
        # if you like to push hard, change to 30 or 40
        Option          "FingerLow"             "16"
        Option          "FingerHigh"            "80"
        Option          "FingerPress"           "256"

        # palm detect
        Option          "PalmDetect"             "0"
        Option          "PalmMinWidth"           "10"
        Option          "PalmMinZ"               "200"  

        # borders based on output from synclient
        # controls the edge scrolling
        # turned off by specifing the exact size /henrik
        Option          "LeftEdge"              "0"
        Option          "RightEdge"             "1280"
        Option          "TopEdge"               "0"
        Option          "BottomEdge"            "800"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8"
        # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2"
        # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "223"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        #Option          "TapButton2"             "0"
        #Option          "TapButton3"             "0"

        # must be commented out or normal tapping wont work
        #Option          "TapButton1"             "0"

        # not using corner buttons
        Option          "RTCornerButton"         "0"
        Option          "RBCornerButton"         "0"
        Option          "LTCornerButton"         "0"
        Option          "LBCornerButton"         "0"  

        # needed for disabled while typing fix  
        Option          "SHMConfig"              "true"

EndSection

```

thanks for posting - I really appreciate it :)

---

### Post by cyberdork33 on 2008-11-11
I believe you need to take that whole synaptics section out of our xorg.conf.

---

### Post by jaspertandy on 2008-11-11
it doesn't work either way, I've tried it with both.

---

### Post by kosumi68 on 2008-11-11
As cyberdork says, remove the whole synaptics section, and all references to it. Attached is an example of a working file (You may not want the keyboard config, but this is a test).

---

### Post by jaspertandy on 2008-11-11
copied your xorg.conf over mine and it's still not working. Didn't remove the keyboard stuff for testing purposes.

running the diagnostics still says that SHMC is disabled. Is there anything else I can take a look at to give a better idea of why it's not working?

---

### Post by kosumi68 on 2008-11-11
> **jaspertandy said:**
> copied your xorg.conf over mine and it's still not working. Didn't remove the keyboard stuff for testing purposes.

running the diagnostics still says that SHMC is disabled. Is there anything else I can take a look at to give a better idea of why it's not working?

Did you reboot after doing this?

---

### Post by bryonak on 2008-11-11
Well... I overlooked a few issues...

1. Remove **everything** about input devices from your xorg.conf. Input configuration is now completely based on hal, and the xorg.conf will only interfere with it. It is now mainly used for graphics.
(personally I liked the xorg.conf better than the hal XML files, but that's the way Xorg is going)

2. It is not recommended to enable SHMConfig. This options shares your touchpads RAM space with other user processes, so you can use gsynaptics, syndaemon etc to configure your touchpad... which you can perfectly do via hal anyway. SHMConfig is considered a huge security hole.

3. My fdi file is expecting the appletouch driver (MacbookPro 3.1).
You can see this if you look at lines 4 and 5 (the "match" entries)...
Although I thought that should work for newer models as well (since "appletouch" should be in the product identifier there as well), I don't know what to look for exactly on a Penryn Mac, but you might want to try matching other keys ("info.xxx" contains="bcm5974"). Perhaps someone who owns a newer Macbook knows what exactly you have to write there...

---

### Post by kosumi68 on 2008-11-11
> **bryonak said:**
> 
3. My fdi file is expecting the appletouch driver (MacbookPro 3.1).


Yes! I overlooked this one, too. Change 'appletouch' to 'bcm5974' in your /etc/hal/fdi/policy/appletouch.fdi file, and you should be good.

---

### Post by jaspertandy on 2008-11-11
> **kosumi68 said:**
> Did you reboot after doing this?

I restarted X - is a full reboot necessary?

> **bryonak said:**
> Well... I overlooked a few issues...

3. My fdi file is expecting the appletouch driver (MacbookPro 3.1).
You can see this if you look at lines 4 and 5 (the "match" entries)...
Although I thought that should work for newer models as well (since "appletouch" should be in the product identifier there as well), I don't know what to look for exactly on a Penryn Mac, but you might want to try matching other keys ("info.xxx" contains="bcm5974"). Perhaps someone who owns a newer Macbook knows what exactly you have to write there...

sorry, are you saying that I need to wrap another <match...></match> around all the <merge>....</merge> nodes but within the existing info.product one? when you say info.xxx, what are the possible things it could be? Is there any documentation I can read on this?

edit: ahh, just saw kosumi's most recent one - rebooting now. Will post results.

---

### Post by jaspertandy on 2008-11-11
ooook, so now it seems that 2 finger right click works, but moving the cursor with the trackpad is no longer working! :/

any ideas?

actually, everything's working but it's really intermittent!

---

### Post by bryonak on 2008-11-11
Now it's tweaking time...

Maybe the pressure ranges are completely different with the bcm pads, or you should use the options I have set to 0 in my config.

For some documentation, open a terminal and type 'man synaptics'
There's a nice [overview here]("http://web.telia.com/~u89404340/touchpad/") and for extensive tweaking tips, you might want to look into the [gentoo wiki]("http://en.gentoo-wiki.com/wiki/Main_Page"), (those people do nothing else all the time ;))...

To check for errors, type 'dmesg | tail' in a terminal, this will give you the recent entries in the dmesg log file.

I'm sorry I can't give you concrete solutions, but that's the problem with closed, new hardware - no one in the FOSS community knows how it works until they try it out.

If you have a good, working fdi file, you might want to upload it for other Penryn users.

---

### Post by kosumi68 on 2008-11-11
> **bryonak said:**
> Now it's tweaking time...


It seems the real problem was only the xorg.conf file. The initial settings for bcm5974 are fine, except the tapping needs to be turned on. Copy the /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi file to /etc/hal/fdi/policy, remove (or move away) the appletouch.fdi file, and change these lines in 11-x11-synaptics.fdi:
```

<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">3</merge>
<merge key="input.x11_options.TapButton3" type="string">2</merge>

```

---

### Post by jaspertandy on 2008-11-11
cool, cheers for your help. It's weird, I've managed to make it work by dragging my finger in from the edges (like just off the trackpad) to make it work. I'll have a play around with it tonight, but if you know what could cause this, I'd appreciate it - I'm just blindly changing stuff and restarting hal right now. FUN!

edit: sneaky kosumi posted again! I'll try that in a bit! thanks.

---

### Post by bryonak on 2008-11-11
Thanks kosumi, I wasn't aware that this was already preconfigured!


> ...but that's the problem with closed, new hardware - no one in the FOSS community knows how it works until they try it out.
Seems like it has been tried out.

Just a quick note about SHMConfig... if you want to configure it via gsynaptics, you have to leave this on (though I don't know if gsynaptics works with the new Xorg). This was a very useful tool when you had to restart the whole X server to make changes take action, but now you just type 'sudo /etc/init.d/hal restart'
It is strongly recommended to leave SHMConfig off... obviously not if it breaks things, so could you report on whether it works with it turned on/off for you?


kosumi might be sneaky, but he's a nice dude with great knowledge nevertheless ;P

---

### Post by kosumi68 on 2008-11-11
> **bryonak said:**
> Thanks kosumi, I wasn't aware that this was already preconfigured!


Intrepid works very well out-of-the-box for the MacBookPro4,1 and MacBookAir, which one notices when running the live CD. The most problems we see on these pages today actually stem from upgrading an existing installation.

> 
It is strongly recommended to leave SHMConfig off... obviously not if it breaks things, so could you report on whether it works with it turned on/off for you?


Yes, it should eventually be turned off completely, but as of today, there are no good alternative ways to examine the trackpad state, and in the interest of reducing the number of things that can go wrong, I believe it is best to turn it on. Once all checks are done, one can start deviating.

> 
kosumi might be sneaky, but he's a nice dude with great knowledge nevertheless ;P


I will try to take that as a compliment ;-)

---

### Post by jaspertandy on 2008-11-11
OK, I'm so nearly there with this. I promise. I've figured out something - if I press down on the trackpad any heavier than so very lightly, it ignores the input - so I don't get a tap or a cursor move or anything. Does anyone know offhand what setting I need to alter for this? I've tried the only ones I thought it could be and it hasn't worked. If you could help, I'll be your friend forever!

---

### Post by jaspertandy on 2008-11-11
woohoo! told you I was near. Coupla tweekies and a restart and it's working perfick! Thanks so much for your help guys. I owe you all a virtual beer or something less lame.

---

### Post by kosumi68 on 2008-11-11
Did you copy the default settings in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi over to /etc/hal/fdi/policy? It is the fastest way forward, trust me. It sounds like you are experiencing problems with FingerPress.

---

### Post by jaspertandy on 2008-11-11
yeah, I did as you suggested and copied 11-x11-synaptics.fdi and switched out my old one. Now it's working pretty well.

Ahhh, now onto playing around with all the other cool new stuff on this thing!!

---

### Post by Craigular.B on 2008-12-05
Hi jaspertandy-

I noticed you were having a lot of the same issues I am, and I was wondering if you could post the contents of your /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi file? Right now I'm still using the appletouch.fdi file because with exams coming up I don't have the time for tweaking constantly. I'd appreciate any help you can give me.

Thanks a lot!
-Craig

---

### Post by jaspertandy on 2008-12-06
hey Craigular. I'm probably not the best person to ask for this sort of thing, as it seemed to start working randomly. Nonetheless, I followed all advice in this thread and it's working! As you requested, my 11-x11-synaptics.fdi file:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

Hope it's of some help to you. I think it could do with a bit of tweaking; it gets a little over zealous with light touches, but I haven't time to be testing it and figuring out the best settings for me at the moment. If you manage to sort it out, post your settings back here. I'll do the same.

---

### Post by Craigular.B on 2008-12-10
Hi again, I'm still having issues...I can't tap-to-click (or "right-click"), and when I run the bcm diagnostics it says this:

```
* Kernel version: 2.6.27-9-generic
* Synaptics version: 0.15.2-0ubuntu7-mactel1
* USB device: Bus 003 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard Bus 006 Device 003: ID 05ac:0230 Apple, Inc.
* /lib/modules/2.6.27-9-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: no such file, good
* /lib/modules/2.6.27-9-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974

```

I have the 11-x11-synaptics.fdi file in my policy folder, and I'm pretty sure I followed all the instructions in this thread...It just doesn't want to work.

-Craig

---

