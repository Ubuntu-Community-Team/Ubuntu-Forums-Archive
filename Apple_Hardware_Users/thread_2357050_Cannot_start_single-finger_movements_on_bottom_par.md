---
title: "Cannot start single-finger movements on bottom part of trackpad"
date: 2017-03-29
forum: Apple Hardware Users
---

### Post by &amp;KyT$0P# on 2017-03-29
Since upgrading to Xubuntu 16.04 on my MacBook Pro 9,1, it's like the title says.  But the bottom part of the trackpad still seems responsive to two-finger scrolling, and to movements that started above it.

I think this problem goes away if I remove this configuration file from [FONT=Courier New]/etc/X11/xorg.conf.d[/FONT] -
```
Section "InputClass"
        Identifier "trackpad right-click area"
        # Set up on a MacBook Pro; uncomment the
        # next line to match only Apple trackpads:
#       MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        # This option enables the bottom right corner to be a right button.
        # This option is only interpreted by clickpads.
        Option "SoftButtonAreas" "67% 0 72% 0 0 0 0 0"
        # Disable tap to click
        Option "MaxTapTime" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
EndSection

```

Unfortunately I need that configuration.  And it didn't have any such side-effect in Lubuntu 14.04.

How to get the bottom portion of my trackpad back while keeping the right-click area and the disabled tap-to-click?


* I should add, this problem occurs even on the login screen, before any users have logged in.

---

### Post by #&amp;thj^% on 2017-03-29
Bear in mind I do not own one of these, but have work on quite a few...But have you yet looked at:
```
/usr/share/X11/xorg.conf.d/50-synaptics.conf
```
Some will show different numbers IE: **"60-synaptics.conf"** yada yada.
But about a year ago had a buddy's in for something along that same symptom;
What I did was add a line in there....now this will have to be a trial and error setting as I just can't remember the actual value that I added.:D
EXAMPLE ONLY: Like this:
```

# This option enables the bottom right corner to be a right button on
# non-synaptics clickpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
#       Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
#       To disable the bottom edge area so the buttons only work as buttons,
#       not for movement, set the AreaBottomEdge
**#       Option "AreaBottomEdge" "82%"**
EndSection
```
And if I remember correctly it took a reboot to see the changes.
Just my small effort to help.;)
Good Luck halogen2 :D
I just need to break down and buy one of these lappy's....After my Ship comes in...LOL

---

### Post by &amp;KyT$0P# on 2017-03-29
Thanks 1fallen.  I actually mostly use [FONT=Courier New]synclient[/FONT] to configure my trackpad.  That conf file is the only one I've touched.

So, after replacing the problematic .conf file and rebooting, first I listed the settings -
```
synclient -l
```

AreaBottomEdge was set to 0, so I set the bottom edge to 82% just to see what it would do -
```
synclient AreaBottomEdge=82%
```

All but the very very top of the trackpad became unresponsive, apparently because 82% was being translated into the coordinate "82", which is above the top of my trackpad.  But I noticed that affected two-finger scrolling as well as single-finger movements.

So then I tried putting in the value for "BottomEdge" into "AreaBottomEdge", and the problem is still there. :confused:


Feeling adventurous, I decided to try some synclient commands that didn't work in 14.04.  And I discovered that the problem happens if either RightButtonAreaTop or RightButtonAreaBottom ([FONT=Courier New]synclient[/FONT]'s interface to those individual parts of the "SoftButtonAreas" setting) are not set to zero. :confused:

Even weirder is, fortunately, the RightButtonAreaLeft and RightButtonAreaRight settings do not seem to affect this problem.

I can live with the entire right edge being right-click if I have to, but is there a way to force-enable single-finger movement over the click area, regardless of RightButtonAreaTop and RightButtonAreaBottom?

---

### Post by &amp;KyT$0P# on 2017-04-05
bump

---

### Post by &amp;KyT$0P# on 2017-04-15
bump

---

### Post by &amp;KyT$0P# on 2017-04-28
Since there were no further suggestions here, I looked into filing a bug.  And the process for gathering needed information looks too involved for me.  So I just set the right-click to be the entire right side of the trackpad and calling this solved.

Thanks again 1fallen for trying to help.

---

