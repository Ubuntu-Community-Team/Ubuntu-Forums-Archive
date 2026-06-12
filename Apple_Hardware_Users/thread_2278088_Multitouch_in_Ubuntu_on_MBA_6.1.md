---
title: "Multitouch in Ubuntu on MBA 6.1"
date: 2015-05-13
forum: Apple Hardware Users
---

### Post by dondondonkaibudafl on 2015-05-13
Hi forum,

I'd like to share my experience in configuring multitouch on my MBA. The configuration should enable the following gestures, the respective keybinding can be found in the `.xbindkeysrc` (if you don't use workspace that much, switch the keybindings of three fingers and four fingers would be better. I think four finger swipes are good for the tasks most commonly used):

open/close dash (three finger tap),
switch application (three finger swipe up),
clear desktop (three finger swipe down),
switch browser/editor tabs (three finger swipe left/right),
zoom in/out (two finger pinch),
switch workspace (four finger swipe),
and,
selecting current applications (four finger tap).

Firstoff, both of Ubuntu 14.04 and 14.10 with kernel 3.16 are pretty good on MBA 6.1. I got no MBA 6.1/6.2-specific problem here. However, for the multitouch support, it really costed me a few nights. I tried `touchegg` but had no clue on how to make it work. After read a post on Dropbox security and how to detect user keystrokes, I tried again with a hope to find a better driver or a way to re-map the trackpad input. And, with a few different combinations (xdotool is ruled out in my case), the multitouch finally work on my MBA. My setting (yup, it's highly customizable) focuses on switching applications and workspaces. Also zoom in and zoom out, it quite helpful in browser and some code editor, e.g. sublime text.

Hereunder is the my tested solution, an updated version may be found in the file [multitouch.markdown of Setup Development Environment - Linux Version]("https://bitbucket.org/snippets/drewfle/kkp8#multitouch.markdown") on my BitBucket:

***I might forget to mention xev and xte are needed to be installed (I got one of them bundled in 14.04/14.10). Now the line is added to the the latter section of this post.

**Reference**
[How to fix MacBook Pro touchpad on Ubuntu 14.04]("http://yarenty.blogspot.com/2014/08/how-to-fix-macbook-pro-touchpad-on.html")
[xf86-input-mtrack]("https://github.com/BlueDragonX/xf86-input-mtrack/")
[XEV]("http://www.x.org/archive/current/doc/man/man1/xev.1.xhtml")
[How to configure extra buttons in Logitech Mouse]("http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse/246849#246849")

**Install `mtrack`**

```

sudo apt-get install xserver-xorg-input-mtrack

```

**Configure `mtrack`**
```

sudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf

```

And my configuration is as below, paste and edit them in `50-synaptics.conf`. Basically the options commented out are the default setting manually typed in according to the readme in mtrack's GitHub repo. Note that you can even add your own button number such as assigning button number `[COLOR=#000000]20` to `[/COLOR][COLOR=#000000]TapButton4`. The response time between click, tap and swipe can also be finely tuned to resemble the feel in OS X. The default setting has a slightly noticeable time, in ms, between gestures. 

[/COLOR]```

# Drewfle added for mtrack
Section "InputClass"
        MatchIsTouchpad "on"
        Identifier      "Touchpads"
        Driver          "mtrack"
#        Option          "TrackpadDisable" "0"
        Option          "Sensitivity" "1.3"
#        Option            "FingerHigh" "5"
#        Option            "FingerLow" "5"
        Option            "IgnoreThumb" "true"
        Option            "IgnorePalm" "true"
        Option            "DisableOnThumb" "true"
        Option            "DisableOnPalm" "true"
#        Option            "ThumbRatio" "70"
#        Option            "ThumbSize" "25"
#        Option            "PalmSize" "40"
#        Option            "BottomEdge" "10"
#        Option            "ButtonEnable" "true"
#        Option            "ButtonIntegrated" "true"
#        Option            "ButtonMoveEmulate" "true"
#        Option            "ButtonZonesEnable" "false"
#        Option            "ButtonTouchExpire" "100"
#        Option            "ClickFinger1" "3"
#        Option            "ClickFinger2" "2"
#        Option            "ClickFinger3" "0"
#        Option            "TapButton1" "1"
#        Option            "TapButton2" "3"
        Option            "TapButton3" "2"
        Option            "TapButton4" "20"
#        Option            "ClickTime" "50"
#        Option            "MaxTapTime" "120"
#        Option            "MaxTapMove" "400"
#        Option            "GestureClickTime" "10"
#        Option            "GestureWaitTime" "100"
#        Option            "ScrollDistance" "150"
#        Option            "ScrollUpButton" "4"
#        Option            "ScrollDownButton" "5"
#        Option            "ScrollLeftButton" "6"
#        Option            "ScrollRightButton" "7"
#        Option            "SwipeDistance" "700"
#        Option            "SwipeUpButton" "8"
#        Option            "SwipeDownButton" "9"
#        Option            "SwipeLeftButton" "10"
#        Option            "SwipeRightButton" "11"
#        Option            "Swipe4Distance" "700"
        Option            "Swipe4UpButton" "16"
        Option            "Swipe4DownButton" "17"
        Option            "Swipe4LeftButton" "18"
        Option            "Swipe4RightButton" "19"
#        Option            "ScaleDistance" "150"
#        Option            "ScaleUpButton" "12"
#        Option            "ScaleDownButton" "13"
#        Option            "RotateDistance" "150"
#        Option            "RotateLeftButton" "14"
#        Option            "RotateRightButton" "15"
#        Option            "TapDragEnable" "true"
#        Option            "TapDragTime" "350"
#        Option            "TapDragWait" "40"
#        Option            "TapDragDist" "200"
#        Option            "AxisXInvert" "false"
#        Option            "AxisYInvert" "false"
EndSection

```
Reload the Synaptics driver configuration (the command will restart X Display Manager and log out the current session, I GUESS, it looks like a restart but not a restart).
```

sudo restart lightdm

```

[B]Install Xbindkeys and Xautomation

[/B]This is the high time to hook the trackpad up with Ubuntu. Note that you may need `xev` to look up the keyboard and multitouch input.

```

# in case you don't have xev and xte installed
sudo apt-get install xev xte

# now install xbindkeys xautomation
sudo apt-get install xbindkeys xautomation
xbindkeys --defaults > $HOME/.xbindkeysrc
gedit $HOME/.xbindkeysrc

```

Paste  and/or edit the following near the bottom of `.xbindkeysrc`.

```

# Drewfle Configuration
"xte 'key Super_L'"
b:2

"xte 'keydown Alt_L' 'key Tab' 'keyup Alt_L'"
b:8
"xte 'keydown Super_L' 'key d' 'keyup Super_L'"
b:9
"xte 'keydown Shift_L' 'keydown Control_L' 'key Tab' 'keyup Shift_L' 'keyup Control_L'"
b:10
"xte 'keydown Control_L' 'key Tab' 'keyup Control_L'"
b:11


"xte 'keydown Control_L' 'key equal' 'keyup Control_L'"
b:12
"xte 'keydown Control_L' 'key minus' 'keyup Control_L'"
b:13


"xte 'keydown Control_L' 'keydown Alt_L' 'key Up' 'keyup Control_L' 'keyup Alt_L'"
b:16
"xte 'keydown Control_L' 'keydown Alt_L' 'key Down' 'keyup Control_L' 'keyup Alt_L'"
b:17
"xte 'keydown Control_L' 'keydown Alt_L' 'key Left' 'keyup Control_L' 'keyup Alt_L'"
b:18
"xte 'keydown Control_L' 'keydown Alt_L' 'key Right' 'keyup Control_L' 'keyup Alt_L'"
b:19

"xte 'keydown Super_L' 'key w' 'keyup Super_L'"
b:20

```

(If needed) Now customize the newly added key bindings in `.xbindkeysrc` with the help of `xev` and add/remove mouse keys in `50-synaptics.conf`


```

# use xev to check key or mouse key if necessary
# note: once the mouse key is bound to xbindkeys, xev would not be able detect mouse key correctly
xev

```


[B]Last Step
[/B]Just `sudo reboot` to make the setting to take effect. I tried `exec $SHELL` but not applying the setting. Enjoy MT with UBUNTU!

---

### Post by dondondonkaibudafl on 2015-05-13
Here is some additional discussion. Seeking for an ideal machine for some kind of double/triple boot is hard. And my experience told me Ubuntu prefer some one-year+ aged machine to live with (not like too old cuz there may no proper graphics driver for some vendor). I tried to upgrade kernel to 3.16 in 14.04.1, but any versions of bcmwl driver just not work with the wifi. After I freshly installed 14.04.2, the `probably similar` 3.16 kernel and the `probably` the same `bcmwl` are not just work out of the box, but also support 5G connection (and it's really fast ...). Many weird problems I met with 14.04.1 are gone as well. The thing doesn't so cool is the detached encrypted swap area that I have to sort out on other desktops/laptops.

---

