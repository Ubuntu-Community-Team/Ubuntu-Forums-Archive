---
title: "Irratic track pad under 2.6.20-12"
date: 2007-03-23
forum: Apple Intel Users
---

### Post by gmc on 2007-03-23
Hi Folks,

I'm having a problem with my track pad. It's very irratic, the pointer stutters, stalls and some times refuses to move. I only noted this misbehavior under the current feisty kernel (2.6.20-12). If I plug in a USB mouse the pointer works like a charm.

I've tried playing with my xorg.conf settings:

```

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "CorePointer"
       # Option          "Device"                "/dev/input/mouse1"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "raw"
       # Option          "Protocol"              "auto-dev"
       Option  "LeftEdge"               "100"
       Option  "RightEdge"              "1120"
       Option  "TopEdge"                "50"
       Option  "BottomEdge"             "310"
       Option  "FingerLow"              "25"
       Option  "FingerHigh"             "30"
       Option  "MaxTapTime"             "180"
       Option  "MaxTapMove"             "220"
       Option  "MaxDoubleTapTime"       "180"
       Option  "VertScrollDelta"        "20"
       Option  "HorizScrollDelta"       "50"
       Option  "MinSpeed"               "0.79"
       Option  "MaxSpeed"               "0.88"
       Option  "AccelFactor"            "0.0015"
       Option  "SHMConfig"              "on"
EndSection

```...with no success. 

Can anyone confirm this problem or suggest something I can try to fix the problem. Actually what would be idea, is if someone has figured out how to get the track pad to operate the same way it does under OSX (one finger moved the mouse, two fingers scrolls a window).

Any help or suggestions would be greatly appreciated.

Gord

---

### Post by cyberdork33 on 2007-03-23
maybe the sensitivity needs adjusting? see the synaptics manual page for info on the FingerHigh and FingerLow

```
man synaptics
```

Also there is a VertTwoFingerScroll / HorizTwoFingerScroll detailed there as well.

---

### Post by gmc on 2007-03-23
Hi All,

Well, I found part of a solution. You can also activate a "Mac-style" two-finger-scrolling behaviour by adding to xorg.conf

```

  Option "VertTwoFingerScroll"  "1"
  Option "HorizTwoFingerScroll" "1"


```

Now if only I could get the trackpad to work without stuttering. Interestingly enough, if I boot
a live 6.10 cd, the trackpad works perfectly, so the problem must be with 2.6.20-12 and for some
reason, I'm unable to boot the previous 2.6.17-xx kernels.

Gord

---

### Post by Darrena on 2007-03-25
I think this is fixed in the new version of xorg-input-synaptics.

[https://launchpad.net/ubuntu/feisty/+source/xserver-xorg-input-synaptics/0.14.6-0ubuntu7](https://launchpad.net/ubuntu/feisty/+source/xserver-xorg-input-synaptics/0.14.6-0ubuntu7)

---

### Post by gmc on 2007-03-26
> **Darrena said:**
> I think this is fixed in the new version of xorg-input-synaptics.

[https://launchpad.net/ubuntu/feisty/+source/xserver-xorg-input-synaptics/0.14.6-0ubuntu7](https://launchpad.net/ubuntu/feisty/+source/xserver-xorg-input-synaptics/0.14.6-0ubuntu7)



Agreed. The new synaptics driver has helps some but I find the pointer still freezes after about a second or two of movement, thought prior to this freezing, the motion is a lot smoother than it was before.

Gord

---

### Post by russellc on 2007-03-27
I might have had the same problem you had, but it had to with my xorg config and not the driver version. The change I made to fix my problem was in the ServerLayout section:

Make sure that ```
InputDevice    "Synaptics Touchpad"
```
is above ```
InputDevice    "Configured Mouse"
```

Here are the InputDevice sections for both the Configured Mouse and Synaptics Touchpad:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "SendCoreEvents" "on"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "Device" "/dev/input/mouse1"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "100"
	Option "RightEdge" "5000"
	Option "TopEdge" "50"
	Option "BottomEdge" "300"
	Option "FingerLow" "10"
	Option "FingerHigh" "20"
	Option "MaxTapTime" "150"
	Option "MaxTapMove" "220"
	Option "MaxDoubleTapTime" "180"
	Option "VertScrollDelta" "25"
	Option "HorizScrollDelta" "80"
	Option "VertTwoFingerScroll" "true"
	Option "HorizTwoFingerScroll" "true"
	Option "FastTaps" "false"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
	Option "MinSpeed" "0.79"
	Option "MaxSpeed" "0.88"
	Option "AccelFactor" "0.02"
	Option "PalmDetect" "1"
	Option "SHMConfig" "on"
EndSection
```

Take note of the option "SendCoreEvents" in Configured Mouse and "CorePointer" in Synaptics Touchpad because I recall those had an effect. Hope that helps.

---

### Post by gmc on 2007-03-27
Hi Russell

I commented out the appropriate sections of my current /etc/X11/xorg.conf and cut and pasted your sample. Upon rebooting, the trackpad did not work at all, though my external USB mouse did.

Needless to say, I switched back to my original settings. One thing I have noticed is that the trackpad seems to be very responsive while sitting at the gdm login page, so I'm wondering if the problem is with gnome itself.

Gord

---

### Post by russellc on 2007-03-27
That's strange.. I had that problem too but it was fixed with the SendCoreEvents option. Also, Synaptics Touchpad had to be loaded before Configured Mouse in the ServerLayout section.

What happens is X thinks the touchpad is the primary mouse, so it will not allow the USB mouse to work. With SendCoreEvents, it will be fixed as it will accept events from the USB mouse in addition to the touchpad. This is odd as it works flawlessly for me.

Good luck, nonetheless.

---

### Post by bsantos on 2007-03-27
synaptics is missing a TwoFingerButtonTwo option...

In Mac OS X you can do a right button click while having two fingers on the trackpad, that would be awesome to have supported by synaptics. The current buttons on corners is suboptimal and I hate buttons on trackpad tapping...

---

### Post by cyberdork33 on 2007-03-28
Actually you might want to look around, as I thought that the twofingerclick was possible... I swear I saw someone say they had got it working...

---

### Post by bsantos on 2007-03-28
I believe you can do it by tapping with two fingers, not having two fingers on the trackpad and clicking the button.

I usually use an external mouse, but would be useful when there's not enough space to have the mouse, or when just doing stuff that doesn't require a mouse.

A little OT is my wish for better remote support... :P

Totem is good enough to watch videos, it's no Front Row, something like that will come with Elisa, or with LinuxMCE, or something like that, but it annoys me that you can't seek by keeping the next-previous buttons pressed... :(

When using pommed without key shortcuts for volume associated to the keys (volume keys on the keyboard have the same keycode that the ones on the remote), the volume changes but you get no visual feedback. Is that some bug in pommed? Missing some sort of dbus communication?

---

### Post by russellc on 2007-03-28
> **bsantos said:**
> synaptics is missing a TwoFingerButtonTwo option...

In Mac OS X you can do a right button click while having two fingers on the trackpad, that would be awesome to have supported by synaptics. The current buttons on corners is suboptimal and I hate buttons on trackpad tapping...

My touchpad works just like it does in OS X on mine. You can tap with two fingers to right click, two finger drag to scroll.

---

### Post by bsantos on 2007-03-28
> **russellc said:**
> My touchpad works just like it does in OS X on mine. You can tap with two fingers to right click, two finger drag to scroll.


Like I already said, I'm referring to twofinger button press right click, not two finger tapping, which I hate. :)

---

### Post by russellc on 2007-03-28
> **bsantos said:**
> Like I already said, I'm referring to twofinger button press right click, not two finger tapping, which I hate. :)

I'm not too sure what that sort of behaviour you are talking about lol, but when I was on OS X, that is how my touchpad worked :p

---

### Post by bsantos on 2007-03-28
> **russellc said:**
> I'm not too sure what that sort of behaviour you are talking about lol, but when I was on OS X, that is how my touchpad worked :p


:) It's not the default behavior. I hate tap clicking, you can configure OS X to do a right click when you have two fingers on the trackpad. It is simpler and way less prone to false clicking than tapping.

---

### Post by cyberdork33 on 2007-03-29
Sorry, I don't have a Mac Laptop didn't know what action you were referring to... that would be good though!

---

### Post by thelost on 2007-05-09
has anyone managed to solve this because I have exactly the same problem (had it under dapper and now feisty). It's extremely frustrating to suddenly have the pad freeze for a second and then start working again.

I've tried the fixes listed above, perhaps I did it wrong? I'm fairly new to linux so help is appreciated!

---

### Post by bsantos on 2007-05-09
> **thelost said:**
> has anyone managed to solve this because I have exactly the same problem (had it under dapper and now feisty). It's extremely frustrating to suddenly have the pad freeze for a second and then start working again.

I've tried the fixes listed above, perhaps I did it wrong? I'm fairly new to linux so help is appreciated!


Removing mouseemu didn't fix it for you?

---

### Post by thelost on 2007-05-09
as in sudo aptitude remove mouseemu?

I tried that and my trackpad stopped working. I reinstalled mouseemu and my trackpad is now having a nervous breakdown, although external mice still work.

I'm a bit of a noob, bear with me. Where to go next you think?

---

### Post by bsantos on 2007-05-09
Your trackpad uses the synaptics driver?

Removing mouseemu shouldn't affect your mouse (it's only a listener to emulate mouse actions, like tapping, and emulating mouse buttons and wheel), have you tried to restart the X server (Ctrl-Alt-Backspace) after removing it?

Most of what mouseemu does is somehow supported by the synaptics driver, like tapping or mouse wheel emulation.

If that doesn't work mouseemu can be configured to don't turn off the pad when a key is clicked, but you have to edit /etc/default/mouseemu and uncomment the following line:

#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

A changing it to

TYPING_BLOCK="-typing-block 0"

The pad blocking is to reduce the possibility of touching your pad while typing (thumbs or hand palms are the most probable culprits) and moving/tapping the pointer.

---

### Post by thelost on 2007-05-10
ok well i am still having the problem and I have the settings from russellc's post in my xorg.conf. I also wondered if it could be this:

[https://bugs.launchpad.net/ubuntu/+bug/84119](https://bugs.launchpad.net/ubuntu/+bug/84119)

any help is appreciated this is driving me nuts!

---

### Post by zurgutt on 2007-05-10
Same problem here.  From my original post in other trackpad related thread:
[http://ubuntuforums.org/showthread.php?p=2621280#post2621280](http://ubuntuforums.org/showthread.php?p=2621280#post2621280)

The trackpad action feels mostly ok, EXCEPT one very annoying issue: sometimes when you put a finger on pad and move it, cursor wont move. Doesnt move at all - this is not issue of touching too lightly or somesuch. To make it move again I have to lift off finger and try again (sometimes 2-3 times) OR I can use quick wiggling movement without lifting finger, which seems to work too, mostly. In contrast, long smooth strokes without lifting finger does not seem to work.

This seems to happen at random times, at average several times per minute. Extremely annoying.

Trackpad works fine in osx and knoppix livecd. Feisty livecd has same issue though.  So it is not a hardware problem, at least not entirely.

I have installed gsynaptics, however it does not seem to help, or do anything in fact - speed/acceleration controls have no effect. Checkbox options do, however..

I have also tried several examples of xorg.conf from people who have it working ok, also no help.  Damn thing just moves when it wants.

---

### Post by johnficca on 2007-05-27
> **zurgutt said:**
> Same problem here.  From my original post in other trackpad related thread:
[http://ubuntuforums.org/showthread.php?p=2621280#post2621280](http://ubuntuforums.org/showthread.php?p=2621280#post2621280)

The trackpad action feels mostly ok, EXCEPT one very annoying issue: sometimes when you put a finger on pad and move it, cursor wont move. Doesnt move at all - this is not issue of touching too lightly or somesuch. To make it move again I have to lift off finger and try again (sometimes 2-3 times) OR I can use quick wiggling movement without lifting finger, which seems to work too, mostly. In contrast, long smooth strokes without lifting finger does not seem to work.

This seems to happen at random times, at average several times per minute. Extremely annoying.

Trackpad works fine in osx and knoppix livecd. Feisty livecd has same issue though.  So it is not a hardware problem, at least not entirely.

I have installed gsynaptics, however it does not seem to help, or do anything in fact - speed/acceleration controls have no effect. Checkbox options do, however..

I have also tried several examples of xorg.conf from people who have it working ok, also no help.  Damn thing just moves when it wants.

I have the same problem, I hope there will be a fix soon.

---

### Post by citizenofnowhere on 2007-06-09
Same problem on Feisty 2.6.20-16 generic. Seems to happen after the gdm screen too, as pointed out earlier, and after i turned on the two finger scroll. Should we pass this on to a launchpad thread?

---

