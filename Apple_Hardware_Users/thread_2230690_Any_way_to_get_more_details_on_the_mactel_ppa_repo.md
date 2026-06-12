---
title: "Any way to get more details on the mactel ppa repos--what the packages do?"
date: 2014-06-20
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-06-20
> After going thru this process I went back to the mactel-support ppa  and  tried to look at other packages that might be helpful . . .  particularly  anything that might help with a "jumping cursor" issue  where the only  fix so far has been to disable "click to tap" on the  touchpad . . . I'm  wondering if installing any of the  "xorg-xserver-synaptics" or the  "multitouch" packages is necessary, or  would that be redundant . . .  have those packages been already updated  in 14.04??  The packages list  doesn't offer too much in terms of what  they do, or whether they are  needed in trusty . . . seems like you just  have to know??? 			 		 	 Hoping to get some further feedback on the other mactel-support  ppa items . . . how can we tell if our computer needs the packages, or  even, how can we tell what they do?  I guess apt/synaptic might show  them if they are already installed?  Although neither of them showed  macfanctl . . . I'd like to be able to have "tap to click" enabled again  w/o having the problems of jumping cursor with data erasure, etc to  contend with . . . .

e.e.p.


Folks:

I posted this question on the tail end of my "macfanctld" thread . . . since it was my first foray into the land of ppa's . . . but so far the question has remained evaded.  Still looking for some direction on where to find out what individual mactel packages do, and whether or not any or all or none are "needed" to get the Intel Mac to run better . . . and particularly whether any of them might help with the "jumping cursor" issue I and others have been having . . . .  I've been following a thread on the lubuntu-users list where recently a post suggested that "lm-sensors would not work in 14.04"????  So, as always there is conflicting data about how to handle all issues in linux . . . makes it difficult to discern which is reliable directions, etc.

e.e.p.

---

### Post by este.el.paz on 2014-06-27
Bump.

Still hoping to get some direction on how to find valid data on what is contained in individual PPA's in the mactel repository . . . google did not provide too much depth . . . .

e.e.p.

---

### Post by este.el.paz on 2014-07-03
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

*[FONT=arial][/FONT]*[FONT=arial]I found this link through the Mactel sticky . . . last updated in > 2009[/FONT] . . . the previous decade ago . . . .  Nothing on the "multitouch" or synaptic . . . packages that may or may not be needed for the touchpad . . . .  Doesn't seem current . . . .  Still trying to get some direction on this question.

e.e.p.

---

### Post by este.el.paz on 2014-07-06
Latest . . . had a few moments to check out packages in the ppa in Synaptic Package--looking for "xf86-input-multitouch" . . . the only option returned is "xf86-input-mtrack" . . . went to their website and it shows up on Github offering service to touchpads.  Searched "xserver-xorg-input-synaptic" . . . and it shows that version 1.7.4-Oubuntu1" is installed . . . but that version is not listed in the Mactel ppa list of available versions . . . so there is an updated version of this app installed, but doesn't seem to be able to get around the "jumping cursor" problem . . . .  Don't kknow if installing xf86-input-mtrack is worth my time, or is just an overlap . . . .  Saw the other thread where somebody mentions that "mactel ppa is no longer supported" . . . seems possible, but still is listed in sticky . . . even though as mentioned in previous post, last updated . . . '09???

e.e.p.

---

### Post by este.el.paz on 2014-07-12
> **este.el.paz said:**
> Latest . . . had a few moments to check out packages in the ppa in Synaptic Package--looking for "xf86-input-multitouch" . . . the only option returned is "xf86-input-mtrack" . . . went to their website and it shows up on Github offering service to touchpads.  Searched "xserver-xorg-input-synaptic" . . . and it shows that version 1.7.4-Oubuntu1" is installed . . . but that version is not listed in the Mactel ppa list of available versions . . . so there is an updated version of this app installed, but doesn't seem to be able to get around the "jumping cursor" problem . . . .  Don't kknow if installing xf86-input-mtrack is worth my time, or is just an overlap . . . .  Saw the other thread where somebody mentions that "mactel ppa is no longer supported" . . . seems possible, but still is listed in sticky . . . even though as mentioned in previous post, last updated . . . '09???

e.e.p.

Bump in the night . . . .  Still looking for some direction on finding details on the packages in the mactel ppa . . . only finding very basic info . . . .  I suppose the non-answers is because there are no details ??

e

---

### Post by maestrobwh1 on 2014-07-13
I honestly think if you are using 14.04, you really don't need anything extra.  The only thing I would recommend is installing xserver-xorg-input-mtrack and use that driver for the touchpad so that it behaves like it does in OSX.  I could never tweak the synaptics driver to get it under control where it didn't drive me nuts.  With then instructions below, I have my trackpad behaving very nicely as it does in OSX.  It would be nice if there was a graphical tool for mtrack like there is for synaptics, but once I set my touchpad up, I rarely if ever change settings.

This post shows some information:
[http://www.chris-reilly.org/blog/technotes/macbook-trackpad-in-ubuntu/](http://www.chris-reilly.org/blog/technotes/macbook-trackpad-in-ubuntu/)

This post explains each option better:
[http://www.snip2code.com/Snippet/61696/a-part-of--etc-X11-xorg-conf-d-50-mtrack](http://www.snip2code.com/Snippet/61696/a-part-of--etc-X11-xorg-conf-d-50-mtrack)


You'd then need to create a file in /etc/X11/xorg.conf.d

```
sudo mkdir -p /etc/X11/xorg.conf.d
```

then create a file like this, I use nano in terminal:

```
sudo nano /etc/X11/xorg.conf.d/50-mtrack.conf
```

Contrary to the first post's example,I like the tap to click so I have "tapbutton1" and "tapbutton2" set to do one and two finger taps (no zero numbers) to mimic left and right click, and I also made my sensitivity higher so that I could have the mouse a larger distance with a finger swipe.  My file looks like this:

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "touchpad"
    Driver          "mtrack"
    Option          "Sensitivity" "0.90"
    Option      "FingerHigh" "12"
    Option      "FingerLow" "1"
    Option          "IgnoreThumb" "true"
    Option          "IgnorePalm" "true"
    Option          "TapButton1" "1"
    Option          "TapButton2" "3"
    Option          "TapButton3" "0"
    Option          "TapButton4" "0"
    Option          "ClickFinger1" "1"
    Option          "ClickFinger2" "3"
    Option          "ClickFinger3" "3"
    Option          "ButtonMoveEmulate" "false"
    Option      "ButtonIntegrated" "true"
    Option          "ClickTime" "25"
    Option          "BottomEdge" "25"
    Option      "SwipeLeftButton" "8"
    Option      "SwipeRightButton" "9"
    Option      "SwipeUpButton" "0"
    Option      "SwipeDownButton" "0"
    Option      "ScrollDistance" "75"
EndSection
```

---

### Post by este.el.paz on 2014-07-13
> **maestrobwh1 said:**
> I honestly think if you are using 14.04, you really don't need anything extra.  The only thing I would recommend is installing xserver-xorg-input-mtrack and use that driver for the touchpad so that it behaves like it does in OSX.  I could never tweak the synaptics driver to get it under control where it didn't drive me nuts.  With then instructions below, I have my trackpad behaving very nicely as it does in OSX.  It would be nice if there was a graphical tool for mtrack like there is for synaptics, but once I set my touchpad up, I rarely if ever change settings.

This post shows some information:
[http://www.chris-reilly.org/blog/technotes/macbook-trackpad-in-ubuntu/](http://www.chris-reilly.org/blog/technotes/macbook-trackpad-in-ubuntu/)

This post explains each option better:
[http://www.snip2code.com/Snippet/61696/a-part-of--etc-X11-xorg-conf-d-50-mtrack](http://www.snip2code.com/Snippet/61696/a-part-of--etc-X11-xorg-conf-d-50-mtrack)


You'd then need to create a file in /etc/X11/xorg.conf.d

```
sudo mkdir -p /etc/X11/xorg.conf.d
```

then create a file like this, I use nano in terminal:

```
sudo nano /etc/X11/xorg.conf.d/50-mtrack.conf
```

Contrary to the first post's example,I like the tap to click so I have "tapbutton1" and "tapbutton2" set to do one and two finger taps (no zero numbers) to mimic left and right click, and I also made my sensitivity higher so that I could have the mouse a larger distance with a finger swipe.  My file looks like this:

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "touchpad"
    Driver          "mtrack"
    Option          "Sensitivity" "0.90"
    Option      "FingerHigh" "12"
    Option      "FingerLow" "1"
    Option          "IgnoreThumb" "true"
    Option          "IgnorePalm" "true"
    Option          "TapButton1" "1"
    Option          "TapButton2" "3"
    Option          "TapButton3" "0"
    Option          "TapButton4" "0"
    Option          "ClickFinger1" "1"
    Option          "ClickFinger2" "3"
    Option          "ClickFinger3" "3"
    Option          "ButtonMoveEmulate" "false"
    Option      "ButtonIntegrated" "true"
    Option          "ClickTime" "25"
    Option          "BottomEdge" "25"
    Option      "SwipeLeftButton" "8"
    Option      "SwipeRightButton" "9"
    Option      "SwipeUpButton" "0"
    Option      "SwipeDownButton" "0"
    Option      "ScrollDistance" "75"
EndSection
```

@maestrobwh1:

Thanks very kindly for the reply, appreciate the feedback and the details, and specific insight into the touchpad issue--that has been a problem with just about every distro I've tried, between the LM flavors and then over in various 'Buntu . . . as you say, and I've experienced, the synaptics driver doesn't really cut it.  So, thanks.  Got a little busier from the month or so back when I first posted this, so it'll be a bit before I can cut out the time to actually go through and do it . . . .  Seems like the installing of "x-x-i-mtrack" or whatever, wouldn't be too time consuming, but from quick read it appears like you are showing it then needs to be added into the xorg.conf file, etc????  It wouldn't become the "default" driver automatically with installation???? 

e.e.p.
PS: Funny to see "Allentown" . . . I grew up in small town not too far away from there, and last time I went home I caught a shuttle from Philly to Allentown airport, to save my aging folks the drive down the SureKill to PHX . . . .

---

