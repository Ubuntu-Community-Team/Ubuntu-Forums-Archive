---
title: "Macbook Santa Rosa. Is 8.04 solving old problems?"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by fredscripts on 2008-04-26
Hi!!

I have installed 7.10 on my macbook Santa Rosa. I can't run compiz, nor use the touchpad (can't use right-button nor scrolling). I wonder if I upgrade to 8.04 I will be able to do that two things (and if not, what is worth with 8.04 in macbook to get it installed?) .

Thank you very much!!!!!!

---

### Post by sands on 2008-04-26
Mine is MacBook ver 3,1 SantaRosa
I Just installed Hardy

*Keyboard is working.. (Some function keys like brightness are not working..)
*Touchpad is working.. Need to be configured to get right click
*Desktop effects are enabled by default and are working fine..

There are other things that need to be configured.. I followed this guide..

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by PartisanEntity on 2008-04-26
Third gen MacBook here, sound is not working for me, and my external monitor is merely cloning. I am trying to resolve these two issues.

Touchpad is working, and wifi worked using ndiswrapper.

---

### Post by sands on 2008-04-26
I just configured sound.. This is what I did..

*added *options snd_hda_intel model=mbp3* to /etc/modprobe.d/options
*reboot
*update-initramfs -u
*reboot
*opened sound properties and there in switches tab, I enabled speaker..

Both Input from the mic & Output are working fine..
But the volume of input from the mic is very low.. when I speak infront of the mic, It is able to record well, with good volume, but if I am a little bit far from it.. I barely can hear the recording..
May be I should check some options.

---

### Post by cyberdork33 on 2008-04-27
> **sands said:**
> I just configured sound.. This is what I did..

*added *options snd_hda_intel model=mbp3* to /etc/modprobe.d/options
*reboot
*update-initramfs -u
*reboot
*opened sound properties and there in switches tab, I enabled speaker..

Both Input from the mic & Output are working fine..
But the volume of input from the mic is very low.. when I speak infront of the mic, It is able to record well, with good volume, but if I am a little bit far from it.. I barely can hear the recording..
May be I should check some options.
the way the recording is setup, there is a capture level and a Mic level. Make sure to adjust them both.

---

### Post by PartisanEntity on 2008-04-28
> **sands said:**
> I just configured sound.. This is what I did..

*added *options snd_hda_intel model=mbp3* to /etc/modprobe.d/options
*reboot
*update-initramfs -u
*reboot
*opened sound properties and there in switches tab, I enabled speaker..

Both Input from the mic & Output are working fine..
But the volume of input from the mic is very low.. when I speak infront of the mic, It is able to record well, with good volume, but if I am a little bit far from it.. I barely can hear the recording..
May be I should check some options.

Thanks very much, that worked!

---

### Post by fredscripts on 2008-05-07
Thanks for answering!!!


So then no problem with touchpad (scrolling with two fingers and that stuff) and with desktop effects like the cube?

---

### Post by fredscripts on 2008-05-11
> **fredscripts said:**
> Thanks for answering!!!


So then no problem with touchpad (scrolling with two fingers and that stuff) and with desktop effects like the cube?

Please!! I would like to know about that before updating to 8.04 on my macbook santa rosa.

---

### Post by sands on 2008-05-11
> **fredscripts said:**
> Please!! I would like to know about that before updating to 8.04 on my macbook santa rosa.

Initially only mouse move and left click worked..

To config right click & two finger scroll follow this, it worked fine..
But the usual right click (like, placing two fingers on the touchpad and clicking the button) won't work.
Both fingers should be placed on the touchpad at a time to make a right click.

two finger and click can be achieved by applying a patch to xorg.. I found somewhere in this forum. But I don't use that feature..


[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb)

---

### Post by sands on 2008-05-11
By the way, I did a fresh install, did not upgrade.
I think all this should work fine for upgrade too. :)

---

### Post by fredscripts on 2008-05-11
Thanks for answering!!

I configured xorg.conf file as that website tells on Ubuntu 7.10 hundreds of times to get touchpad with right click and scrolling and never got it working, maybe with 8.04...

And anyone with Macbook Santa Rosa and the cube stuff (desktop 3D effects) working in 8.04?

---

### Post by sands on 2008-05-11
> **fredscripts said:**
> Thanks for answering!!
And anyone with Macbook Santa Rosa and the cube stuff (desktop 3D effects) working in 8.04?

Desktop effects work by default. So is 3D cube..

---

### Post by fredscripts on 2008-06-12
Hi again!!!


I've updated from 7.10 to 8.04 today on the macbook with the updatemanager and the fist issue I have is that sound isn't working. I've added the line I had to on that /etc.../options file and enabled speackers in the Volume control, I have already the restricted formats package and no kind of sound is working.

Please anyone could help me??


Thanks in advance!! (Hope I can work out this issues because I fell I like 8.04 :))

---

### Post by sands on 2008-06-12
did u try
update-initramfs -u

---

### Post by fredscripts on 2008-06-12
Thanks for answering!!!

Yes I did it, I've found the solution: On the Volume Control, I had muted the "Front" bar, so now the sound is working :)


Thanks you very much!!

---

### Post by fredscripts on 2008-06-12
> **sands said:**
> Mine is MacBook ver 3,1 SantaRosa
I Just installed Hardy

*Keyboard is working.. (Some function keys like brightness are not working..)
*Touchpad is working.. Need to be configured to get right click
*Desktop effects are enabled by default and are working fine..

There are other things that need to be configured.. I followed this guide..

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

I configured the xorg file to get touchpad working for right clicking but now I can't manage to get right-clicking lol I thought it was holding two fingers on touchpad and then click the button but when holding two fingers on touchpad I get desktop switching stuff.

Anyone can help me with the basics touchpad ubuntu stuff? (Right click , scroll...)

Thanks in advance!!!!!

---

### Post by issih on 2008-06-12
The ubuntu wiki guides for the macbook tell you how to set up the touchpad so tapping on the actual pad (rather than the button) with two fingers or three fingers (dependent on configuration) acts as a right click/ middle click. If you want the version where you hold two fingers down and then click the button, look here :

[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

Works nicely here :)

P.S. this is my touchpad section from my xorg.conf, its for use with the patch from the thread above, 

```
Section "InputDevice"
        # updated 2007-12-07
        # use command "synclient -m 1" to see raw output
        # common stuff
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        
        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        
        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like

        # borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
      
        # don't change these or two finger tap stops working
        #Option          "TapButton2"            "3"
        #Option          "TapButton3"            "2"

        # must be commented out or normal tapping wont work
        Option         "TapButton1"            "0"
	Option          "TapButton2"            "0"
        Option          "TapButton3"            "0"

        # needed for disabled while typing fix  
        Option          "SHMConfig"             "on"

	# multitap rightclick  
	Option		"MultiFingerButton"	"2"
EndSection
```

---

### Post by cyberdork33 on 2008-06-12
Please create new threads for new problems / questions and mark your old ones as solved.

---

### Post by fredscripts on 2008-06-12
Thank you very much for answering!!

I've added the two lines: 

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

On the /etc/apt/sources.list file and added the 

```
Option		"MultiFingerButton"	"2"
```

On the touchpad section of xorg file.

I've rebooted but I don't see any change, I believe I must "Install" something, but don't know how.

Sorry for newbie questions!

Thank you very much for answering!!!

---

### Post by fredscripts on 2008-06-12
Oh!! Now it works, just had to install updates :)

But I have a little problem because pushing two fingers on touchpad switches between desktops, and that makes hard to actually right clicking, can I disable the switching desktop when I press two fingers option??


Thank you very much in advance!!

---

### Post by fredscripts on 2008-06-13
I've taken a look at the touchpad section of xorg, but I don't see any reference on "switching desktop" when two fingers are pressed, so I image that must be any desktop effects stuff, anyone know how to configure it??

Thank you very much in advance!

---

### Post by skiwithpete on 2008-06-13
I've got a macbook 4,1 and Ubuntu 8.04 installed.

It works kinda ok.  Sound/iPhoto/battery/fan/moupad issues really stop it from being the be all and end all.

P

---

### Post by cyberdork33 on 2008-06-13
> **fredscripts said:**
> I've taken a look at the touchpad section of xorg, but I don't see any reference on "switching desktop" when two fingers are pressed, so I image that must be any desktop effects stuff, anyone know how to configure it??

Thank you very much in advance!

It is part of the compiz configuration. Please start new threads for new questions.

---

### Post by sands on 2009-03-01
> **fredscripts said:**
> Oh!! Now it works, just had to install updates :)

But I have a little problem because pushing two fingers on touchpad switches between desktops, and that makes hard to actually right clicking, can I disable the switching desktop when I press two fingers option??


Thank you very much in advance!!


It has been a while, visiting this forum. Using Arch now :D
If you still have that desktop switching problem, goto compiz advanced settings and disable desktop wall, I guess.. I dont remember exactly the plugin, I disabled something and then it worked fine..

---

