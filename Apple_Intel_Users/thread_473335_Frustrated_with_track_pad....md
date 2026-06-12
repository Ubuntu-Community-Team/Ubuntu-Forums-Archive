---
title: "Frustrated with track pad..."
date: 2007-06-13
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-13
I've been trying to get this set up for hours... I installed qsynaptics, edited xorg.conf, etc., but nothing seems to work.

All I really want at this point is two finger right clicking and maybe two finger scrolling. Anyone have any suggestions?

---

### Post by alloydwhitlock on 2007-06-14
I can understand the trackpad frustration, since I finally got mine to where I like it. 

If you post a copy of your Synaptics xorg config and we can check if there is an issue with the settings you are trying to use.

---

### Post by SectionThree on 2007-06-14
I've yet to get two-fingered scrolling down, but I got three-finger right-clicking and two-finger middle-clicking without having to set anything up.

---

### Post by ronocdh on 2007-06-14
> **alloydwhitlock said:**
> I can understand the trackpad frustration, since I finally got mine to where I like it. 

If you post a copy of your Synaptics xorg config and we can check if there is an issue with the settings you are trying to use.
Seconded. Also, the first couple times I tried to set up my trackpad, I kept forgetting that the driver had to be running... I ended up adding the terminal command **qsynaptics** to my startup scripts so it's enabled as soon as I log in.

---

### Post by Torajima on 2007-06-14
> **ronocdh said:**
> Seconded. Also, the first couple times I tried to set up my trackpad, I kept forgetting that the driver had to be running... I ended up adding the terminal command **qsynaptics** to my startup scripts so it's enabled as soon as I log in.

How do I edit my startup script? Yeah, I'm a bit of a newbie...

Here's the synaptics bit from my config file (this one is pretty long, I've tried shorter ones):
[COLOR="Blue"]
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true" # comment out in Gutsy for better performance 
        # Option "CorePointer" # use in Gutsy for better performance
        Option "Device" "/dev/input/mouse1"
        Option "Protocol" "auto-dev"
        Option "LeftEdge" "20"
        Option "RightEdge" "1000"
        Option "TopEdge" "17"
        Option "BottomEdge" "700"
        Option "FingerLow" "5"
        Option "FingerHigh" "7"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "180"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "VertScrollDelta" "7"
# turn off horizontal scrolling
        #Option "HorizScrollDelta" "0"
        Option "MinSpeed" "0.79"
        Option "MaxSpeed" "0.88"
        Option "AccelFactor" "0.0015"
        Option "LeftRightRepeat" "0"
        Option "UpDownRepeat" "0"
        Option "UpDownScrolling" "on"
# turn off corner buttons
        Option "RTCornerButton" "0"
        Option "RBCornerButton" "0"
        Option "LTCornerButton" "0"
        Option "LBCornerButton" "0"
# edge motion
        Option "EdgeMotionUseAlways" "0"
        Option "EdgeMotionMinZ" "25"
        Option "EdgeMotionMaxZ" "60"
        Option "EdgeMotionMinSpeed" "150"
        Option "EdgeMotionMaxSpeed" "200"
        Option "SHMConfig" "on"
EndSection[/COLOR]

---

### Post by pveith on 2007-06-14
To automatically start a script when you log into your Gnome-Session just use System -> Preferences -> Sessions.
Create a new "Startprogram" and select your script as command. That's it. Now the next time you log in, your script should be executed.

(i have a german Ubuntu, so it might be that the translations are not acurate. But it should be easy to find.)

---

### Post by thully on 2007-06-14
Try the new instructions on the Ubuntu wiki - I was working on it and just figured out how to make it somewhat better...

---

### Post by Torajima on 2007-06-14
> **thully said:**
> Try the new instructions on the Ubuntu wiki - I was working on it and just figured out how to make it somewhat better...

You didn't post a link, so I'm not sure if they are your instructions or not...

But I modified xorg again and now my track pad is completely dead! :(

What really worries me is that it has remained dead after I've undid all the changes...

---

### Post by thully on 2007-06-14
The track pad shouldn't be dead if you follow the very latest instructions that I posted on the wiki.  If it is dead, it is most likely because  the CorePointer/SendCoreEvents are configured incorrectly.  If you follow the steps on the wiki to fix those parts, it should work.

---

### Post by Torajima on 2007-06-14
> **thully said:**
> The track pad shouldn't be dead if you follow the very latest instructions that I posted on the wiki.  If it is dead, it is most likely because  the CorePointer/SendCoreEvents are configured incorrectly.  If you follow the steps on the wiki to fix those parts, it should work.

I'm sorry, but which wiki are you referring to?

I was able to get the track pad working again, but it still isn't work right.

---

### Post by thully on 2007-06-14
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) is the address...

---

### Post by Torajima on 2007-06-14
> **thully said:**
> [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) is the address...

Thanks. Unfortunately, even after doing what you suggested, two finger tapping still isn't working.

---

### Post by thully on 2007-06-14
Make sure the "TapButton" settings are correct as noted in the wiki.  Also, make sure gsynaptics/ksynaptics/qsynaptics  is NOT installed - you don't need it if you configure everything in the xorg.conf (as the wiki entry suggests). Those settings should make twp-finger tap right-click and three-finger tap middle-click.

---

### Post by Torajima on 2007-06-14
Horizontal scrolling is still working (and it looks like it's turned off in the xorg file), so I don't think it's reading those settings at all.

One strange thing I've noticed, under preferences my keyboard layout is set to generic PC, not Mac. When I try to change it to Mac, I get an error.

---

