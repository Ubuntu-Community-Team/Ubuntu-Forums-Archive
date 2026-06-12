---
title: "Extra mouse clicks whenever I slow down"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Dave in Maine on 2007-03-17
Hi all.

Gnome provides me with extraneous mouse clicks every once in a while.  I can be typing away and the typing cursor will jump back to where the mouse pointer is.  I have to be careful where I rest the mouse.  In menus the system may start processes that I didn't want.  Web browsing is odd since I go to pages I didn't intend to select.  (I'm at the fringe of the series of tubes where 3kBs is doing OK.)

I tried Alt-F2 and ran gconf-editor, but couldn't find a configuration parameter for clicks after pauses.  I don't actually know what to call it.  It could be "hover click" or "pause click" or "random click".

I'm using an HP pavilion ZV5000 notebook with P4.

Now let me introduce myself.  I just installed ubuntu yesterday and got the laptop modem working while trying to keep my mouse out of trouble.  I had Slackware  in the '90s but didn't use it that much.  Used Sun Solaris at work for decades.  When my disk drive failed recently I decided to go 100% Linux.  So far so good except the clicks.

THANKS!

---

### Post by tocleora on 2007-03-18
First, you might make sure it's not the mouse, try another mouse and see if you can duplicate the error with it.  I had a mouse that I swore was perfect until I replaced it.  I still honestly thought it was perfect until I just recently tried to go back to it (the new one is wireless and I thought it would be smarter for games - it wasn't).  Plus it's always just a good rule of thumb to verify if you can.  You probably already tried this but didn't want to leave anything out.

Second, if you're on a laptop, it might be your touchpad. Unlike windows, Gnome doesn't disable your touchpad when you plug in a mouse.  I'm constantly fighting that and unfortunately don't have an option in xorg.conf to turn it off (mouse runs both).  But I will constantly find myself running my thumb across it and if your touchpad is like mine (assuming of course you *have* a touchpad) you can even press on the pad area to make a click, so that could be causing your problem.  There are fixes for that on this forum I believe, if yours is the type listed in xorg.conf.  If you can't fix it, just have to try to avoid it, but at least you'd know what the problem was then.

Hope one of those helps, let us know if it doesn't, or even if it does we'd love to know. ;)

---

### Post by annda on 2007-03-18
install gsynaptics. it will let you configure your touchpad's sensitivity and more. (i've seen a few oversensitive hp laptop touchpads - on windows).

---

### Post by Dave in Maine on 2007-03-19
I'm still having trouble.

My bad on "mouse".  I don't own a mouse; I used "mouse" to differentiate the typing cursor from the pointer for selecting.  It's a touchpad.

I've paid more attention to the symptoms and the extra select comes most reliably after I use the touchpad's scrolling part.  Whenever I scroll I get the extra select.  Sometimes immediately and sometimes after 4 or 5 seconds.  Moving with the main part of the touchpad will generate extra selects less reliably but still fairly frequently.

I don't think the problem is touchpad sensitivity. I can tap the touchpad hard to select, but it takes effort.  ANY motion on the scolling section or SOME motions on the general touchpad still cause these extra selects.

I installed gsynaptics and added SHMconfig to my xorg.conf file as it requested.  Nothing I change in the new touchpad configuration GUI makes any difference unless I select "enable circular scrolling" which immediately locks the pointer so I get to re-boot without using the touchpad at all.  The default setting is to have "enable touchpad" NOT selected, so when I add "gsynaptics-init" to my session startup info the system reboots with NO touchpad and I have to re-re-boot and flail around with ed to get that line back out of .config/autostart.

I downloaded only gsynaptics_0.9.5-1ubuntu1_i386.deb .  More accurately, I downloaded the zipped tarball three times but each time Firefox reported successful completion but I had only 190k of a file that should be 348k so the archive manager failed to open it.  Am I missing an essential file?
 
I'm sure glad I used Solaris for so long; I cannot imagine a Windows user treading water as well as I can.:-s

I will borrow a USB mouse sometime this week and see how that works.  I will also try to find the file to which gsynaptics writes configuration info.  

Thanks for your suggestions so far.  Any more?

---

### Post by annda on 2007-03-19
a random idea: disable horizontal scrolling. 

other than that, i give up.

---

### Post by jordanmthomas on 2007-03-19
```
# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier          "Mouse3"
    Driver              "synaptics"

        Option      "Device"                "/dev/psaux"
    Option      "Protocol"              "auto-dev"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "560"  # comment out this entire line to disable horizontal scroll/click ability
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    Option      "EmulateMidButtonTime"  "70"
    Option      "VertScrollDelta"       "20"
    Option      "HorizScrollDelta"      "0"
[COLOR="Red"]    Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable[/COLOR]
    Option      "MinSpeed"              "0.3"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.015"
    Option      "EdgeMotionMinSpeed"    "200"
    Option      "EdgeMotionMaxSpeed"    "200"
    Option      "UpDownScrolling"       "1"
    Option      "LeftRightScrolling"    "0"
    Option      "CircularScrolling"     "0"

#Option         "SendCoreEvents"        "true"
#    Option             "Device"                "/dev/psaux"
#    Option             "Protocol"              "auto-dev"
#    Option             "HorizScrollDelta"      "0"
    Option              "SHMConfig"             "on"
    # For ALPS TouchPads
#    Option             "MaxSpeed"              "0.7"
#    Option             "MinSpeed"              "0.18"
#    Option             "AccelFactor"           "0.08"
#    Option             "TopEdge"               "120"
#    Option             "LeftEdge"              "120"
#    Option             "BottomEdge"            "830"
#    Option             "RightEdge"             "650"
#   Option              "FingerLow"             "25"
#    Option             "FingerHigh"            "30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection

```

From my xorg.conf.  Add the red line into your touchpad's section.  Note that if you do this your will have to click you button and you won't be able to tap on the pad to click.

---

### Post by Dave in Maine on 2007-03-19
THANKS jordanmthomas !  :)  Has anyone given you a star today? :KS 

[SIZE="4"][COLOR="Red"]The line in red fixed it perfectly.  THANKS![/COLOR][/SIZE]

(Actually THANKS to everyone who replied or even everyone who read the post and pondered a moment.)

Dave

---

