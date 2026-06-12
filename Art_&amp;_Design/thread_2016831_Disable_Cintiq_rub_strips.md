---
title: "Disable Cintiq rub strips?"
date: 2012-07-04
forum: Art &amp; Design
---

### Post by Jack the R on 2012-07-04
I have tried going through System Settings>Input Devices>Graphic Tablet>Pad Buttons.  In the Touch Strip section, is the option to set the strips to "disable."  Unfortunately this does not work.  The touch stips are still active.  Is there a way to actually disable all input from the touch strips within Linux?  I may even be willing to physically open the Cintiq (12WX) and pull plugs or cut wires as long as the screen and stylus remain functional. 

I'm using Kubuntu 12.04, but I believe the input devices section is the same in Ubuntu and Mint.

---

### Post by Favux on 2012-07-04
Hi Jack the R,

I think you would be able to do that with a xsetwacom command assigning the touch strips to nothing.

What's the output of the following command in a terminal?
```
xinput list
```
That will give us the <device name> to use in the xsetwacom command.

---

### Post by Jack the R on 2012-07-05
Here's what I got - 

```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 12WX stylus                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; Honey Bee  Nostromo SpeedPad2             id=11   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Mouse                       id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 12WX eraser                  id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Cintiq 12WX pad                     id=14   [slave  pointer  (2)]
&#9116;   &#8627; HID 045e:00be                             id=16   [slave  pointer  (2)]
&#9116;   &#8627; Pystromo Input Remapper                   id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; LITEON Technology USB Multimedia Keyboard id=8    [slave  keyboard (3)]
    &#8627; Honey Bee  Nostromo SpeedPad2             id=10   [slave  keyboard (3)]

```

---

### Post by Favux on 2012-07-05
OK, given that device name what happens to the right touch strip when you run these two xsetwacom commands in a terminal?
```

xsetwacom set "Wacom Cintiq 12WX pad" StripRightDown ""
xsetwacom set "Wacom Cintiq 12WX pad" StripRightUp ""

```
If that works then you'd do the same with the left one.

---

### Post by Jack the R on 2012-07-05
Still mucking up, changes me from the paintbrush to the airbrush in GIMP.

---

### Post by Favux on 2012-07-05
Before and after you run the xsetwacom set commands what is the result of running these get commands?
```
xsetwacom get "Wacom Cintiq 12WX pad" StripRightDown
xsetwacom get "Wacom Cintiq 12WX pad" StripRightUp
```

---

### Post by Jack the R on 2012-07-06
StripRightDown is 4, StripRightUp is 3.  Before and after the set commands.

---

### Post by Favux on 2012-07-06
Interesting.  The xsetwacom set commands should override the hardcoded key values from the kernel(?) or the KDE configuration utility if you are using it.  So is this a bug?  In Kubuntu 12.04 or in xf86-input-wacom?  You should have version 0.14.0 which is pretty recent:
```
xsetwacom -V
```
Hmm.  There's a couple of commits after 0.14.0 that may actually address your "bug".  The 0.15.0 release tar is due anytime or we could clone the git repository.

3 and 4 are for vertical scrolling I think.  Does that make sense with what you are seeing?

But it does answer a question I had on whether the strips would take an integer assignment.  For buttons to disable them you can assign them 0 in a static configuration (as opposed to a run-time configuration like xsetwacom).  So let's try that rather than updating xf86-input-wacom yet.

We'll work from:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

If you already do not have /etc/X11/xorg.conf.d create it with:
```
su - -c "mkdir /etc/X11/xorg.conf.d"
```
Then we'll create a .conf file:
```
su - -c "kwrite /etc/X11/xorg.conf.d/52-wacom.conf
```
Then for it's content add:
```
Section "InputClass"
	Identifier "Wacom pad options"
	MatchDriver "wacom"
	MatchProduct "pad"
	# Apply custom Options to this device below.
	Option "StripRightDown" "0"
	Option "StripRightUp" "0"
EndSection
```
Then Save and restart.  If that works then you can add the left options below the right ones.

---

### Post by Jack the R on 2012-07-06
I do have 0.14.0.

The right rub strips do scroll in Firefox.

Sadly they still scroll in Firefox, after creating 52-wacom.conf.

---

### Post by Favux on 2012-07-06
Well that sure is sounding like a bug.

Let's try updating xf86-input-wacom and see if the xsetwacom commands or the xorg.conf.d .conf file will then work.

I think you should try cloning the xf86-input-wacom repository and then compile and install it.  See part II. b) abd c) in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Jack the R on 2012-07-07
I'm trying to remap 3 and 4 with Pystromo - not having any luck, but I haven't given up yet.

---

### Post by Jack the R on 2012-07-29
For anyone having a similar problem, the solution turned out to be changing a setting in GIMP.  Go to Edit>Input Devices, select the pad and change the mode from screen to disabled.  This will keep GIMP from seeing the pad as a tool, like the stylus or mouse, and giving the pad its own tool settings.  Which GIMP then changes to when the rub strips are touched.

---

