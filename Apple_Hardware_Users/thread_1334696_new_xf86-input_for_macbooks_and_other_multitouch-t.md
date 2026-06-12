---
title: "new xf86-input for macbooks and other multitouch-touchpads."
date: 2009-11-22
forum: Apple Hardware Users
---

### Post by bobbytables on 2009-11-22
[CENTER][SIZE="4"]**xf86-input-multitouch status:**
** beta1** has been released. rc1 scheduled for **July 20th.**[/SIZE][/CENTER]




The Multitouch X Driver driver uses the kernel MT protocol to bring multi-touch gestures to the Linux desktop.

You need an [[COLOR="Blue"]_MT-enabled touchpad_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9121886&postcount=79") in order to use this driver.




[SIZE="5"]_Features_[/SIZE]
[LIST]
[*] [COLOR="SeaGreen"] 2-Finger Scrolling
[*] Click with one Finger, Drag with another
[*] Tap-to-Click
[*] 3-Finger-Swipe: BTN 8 through 11
[*] Resize: BTN12 and 13
[*] Rotate: BTN15 and 15[/COLOR]
-------------
[COLOR="red"]
[*] On-the-fly configuration (like synclient)
[*] Region for "thumb-click -> index-finger drag" should not be fixed size, but rather depending on relative positions.
[/COLOR]
[/LIST]


[SIZE="5"]_Installation_[/SIZE]

if you're keen to try it out, grab the sources, and build them:
[INDENT]Prerequisites:
```
sudo aptitude install xserver-xorg-dev
```
[/INDENT]


```

git clone http://bitmath.org/git/multitouch.git
cd multitouch
make && sudo make install

```

afterwards add the following to your "[COLOR="Blue"]**/etc/X11/xorg.conf**[/COLOR]":
```

Section "InputClass"
        MatchIsTouchpad "true"
        Identifier "touchpad"
        Driver "multitouch"
EndSection

```

Note: when you run into problems, please think for a moment, before asking. e.g. when ubuntu says, that it doesn't know "git", than that is something you can probably figure out without asking questions here...


[SIZE="4"]_Changelog_[/SIZE]
[LIST]
[*]15JUN2010 Multitouch v1.0-beta1 released. Tap-to-Click, Tap-and-Hold for Dragging, ... see [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9469768&postcount=187")
[*]15MAY2010 Multitouch v1.0-alpha3 released. Thumb detection, better support for integrated button trackpads, scaling and rotation gestures.
[*]15APR2010 Multitouch v1.0-alpha2 released. Kudos to Arturo Castro for work on the integrated button trackpad.
[*]01FEB2010 The Multitouch X Driver is now in alpha stage. You are welcome to contribute gestures to the project.
[/LIST]


[COLOR="Red"]Disclaimer:[/COLOR] this driver is mainly developed by Henrik Rydberg ([kosumi68]("http://ubuntuforums.org/member.php?u=592679") ), not me. a few people (including me) contributed minor fixes - for more information see the git-log.

---

### Post by alexmurray on 2009-11-22
You should definitely get in contact with Henrik Rydberg since I know he has looked at similar issues in the past and would be the most familiar with all of this (ie multitouch and synaptics etc). He's the one who developed the existing BCM5974 driver for Macbooks and has been looking at multi-touch for a while.

He's on launchpad as [rydberg]("https://launchpad.net/~rydberg") and also these forums as [kosumi68]("http://ubuntuforums.org/member.php?u=592679").

---

### Post by kosumi68 on 2010-01-30
UPDATE 15MAY2010:

Multitouch X Driver v1.0-alpha3 is released:
[http://bitmath.org/code/multitouch/](http://bitmath.org/code/multitouch/)

You need an MT-enabled touchpad in order to use this driver. For macs, install the bcm5974-dkms package from the Mactel PPA. To compile the code, you need the xserver-xorg-dev package. Compiling is reported to work for most, and a "sudo make install" puts the driver in the right place. Depending on lucid / karmic, the setting up in Xorg is different, you will find answers throughout this thread.

The beta1 will be released 15JUN2010, so if you want to contribute, now is the time. :-)

Happy hacking

---

### Post by DizzyTech on 2010-01-30
Do you mind me asking if there are any package dependencies that could aid in getting it working?  I got it compiled and installed from GIT, but my trackpad (MacBookPro5,5; a.k.a. June 2009 Unibody MBP) only clicks and doesn't move.  On the positive side, Xorg logs show that it's running.  Very interesting developments.  ;)

---

### Post by kosumi68 on 2010-01-31
The multitouch (MT) protocol was introduced in the 2.6.31 kernel, but there are only a few MT-enabled input drivers so far, and none of them are available in 2.6.31, which karmic is based on.

I updated the karmic version of bcm5974-dkms in the ppa to the 2.6.33 kernel version, which is MT-enabled. That should help. :-)

---

### Post by kosumi68 on 2010-02-01
Alpha 1 of the multitouch X driver is now released.

I run it daily instead of the synaptics driver. It has all the features i normally use, which include two-finger scrolling, three-finger swipe, two-finger click and three-finger click. For those of you running the all-in-one trackpad with integrated button, this driver should be the place to implement the hack you are currently using.

---

### Post by DizzyTech on 2010-02-02
Kudos on the release... but, still, any hints on dependencies?  I actually got errors in compiling this time, which is suprisingly good news.  Do I need to install the Xorg SDK?  Is there a package for that?

---

### Post by alexmurray on 2010-02-03
Try installing [xserver-xorg-dev]("apt:xserver-xorg-dev")

---

### Post by alexmurray on 2010-02-03
Okay have finally tested it - after compiling multitouch from git and installing it, and installing bcm5974-dkms from the mactel support ppa, I then had to remove /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi to stop the synaptics driver getting loaded in place of the multitouch driver.

I can confirm 2 finger vertical scroll works, as does right and middle click using 2 and 3 finger clicks respectively. 2 finger horizontal scroll doesn't appear to work, whilst 3 finger swipe produces a slow vertical scroll in chrome at least but doesn't do forwards / backwards as expected.

Running xev reports no events during 2 finger horizontal scrolling, but button 6 / 7 events during 3 finger horizontal swipe. I have enabled horizontal scrolling under Mouse preferences (and this works fine with the synaptics driver).

@kosumi68 - does this sound about right? I'm using current git head at 0627d6038e1e460a1ec279c5670eda2e7f044c94.

---

### Post by kosumi68 on 2010-02-03
Great! Yep, spot on. The two-finger horizontal scroll is not implemented, so the behavior is quite expected. I use a custom fdi file in /etc/hal/fdi/policy/11-touchpad.fdi, which loads the multitouch driver instead of the synaptics driver, otherwise my setup is very similar.

I have been thinking a little bit about the two-finger click versus the drag-and-drop problem on the integrated trackpads, and I wonder about the behavior under some extreme conditions. The questions should determine if the basic behavior is to recognize fingers from different hands, or if the position on the trackpad is more important. So, in OSX,

1. Place one finger in the center of the pad. Place one finger from the other hand beside the first finger, and press. What is happens?

2. Place one finger in the center of the pad. Place one finger from the other hand at the very bottom of the pad, move it around a bit, then press. What happens?

3. Place one finger in the center of the pad. Use the thumb of the same hand to press at the bottom of the pad. What happens?

4. Place two fingers from the same hand on the pad and press. What happens?

---

### Post by DizzyTech on 2010-02-03
Okay, I think I got it compiled.  Really excited.  As a matter of fact, xserver-xorg-dev was the first thing I installed - but I never did remove the 11-x11-synaptics.fdi file, though I had removed the synaptics driver through Synaptics (whoa... ;) ).

As far as your questions:
[LIST=1]
[*]This is a standard two-finger click, although it'll vary depending on how close they are.
[*]Nothing.  This is actually very pleasing about OS X, and a tiny bit jarring when using Linux.  Leave your palm (or another finger) on the corner of the touchpad and it has zero effect.
[*]A single-finger click.  I actually do this a ton.
[*]A two-finger click.
[/LIST]

---

### Post by kosumi68 on 2010-02-04
Thank you for the answers. Regarding number two on the list, I realize there was an ambiguity in the question, so lets split it into two:

2a: Place one finger in the center of the pad. Place one finger from the other hand at the very bottom of the pad and press. What happens?

2b: Place one finger in the center of the pad. Place one finger from the other hand at the very bottom of the pad, then press with the first finger. What happens?

---

### Post by arturoc on 2010-02-09
hi

have been giving a try to this, and think i have something more or less working as in mac os x.

the idea is not try to identify fingers by their absolute position or size (although comparing major and minor for the thumb at the bottom works more or less) but compare relative distance between fingers and amount of displacement in x and y for detecting the thumb.

attached is a test, the code is super ugly but works:

thumb at the bottom + one finger: moves and only the finger in the higher part controls the movement
thumb + one finger and press: drag and drop
thumb at the bottom + 2 fingers: vertical scroll
two fingers moving in y: vertical scroll
thum at the bottom + 2 fingers and press: right click
two fingers and press: right click

i think in mac os x it also has into account if one finger id was previously the finger at the bottom and keeps it even if there's no more fingers unless you pass some movement threshold in any direction.

---

### Post by ejohney on 2010-02-10
Wow, this is working great for me so far, thank you! I will keep testing and see what I find

---

### Post by miatawnt2b on 2010-02-25
installed the bcm5974, installed multitouch from git and removed the 11-x11-synaptics.fdi file from  /usr/share/hal/fdi/policy/20thirdparty/

rebooted and I have no touchpad.  What did I do wrong?

Thanks,
-J

---

### Post by dennis.jarosch on 2010-03-05
Has anybody gotten this to work with Lucid Lynx?

I have a MacBookPro5,5 and was able to check out and compile the current version of the mutitouch driver.

In order for it to be loaded by the xserver, I had to edit 

/lib/udev/rules.d/66-xorg-synaptics.rules

and replace synaptics with multitouch. Since the xserver has migrated from hal to udev, editing the fdi file will no longer work.

The multitouch driver is now loaded but only clicking works. I cannot move the pointer and xev does not report any events.

Can anybody drop me a hint?

---

### Post by kosumi68 on 2010-03-06
> **dennis.jarosch said:**
> 
[...]
I have a MacBookPro5,5 and was able to check out and compile the current version of the mutitouch driver.
[...]
The multitouch driver is now loaded but only clicking works. I cannot move the pointer and xev does not report any events.

Can anybody drop me a hint?

Perhaps you are not running the mactel version of bcm5974? It is the only version out there with kernel MT support.

---

### Post by NiñoScript on 2010-03-07
I want to help here, but I have no idea how :P
I know how to program, but I'm just moving to Linux&#8230;

Can you tell me at least how to install what you have?
If I know how to do that, I could play a little with the code


[COLOR="Silver"]I'm really sorry if my english is not so good[/COLOR]

---

### Post by dennis.jarosch on 2010-03-08
Thanks kosumi,

You were correct. After installing bcm5974 from the Mactel PPA, the touchpad became usable. I noticed it is much more sensitive than with synaptics and most importantly (for me): taps aren't working.

I guess you are busy, but do you have any idea when taps-to-click will be implemented? Or is there already a way to configure the touchpad behavior? I have quickly scanned through the code, but haven't found anything yet.

I have never programmed Xorg related stuff, but if there's a way I can help out...

---

### Post by NiñoScript on 2010-03-08
So, I managed to compile it, I did: ```
make
sudo make install
```
I wanted to edit /lib/udev/rules.d/66-xorg-synaptics.rules but it wasn't there, so I created the file with ```
ENV{x11_driver}="multitouch"
``` in it…

Didn't work.

Can you help me install it? :P

---

### Post by dennis.jarosch on 2010-03-09
Niño,

> 
I wanted to edit /lib/udev/rules.d/66-xorg-synaptics.rules but it wasn't there, so I created the file with ```
ENV{x11_driver}="multitouch"
``` in it…

These instructions were for Lucid Lynx only. If you are using Karmic, you need to edit the file 11-x11-synaptics.fdi.

---

### Post by NiñoScript on 2010-03-09
Yay, it works! :D

I think it just needs a threshold for moving the actual cursor, when I click, sometimes the cursor moves.
I'll have fun with the code now :P

---

### Post by kosumi68 on 2010-03-09
I am glad to see things are moving forward! :-) Kudos to arturoc for the first gesture patch, bringing us closer to full Macbook support. Perhaps you would be interested in cleaning it up a bit and submitting it for inclusion?

---

### Post by arturoc on 2010-03-13
yeah, sure, i'm going to have some time during the weekend, will give it a try. also if someone test it and want to post some bugs...

also, i see this commit in git:

janitor: stick to kernel-style formatting
    
    With this commit, the whole code base complies with the
    kernel format style, and patches can be checked against
    the kernel-provided ./scripts/checkpatch.pl

 is there any style guide or something similar for the code that i can  take a look, or some advice on how to organize it?

---

### Post by arturoc on 2010-03-13
here's a new version:

- basic filter for the movement so the cursor is more stable
- keep last gesture so the touchpad doesn't move after a scroll if one finger is released slightly before the other
- horizontal scroll working in the correct direction with 2 fingers


i'm going to clean the code and send you a patch, meanwhile if someone can test this and find any bug, please post here.

---

### Post by kosumi68 on 2010-03-13
> 
is there any style guide or something similar for the code that i can  take a look, or some advice on how to organize it?
    

If you have a kernel git tree available, the perl script to run is in scripts/checkpatch.pl. I have attached a copy of that file here. To test a file, do
```

./checkpatch.pl --no-tree --file somefile.c

```

To test a patch, do
```

./checkpatch.pl --no-tree somepatch.patch

```

Cheers!

---

### Post by alexmurray on 2010-03-13
For kernel coding style see the folllowing:

[http://www.kernel.org/doc/Documentation/CodingStyle](http://www.kernel.org/doc/Documentation/CodingStyle)
[http://www.linuxjournal.com/article/5780](http://www.linuxjournal.com/article/5780)

Since GNOME recommend the same style as well as the kernel their page on coding style also has some more info:

[http://developer.gnome.org/doc/guides/programming-guidelines/code-style.html](http://developer.gnome.org/doc/guides/programming-guidelines/code-style.html)

---

### Post by mcoleman44 on 2010-03-13
You might want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

It will give you some insight to all the problems were having right now with multi-touch and n-trig devices.

---

### Post by arturoc on 2010-03-14
hey

so everything seems to be working, and the checkpatch script tells there's no errors in the formatting.

i've used some constants for checking distances and times in defnes, i suppose it can be useful to be able to configure them from outside the code.  also don't know if this is going to be used for other touchpads than the macbook, but i suppose some values will change in that case.

anyway, whats the best way to submit the changes?

---

### Post by kosumi68 on 2010-03-15
> **arturoc said:**
> hey

so everything seems to be working, and the checkpatch script tells there's no errors in the formatting.

i've used some constants for checking distances and times in defnes, i suppose it can be useful to be able to configure them from outside the code.  also don't know if this is going to be used for other touchpads than the macbook, but i suppose some values will change in that case.

anyway, whats the best way to submit the changes?

Great! Just drop a mail to [email]patches@bitmath.org[/email].

---

### Post by NiñoScript on 2010-03-15
> **arturoc said:**
> anyway, whats the best way to submit the changes?

I guess you could post it here?
That way I can try it out too :P

---

### Post by arturoc on 2010-03-16
here it is, i've been talking with henrick and the code needs some more cleaning but the functionality is pretty solid as far as i've tested. post if you find something wrong.

---

### Post by NiñoScript on 2010-03-16
lots of errors like this ones:
```
src/gestures.c:###: error: &#8216;struct MTouch&#8217; has no member named &#8216;ohs&#8217;
src/gestures.c:###: error: &#8216;struct MTouch&#8217; has no member named &#8216;nhs&#8217;

```
What am I missing? Did you change the definition of that struct?

It is defined in mtouch.h like this: [&#8230;] struct State os, ns;

(I changed those names and installed, but if I'm missing something, please tell me :))

---

### Post by arturoc on 2010-03-16
hey sorry

i began to modify the code and didn't realize when i posted. here's the correct files

---

### Post by NiñoScript on 2010-03-16
I have a little problem… If I put two fingers in the upper part of the trackpad, and scroll from there, I get logged out of gnome! :O

I started having these seemingly random logouts, and after a while I realized that it had to do with the trackpad.

Do you think this has to do with this drivers?

---

### Post by NiñoScript on 2010-03-16
> **arturoc said:**
> post if you find something wrong.

The cursor is a lot more stable when clicking, but it suddendly stops recognizing my thumb as the "clicking finger" and gives false right-clicks or starts scrolling.
That makes it pretty hard to use, so I had to go back the the other version.

BTW, is there anywhere (chat, mail, etc) that I could contact with you? I'd like to help coding, but I open gestures.c and I can't follow it :P and I'm not sure where to start learning…
In the meantime, I'll just be your most active beta tester :D
(or pre-alpha tester…)

---

### Post by arturoc on 2010-03-17
there are some constants at the beginning of the file that are hardcoded for my computer an i was suspecting that it will work differently for other computers. you can try changing them to see if it makes it work better.

i'm getting no false positives and the thumb is not lost at any time. the way i detect the thumb is by getting the lowest finger , then i check if it's moving in the vertical direction along with the other finger as in mac os x doing that it begins to scroll from a certain threshold. then i check that it's in the lower part of the touchpad that i consider to be of the size of the button in older macbooks. 

can you try to identify when it looses the thumb. the constants that affect the thumb detection are:

#define BOTTOM_MOVEMENT_THRES 0.001
#define BOTTOM_Y_AREA 0.12

i've detected also the crash that you're talking about, want to try with the previous version since it seems something related with a division by 0 given that it only happens at the very top of the touchpad but can't see nothing in my code that can be causing it.

---

### Post by NiñoScript on 2010-03-17
I don't notice changes when I change those constants&#8230; maybe I'm doing something wrong, I added this to the makefile:
```
everything:
	make clean
	make install
	modprobe -r bcm5974
	modprobe bcm5974
```
is that ok for testing?

---

### Post by arturoc on 2010-03-17
no, that reloads the touchpad kernel module, what you want to reload is the xserver multitouch driver. you need to close the session and start login again or:

sudo service gdm restart


btw. is there a way to tell xserver to reload a driver without restarting it?

---

### Post by NiñoScript on 2010-03-17
Ok, that works, to me it works better with bigger numbers.
I'm trying now with these numbers:
```
#define BOTTOM_MOVEMENT_THRES 0.111
#define BOTTOM_Y_AREA 0.22
```
I think I can lower BOTTOM_Y_AREA a bit, and BOTTOM_MOVEMENT_THRES a lot, but at least I felt the change :)

What I've noticed from the MacOSX driver, that makes it really accurate, is that the movement of the cursor is proportional to the speed of your finger, and that is true for scrolling too.
I somehow feel that this is happening here too, but it speeds up too fast and saturates&#8230;
I'm not sure if you understand what I'm trying to say, as my english is not so good :P

EDIT:
Ok, I kind of like it with:
```
#define BOTTOM_Y_AREA 0.18
```
In MacOSX, when you put your finger in the bottom part, it's recognized as the "clicking finger", and then you can do whatever with it, and it won't affect, unless you move it upper than the other finger, so there's no movement threshold and you can get the finger out of the "BOTTOM_Y_AREA" without it starting to scroll.

---

### Post by NiñoScript on 2010-03-21
> **arturoc said:**
> […] then i check that it's in the lower part of the touchpad that i consider to be of the size of the button in older macbooks. […]

Trackpad buttons in older macbooks were about a third of the whole trackpad:
[IMG]http://www.slashgear.com/gallery/data_files/7/4/MacBook_touchpad.jpg[/IMG]

---

### Post by kosumi68 on 2010-03-21
> **NiñoScript said:**
> 
What I've noticed from the MacOSX driver, that makes it really accurate, is that the movement of the cursor is proportional to the speed of your finger, and that is true for scrolling too.

I somehow feel that this is happening here too, but it speeds up too fast and saturates…
I'm not sure if you understand what I'm trying to say, as my english is not so good :P

EDIT:
Ok, I kind of like it with:
```
#define BOTTOM_Y_AREA 0.18
```
In MacOSX, when you put your finger in the bottom part, it's recognized as the "clicking finger", and then you can do whatever with it, and it won't affect, unless you move it upper than the other finger, so there's no movement threshold and you can get the finger out of the "BOTTOM_Y_AREA" without it starting to scroll.

Thanks for testing this out! The acceleration used in X is suitable for mouse movements, but less so for trackpads, I agree. Thanks also for the information about the clicking finger.

---

### Post by NiñoScript on 2010-03-22
> **kosumi68 said:**
> Thanks for testing this out! The acceleration used in X is suitable for mouse movements, but less so for trackpads, I agree. Thanks also for the information about the clicking finger.

I'll be happy to help in anyway I can, as the development of this driver is something vital to me and every macbook user that want's to give linux a try :)

In fact, this thread is my homepage! ;)

---

### Post by porl on 2010-03-24
i'm sure i'm just doing something stupid, but i can't get the module to load to test it.

i had it compile cleanly, and ran make install to put the module in the right place, then edited the /lib/udev/rules.d/66-xorg-synaptics.rules file to change 'synaptics' to 'multitouch' (i'm running lucid)

unfortunately the xorg log shows the original synaptics driver loading (if i move that out i get no trackpad function at all, so it isn't loading both, just the synaptics one).

is there anything i have missed?

---

### Post by linuxopjemac on 2010-03-24
what's the name of that module, multitouch?

what about a good old fashioned
```
sudo modprobe multitouch
```

?

---

### Post by alexmurray on 2010-03-24
No, multitouch is an xserver driver not a kernel module so you don't modprobe it, you have to get the xserver to load it via udev or similar rules, so porl's attempts appear to be correct... not sure why its not working

---

### Post by jfrorie on 2010-03-24
> **alexmurray said:**
> No, multitouch is an xserver driver not a kernel module so you don't modprobe it, you have to get the xserver to load it via udev or similar rules, so porl's attempts appear to be correct... not sure why its not working

I'm not running a Mac, so I'm not sure the compatibility, but I'm seeing the same thing as porl.  Here is a xorg.log snippet.

(II) XINPUT: Adding extended input device ""AT Translated Set 2 keyboard"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device "SynPS/2 Synaptics TouchPad" (/dev/input/event9)
(II) LoadModule: "multitouch"
(II) Loading /usr/lib/xorg/modules/input/multitouch.so
(II) Module multitouch: vendor="X.Org Foundation"
	compiled for 1.7.5, module version = 0.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) "SynPS/2 Synaptics TouchPad": always reports core events
(II) XINPUT: Adding extended input device ""SynPS/2 Synaptics TouchPad"" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/event9"
(II) multitouch: caps: left middle right
(II) pointer_control
(**) "SynPS/2 Synaptics TouchPad": (accel) keeping acceleration scheme 1
(**) "SynPS/2 Synaptics TouchPad": (accel) acceleration profile 0
(II) device control: on
(II) pointer_property
(II) pointer_property
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event3)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/event3"
(II) "Macintosh mouse button emulation": Found 3 mouse buttons
(II) "Macintosh mouse button emulation": Found relative axes
(II) "Macintosh mouse button emulation": Found x and y relative axes
(II) "Macintosh mouse button emulation": Configuring as mouse
(**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
(**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
(**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
(**) "Macintosh mouse button emulation": (accel) acceleration profile 0
(II) "Macintosh mouse button emulation": initialized for relative axes.
(II) pointer_control
(II) pointer_control
(II) pointer_control
(II) pointer_control
(II) pointer_property
(II) pointer_property

Repeated about 59 times...

(II) pointer_property
(II) pointer_property
(II) pointer_property
(II) pointer_property

---

### Post by porl on 2010-03-25
thanks for the suggestions, but it turned out to be simply that i hadn't rebooted (i restarted X but now that i think of it, there are udev changes so that also needs restarting etc.)

i am now having another problem which has been referred to before, where the mouse doesn't move, only clicking works. i assumed i must have just had the non-patched bcm5974 kernel module as was the case for the previous poster, but i have triple checked that the patched one is in use and the original removed. i've restarted a number of times to no avail. anything else i should check? is there a more up to date bcm5974 patch i am missing? i know that there is not yet a lucid repository for mactel, so i used the karmic one. is there something newer?

---

### Post by NiñoScript on 2010-03-25
I just installed Lucid, and it worked for me, I did this:

01.- Deactivate tapping and activate two-finger scrolling so I could use the trackpad just enough to navigate this forum :P
02.- Add the Karmic mactel repository
03.- sudo apt-get install bcm5974-dkms git-core
05.- git clone [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)
06.- Download the latest version of gesture.c
07.- Replace the one in ~/multitouch/src with it
08.- Change the values of BOTTOM_MOVEMENT_THRES and BOTTOM_Y_AREA to 0.3 and 0.22 respectively
09.- sudo make install
10.- sudo gedit /lib/udev/rules.d/66-xorg-synaptics.rules
11.- Change ENV{x11_driver} to "multitouch"
12.- restart

I think that's all I did.

---

### Post by porl on 2010-03-25
hmm... looks the same as what i did, although i installed the deb package manually rather than using the repository. i might try re-enabling the mactel ppa and see if it has something i am missing.

edit: just added the ppa and the module package had an update. i must have accidentally grabbed an earlier version. all working wonderfully now! :)

i wonder, can synclient etc be patched to be compatible with this? obviously not every option is relevant, but just things like acceleration etc. or is this a completely fresh start with nothing shared?

---

### Post by jfrorie on 2010-03-25
Is bcm5974 required even for non-macs?  I'm running a sony vaio, which has limited touchpad support out of the box.

---

### Post by NiñoScript on 2010-03-25
> **jfrorie said:**
> Is bcm5974 required even for non-macs?  I'm running a sony vaio, which has limited touchpad support out of the box.
I think I read that that version had support for multitouch and the others didn't, if that's right, then "yes" I guess

---

### Post by NiñoScript on 2010-03-25
> **porl said:**
> hmm... looks the same as what i did, although i installed the deb package manually rather than using the repository. i might try re-enabling the mactel ppa and see if it has something i am missing.

edit: just added the ppa and the module package had an update. i must have accidentally grabbed an earlier version. all working wonderfully now! :)

Great!, it feels nice to know that my little "walkthrough" was useful :D
Makes me feel like if I were paying for the driver :P
&#8230; or being paid with a driver for trying to help :o

---

### Post by _mario_ on 2010-03-25
> **jfrorie said:**
> Is bcm5974 required even for non-macs?  I'm running a sony vaio, which has limited touchpad support out of the box.

I can't answer the original question but another related one. The bcm5974 driver (and its updated version in the mactel PPA) is supposed to drive broadcom touchpads used by Apple (wellspring 1/2/3). If your machine doesn't incorporate such a touchpad, you can't even load this driver.

ciao,
Mario

---

### Post by NiñoScript on 2010-03-26
> **kosumi68 said:**
> The acceleration used in X is suitable for mouse movements, but less so for trackpads, I agree.

I went to Mouse settings, and turned the sensibility all the way up.
That makes it behave a lot more mac-like!
I don't know why I had it to the lowest setting :P

I'm now using BOTTOM_Y_AREA as 0.25
and BOTTOM_MOVEMENT_THRES as a huge number so it doesn't work
I quite like it this way :)

---

### Post by NiñoScript on 2010-03-31
Something happened when I updated Lucid, a moment ago!
The file "/lib/udev/rules.d/66-xorg-synaptics.rules" changed! now I can't get the driver to work :\
I tried just adding the x11_driver line, but it doesn't work :O
```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

# Placeholder for platform specific quirks needing
# ID_INPUT.tags to be set.
ATTR{[dmi/id]product_name}=="Inspiron 1011", ENV{ID_INPUT.tags}="inspiron_1011"
ATTR{[dmi/id]product_name}=="Inspiron 1012", ENV{ID_INPUT.tags}="inspiron_1012"
ATTR{[dmi/id]product_name}=="HP MiniNote 1000", ENV{ID_INPUT.tags}="mininote_1000"

LABEL="xorg_synaptics_end"
```

---

### Post by arturoc on 2010-04-02
it seems the x11_driver option in udev rules was deprecated and the change got in lucid with the last update to the new version of Xserver.

you can setup the driver again by using /etc/X11/xorg.conf

```
Section "InputClass"
    MatchIsTouchpad "true"
        Identifier      "Multitouch Touchpad"
        Driver          "multitouch"
EndSection
```there should be a better way of doing this by creating a custom rule in xorg.conf.d but haven't investigated further

---

### Post by NiñoScript on 2010-04-02
Yay! thanks! :D
at last, I can use it again&#8230; I almost returned to MacOSX, just because of that :P

---

### Post by therobbot on 2010-04-06
Hi,

it's great that somebody started development of this. Compared to OSX the Macbook touchpad just feels clunky in Linux.

In OSX I use a great tool called BetterTouchTool that makes lots of great gestures available. I think it is not open source at the moment but the developer is a student and seems to be a nice guy so maybe he would share his code (or could be convinced to make it open source). 

Another thing I'm wondering about is if you should try to plan the whole thing more modular from the start. At some point you will want to assign gestures to actions so it should really have a gestures detection and a seperate action handler. Maybe I don't want 3-finger click to be a middle click but to launch an application or whatever.

Just some suggestions. Unfortunately I don't think I'll find the time to code right now but I'm looking forward to what you will come up with!

Tobias

---

### Post by ejohney on 2010-04-11
Just wondering if tap to click is supposed to be working at this point? I can't get it to work on lucid

---

### Post by kosumi68 on 2010-04-11
> **NiñoScript said:**
> 
In MacOSX, when you put your finger in the bottom part, it's recognized as the "clicking finger", and then you can do whatever with it, and it won't affect, unless you move it upper than the other finger, so there's no movement threshold and you can get the finger out of the "BOTTOM_Y_AREA" without it starting to scroll.

I have two questions for you, we should be able to copy the behavior more or less exactly:

1. Do you need to click before it is recognized as the clicking finger?

2. If you start the touch in the middle of the pad, then move it to the bottom, is it then recognized as the clicking finger?

---

### Post by kosumi68 on 2010-04-11
> **ejohney said:**
> Just wondering if tap to click is supposed to be working at this point? I can't get it to work on lucid

I suspect you want it to work? :-) Actually, it is really worth a poll. How many owners of a macbook, with and without integrated button, use the tap-to-click feature?

---

### Post by therobbot on 2010-04-11
> **kosumi68 said:**
> I suspect you want it to work? :-) Actually, it is really worth a poll. How many owners of a macbook, with and without integrated button, use the tap-to-click feature?

I almost never click. I tap a lot an swipe and tip-tap and make all kinds of gestures since using BetterTouchTool in OSX. In Linux the touchpad really feels very restricted to me now...

Tobias

---

### Post by alexmurray on 2010-04-11
I hate tap-to-click - too easy to accidentally click stuff - so I never enable it, especially on my mbp5,1 with integrated button.

---

### Post by buntuLo on 2010-04-12
i never click. only 1-, 2-, 3-fingers taps, and 2-fingers vertical and horizontal scroll.

---

### Post by kosumi68 on 2010-04-12
Thanks for the answers, it looks like tapping ought to be implemented as well. Patches are always welcome...

Ok, ready for some more testing? :-) I updated the git tree, the "next" branch, with code resulting from merging most of Arturo's work with my own. The branch includes support for two-finger vertical and horizontal scroll, three-finger vertical and horizontal swipe, proper filtering based on the linux kernel code, and a new approach to dealing with the clicking fingers of the integrated trackpad. I am very interested to hear what you think of it.

Cheers!

---

### Post by NiñoScript on 2010-04-12
> **kosumi68 said:**
> I have two questions for you, we should be able to copy the behavior more or less exactly:

1. Do you need to click before it is recognized as the clicking finger?
No, you just need two fingers vertically apart

> **kosumi68 said:**
> 
2. If you start the touch in the middle of the pad, then move it to the bottom, is it then recognized as the clicking finger?
As soon as you put another finger on top


If you start moving the bottom finger up, at the point where it gets higher than the other, the cursor starts moving, and the other finger is now the clicking finger

---

### Post by NiñoScript on 2010-04-12
> **kosumi68 said:**
> I suspect you want it to work? :-) Actually, it is really worth a poll. How many owners of a macbook, with and without integrated button, use the tap-to-click feature?
I've never liked tapping, because of false clicks, but sometimes I activate it when I'm in classes or it's too late and there are people sleeping, it's a lot quieter.
Also, I've got carpal tunnel syndrome in my right hand a couple of times, I activate tapping then too

---

### Post by NiñoScript on 2010-04-12
> **kosumi68 said:**
> Thanks for the answers, it looks like tapping ought to be implemented as well. Patches are always welcome...

Ok, ready for some more testing? :-) I updated the git tree, the "next" branch, with code resulting from merging most of Arturo's work with my own. The branch includes support for two-finger vertical and horizontal scroll, three-finger vertical and horizontal swipe, proper filtering based on the linux kernel code, and a new approach to dealing with the clicking fingers of the integrated trackpad. I am very interested to hear what you think of it.

Cheers!
I have no idea how to use git, apart from "clone" :P
How do I get to that that branch?

---

### Post by kosumi68 on 2010-04-13
> **NiñoScript said:**
> I have no idea how to use git, apart from "clone" :P
How do I get to that that branch?

To get the code from scratch:
```

git clone http://bitmath.org/git/multitouch.git
cd multitouch
git checkout -b next origin/next
make

```

The longer version is to first update the code with "git fetch", then look at the tree with "gitk --all", then create a local branch equal to the remote with "branch -f next origin/next", then checkout that branch with "git checkout next", then compile and run. You can do most of the branch stuff with gitk if you prefer graphical interfaces.

It will become easier again once we get some sanity testing on this new code. The alpha 2 will appear in the master branch, where there will be no need to fiddle with branches.

Cheers!

---

### Post by NiñoScript on 2010-04-13
```
error: &#8216;MT_BUTTON_SWEEP_****' undeclared
```

What happened? :O

---

### Post by kosumi68 on 2010-04-13
> **NiñoScript said:**
> ```
error: ‘MT_BUTTON_SWEEP_****' undeclared
```

What happened? :O

I see, you are running xinput7... never got to test that. If you change the "SWEEP" lines in src/multitouch.c to "SWIPE", it should work better. Also, the swipe button mappings for xinput7 are probably wrong, as the proper buttons seem to be undefined in X at this point. Hopefully it will still work; after all it is the integrated touchpad that is most interesting right now.

*goes to roll out a corrected patch sequence*

---

### Post by jfrorie on 2010-04-13
Any hints for those of us not running macbooks, but have multitouch pads?  Is this possible?  There are a load of us that would love to try this out.  The default synaptics driver is giving us fits. :)

---

### Post by NiñoScript on 2010-04-14
Is there still a threshold for the "clicking finger" movement?
In MacOSX that doesn't happen, you can move the lower finger a lot,
as long as it stays lower than the other finger it doesn't move the cursor/scroll.

Maybe it's a good idea to have a threshold, as if you really move it a lot,
it may mean that you actually want to scroll or something with the lower finger;
but then, it should be a big threshold;
right now, the very small movement that my upper finger does on my whole hand
(probably not bigger than 1 milimeter in the direction I'm moving my finger)
is being enough to sometimes give a false scrolling.

On the other side, I can swipe (sweep?) up and down to go back and forth in my browsers current tab history :D
(In MacOSX it's swipe left and right, but who cares, this isn't MacOSX :P)


BTW, horizontal scrolling isn't working too great here, I'm not sure how to explain the isue, but it's like very few huge steps instead of lots of small ones like the vertical one :\

Oh, and thanks for fixing the "scroll at the top restarts X" bug, it was really anoying,
mostly because a friend saw it and was teasing me by logging me out of my session, just putting 2 fingers on the top part of the trackpad (I hate you Yanko)

---

### Post by kosumi68 on 2010-04-14
> **NiñoScript said:**
> Is there still a threshold for the "clicking finger" movement?
In MacOSX that doesn't happen, you can move the lower finger a lot,
as long as it stays lower than the other finger it doesn't move the cursor/scroll.


No special threshold for the clicking finger, but a finger can participate in a movement gesture regardless of where it on the pad. It was made that way purposely, but apparently it is still not how it works in OSX. Bummer.

> 
Maybe it's a good idea to have a threshold, as if you really move it a lot,
it may mean that you actually want to scroll or something with the lower finger;
but then, it should be a big threshold;
right now, the very small movement that my upper finger does on my whole hand
(probably not bigger than 1 milimeter in the direction I'm moving my finger)
is being enough to sometimes give a false scrolling.


This is how it works currently: The fingers participating in a move gesture are called the active fingers. The number of active fingers is the maximum of the number of pointing fingers and moving fingers. The pointing fingers are generally the ones above the clicking area, but a single finger can point anywhere on the pad, and the clicking fingers may rest above the clicking area as long as the bottom finger stays the same. The moving fingers are those moving jointly on the pad.

From what I gather, this is almost correct, except movement should only be extracted from fingers strictly above the clicking area. How does that sound?

> 
On the other side, I can swipe (sweep?) up and down to go back and forth in my browsers current tab history :D
(In MacOSX it's swipe left and right, but who cares, this isn't MacOSX :P)


Nice :-)

> 
BTW, horizontal scrolling isn't working too great here, I'm not sure how to explain the isue, but it's like very few huge steps instead of lots of small ones like the vertical one :\


That is precisely how it is implemented. The scales for horizontal scroll and horizontal swipe are currently the same. I suspect separate scales for scrolling and swiping will fix this.

> 
Oh, and thanks for fixing the "scroll at the top restarts X" bug, it was really anoying,
mostly because a friend saw it and was teasing me by logging me out of my session, just putting 2 fingers on the top part of the trackpad (I hate you Yanko)


I intend to make it very hard for you to find problems like that in the mainline driver :-)

Cheers!

---

### Post by NiñoScript on 2010-04-14
If you want, I can make some testing/asking in MacOSX and give a detailed report on how it exactly works :P
Maybe even with video included :D
I guess this weekend I may have enough time

---

### Post by kosumi68 on 2010-04-14
> **NiñoScript said:**
> If you want, I can make some testing/asking in MacOSX and give a detailed report on how it exactly works :P
Maybe even with video included :D
I guess this weekend I may have enough time

That would be cool, something for youtube (unless its already there :-O)

One more question: What about two-finger click? Is that also unaffected by moving the clicking finger above the clicking area?

---

### Post by kosumi68 on 2010-04-14
Ok, new version in next. This might even become alpha-2 in master if tests are positive. The horizontal scrolling should work better now, and I believe the integrated button is pretty well covered; nothing happens when the clicking finger moves, up to the point where the other (bottom pointing finger) was when the fingers were put there. Scrolling with two fingers when either or both start off in the clicking area works smoothly, too.

Cheers!

---

### Post by kosumi68 on 2010-04-14
> **jfrorie said:**
> Any hints for those of us not running macbooks, but have multitouch pads?  Is this possible?  There are a load of us that would love to try this out.  The default synaptics driver is giving us fits. :)

It all boils down to what hardware currently has kernel support for MT events. In the latest and greatest kernel, these drivers have MT support:

drivers/hid/hid-3m-pct.c
drivers/hid/hid-debug.c
drivers/hid/hid-magicmouse.c
drivers/hid/hid-mosart.c
drivers/hid/hid-ntrig.c
drivers/hid/hid-quanta.c
drivers/hid/hid-stantum.c
drivers/input/input.c
drivers/input/mouse/bcm5974.c
drivers/input/touchscreen/usbtouchscreen.c

Some of them are available in 2.6.32, which lucid is based on. Some of them have been applied as extra patches to lucid. Some of them might be available as dkms packages. Which driver would apply to you?

---

### Post by kwiksand on 2010-04-14
Thankyou!

Had a couple of issues with the bcm5974 driver, and it unloading during X startup.  If anyone else has the same issue:

Add usbhid to the blacklist firstly, so it doesn't load - **/etc/modprobe.d/blacklist.conf**

**usbhid**

Add bcm5974, then usbhid to **/etc/modules** so that it loads as expected and then usbhid continues as normal afterwards

[B]bcm5974
usbhid[/B]


Anyway, it seems to be working well now, after using the Macbook for so long in MacOSX on the MBP for so long, the touchpad is key, and being without the drag/drop was an issue to say the least.  Kudos to the developer(s)!

One thing: I'm not sure of the correct terminology, but when you attempt to drag and drop (two fingers down, then dragging by moving one finger (normal).  Is there any way to speed up the drag speed??

---

### Post by kosumi68 on 2010-04-15
Multitouch X Driver v1.0-alpha2

The alpha2 is now released, and can be found in the master branch of the git tree. Thanks to NinoScript for testing things out. The shortlog since last version is appended.

Cheers!

---

Arturo Castro (4):
      Reverse the order of the hscroll buttons
      Delay movement after a finger configuration change
      Drop movement during gesture decay
      Extract pointing fingers

Henrik Rydberg (29):
      janitor: remaining indentation fixed
      Introduce convenience function for device dimensions
      Matcher: support up to 32 fingers
      Matcher: convert distance matrix to integer
      Remove unused min/max definitions
      Add support for the ABS_MT_PRESSURE event
      Comply with MT syncronization protocol
      Add millisecond event times
      Correct double commit mistake
      Third time around (and use the next branch for...)
      Use the event source time instead of the arrival time
      Rename State to HWState
      Introduce the MTState
      Add MTState debug output
      Do not sort HWState fingers
      Introduce Memory
      Reorganize gesture code
      Only extract movement from identical finger configurations
      Keep logical buttons separate from the hardware ones
      Add robust position event filtering
      Add a gesture credits section
      Break out scrolling code
      Define swipe buttons
      Define swipe gestures
      Additional device information
      Add integrated button property to capabilities
      Add constant clicking area to capabilities
      Extract moving fingers
      Add memory debug convenience routines

---

### Post by miatawnt2b on 2010-04-15
I am having a problem retrieving from git.  It seems to start OK, but a few got's in I get the error:

```

error: Failed connect to bitmath.org:80; Operation now in progress (curl_result = 7, http_code = 0, sha1 = c7ed4cec501f10479a98e380d760670312101136)
error: Unable to find 7ed6ff82de6bcc2a78243fc9c54d3ef5ac14da69 under http://bitmath.org/git/multitouch.git
Cannot obtain needed blob 7ed6ff82de6bcc2a78243fc9c54d3ef5ac14da69
while processing commit 0587ab0488c46b61d175793f2deedc3a7aa9b600.
fatal: Fetch failed.

```

Any ideas?

---

### Post by kwiksand on 2010-04-15
Perfect, the dragging, horizontal scrolling is substantially better (and it was great already)

Great job!

---

### Post by miatawnt2b on 2010-04-15
OK, finally got things installed.  I am running Karmic.

I set the device in xorg.conf to be multitouch.  What do I have to do to the 11-x11-synaptics.fdi to get this working?

Thanks,
-J

---

### Post by finy on 2010-04-15
hello,

thank you for this improvement!

i have a question regarding the installation.

my system:
macbook pro 5,5 (unibody 2009)
ubuntu lucid lynx 10.04 daily with latest packages installed

i installed xorg-dev in addition to other compiling and building stuff.
after that i cloned your code from [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git).
after - make && sudo make install (all went fine)
i rebootet my system.

if i check the /var/log/Xorg.0.log i see that the multitouch.so doesn't get loaded.
does someone has a clue what to do?

thank you!

regards
finy

---

### Post by kosumi68 on 2010-04-15
The git master branch is updated with patches for three bugs: one common, one rather common and one rare, all resulting in jumpy or jittery motion or scrolling. Overall, motion seems fine now.

I looked a bit at tapping. It is not too hard to implement taps, double taps and tap-and-hold, but the major grief are all false positives associated with the tapping, even if delays and other related tricks are used. If someone comes up with a great and simple idea how to filter out thumbs, corner touches etc, I am all ears. Otherwise, I just cannot see how tapping could be useful to anyone...

Cheers!

---

### Post by jfrorie on 2010-04-15
> **kosumi68 said:**
> Which driver would apply to you?

That's a good question.  I assumed that you have a replacement for the synaptics driver, which is my hardware.  I'm beginning to think that there are two synaptics, a kernel module and and xorg driver.  If so, then my problem is with the kernel synaptics, not the xorg synaptics that you are replacing.

Is this correct?

---

### Post by kosumi68 on 2010-04-15
> **jfrorie said:**
> That's a good question.  I assumed that you have a replacement for the synaptics driver, which is my hardware.  I'm beginning to think that there are two synaptics, a kernel module and and xorg driver.  If so, then my problem is with the kernel synaptics, not the xorg synaptics that you are replacing.

Is this correct?

Quite so. If synaptics turns up when doing lsmod, you are running the kernel synaptics driver. What is your hardware, Vaio X?

---

### Post by jfrorie on 2010-04-15
> **kosumi68 said:**
> Quite so. If synaptics turns up when doing lsmod, you are running the kernel synaptics driver. What is your hardware, Vaio X?

Vaio S.  One of the new models.  Interestingly enough, I don't have a synaptics driver loaded. This is probably related to the detection bug we are struggling with.

---

### Post by paulinchen on 2010-04-16
Don't know if this is helpful but in Karmic I'm using this driver:

[http://randomtruth.110mb.com/blog/index.php/2009/03/30/v10-of-linux-multi-touch-released/comments/#comment100213-185710](http://randomtruth.110mb.com/blog/index.php/2009/03/30/v10-of-linux-multi-touch-released/comments/#comment100213-185710)

It does have most of the multitouchfeatures as osx and tapping works as well

---

### Post by finy on 2010-04-16
i got it working now with latest lucid packages karmic ppa bcm5974 package and latest git master.

furthermore i had to configure the driver in xorg.conf.

the driver works pretty good. but i have problems with drag and drop and text highlighting because of the movement of the pointer when i click to drag.

regards
finy

---

### Post by linuxopjemac on 2010-04-16
I mentioned the developments on the home page of mac.linux.be. Comments are welcome :)

---

### Post by kosumi68 on 2010-04-16
> **finy said:**
> i got it working now with latest lucid packages karmic ppa bcm5974 package and latest git master.

furthermore i had to configure the driver in xorg.conf.

the driver works pretty good. but i have problems with drag and drop and text highlighting because of the movement of the pointer when i click to drag.

regards
finy

Are you saying that drag and drop with one finger behaves differently on the integrated button version than on the others?

---

### Post by finy on 2010-04-16
no, if i want to highlight text or drag something i usually click with my right thumb, hold it and use another finger to move the cursor. and at clicking with the right thumb the cursor moves away from the position i want to click.

i just found out that if i have the second finger on the trackpad as i'm clicking then it's ok and almost no movement.

i use a macbook pro 5,5 without tapping enabled.

---

### Post by kosumi68 on 2010-04-16
> **finy said:**
> no, if i want to highlight text or drag something i usually click with my right thumb, hold it and use another finger to move the cursor. and at clicking with the right thumb the cursor moves away from the position i want to click.

i just found out that if i have the second finger on the trackpad as i'm clicking then it's ok and almost no movement.

i use a macbook pro 5,5 without tapping enabled.

Oh, I see - thanks for explaining this further. Will be looked into.

Cheers!

---

### Post by finy on 2010-04-16
thank you! :)
i think mac os x locks the position somehow if it detects a click.

---

### Post by kosumi68 on 2010-04-16
Ok, let's see if this is the explanation. The driver deliberately treats a single finger in the clicking area as a pointing finger, which will move the mouse just as if the finger was placed in the middle of the pad. If this is not how it works on the integrated trackpad, it explains the behavior finy is talking about - first move the pointer with a finger, then lift the finger, and use the thumb to press the clicking area. Normally, the thumb, as a pointing finger, is less inexact and will cause the pointer to move slightly before the click is executed.

If this is the case, the fix is really easy - the special case for a single finger just needs to be removed, rather saying that a finger in the clicking area _never_ causes any movement. Correct?

---

### Post by *Legion* on 2010-04-16
Please consider editing up-to-date install instructions into the first post and/or the website.

Sifting through the thread to try and piece them together is especially challenging with a touchpad that's not yet behaving properly. :)

---

### Post by kosumi68 on 2010-04-17
> ***Legion* said:**
> Please consider editing up-to-date install instructions into the first post and/or the website.

Sifting through the thread to try and piece them together is especially challenging with a touchpad that's not yet behaving properly. :)

Good idea, except it would have to be post number three...

The question out there right now is for the integrated button trackpad, whether a single finger at the bottom of the pad moves the cursor, but possibly stays still as the finger pressure increases during a click, or whether the finger simply does not move at all in the clicking area.

---

### Post by finy on 2010-04-17
sorry for the long delay,
i took a look at how the touchpad behaves in mac os x.

if i click and hold with one finger it is possible to move this finger over the whole pad and perform actions like drag and drop, text highlighting and to span the selection band.

if i click with the first finger in the upper half of the touchpad, it is possible to use the second finger to move the cursor as long as the second finger is in the upper half.
if i click with the first finger in the bottom half of the touchpad, i can use the whole pad with the second finger.

furthermore it is not possible to move the cursor with the balm, but if you have the balm on the pad it is full useable with the other hand (it is not generally locked or something).

the important part is, that the cursor does not move if you click with a finger, but does move if you slide your finger away.

a right click is detected if both fingers are not to far away from each other. the max. distance is greater horizontal and a little less in the vertical direction.

> The question out there right now is for the integrated button trackpad,  whether a single finger at the bottom of the pad moves the cursor, but  possibly stays still as the finger pressure increases during a click, or  whether the finger simply does not move at all in the clicking area.it seems that the finger does not move at all in the clicking area. but i don't know how they managed to do this. it is really great to use. the cursor does not move if i click but does instantly move if i slide the finger away. the detection seems to be more granular than simple lock the movement at click. don't know.

---

### Post by kosumi68 on 2010-04-18
Thank you for the thorough answers!

> **finy said:**
> 
the important part is, that the cursor does not move if you click with a finger, but does move if you slide your finger away.


I looked at this a bit; subtle and quite tricky. Solvable, but don't hold your breath. :-) 

Meanwhile, I have uploaded some bug fixes to git master. Here is the list since v1.0-alpha2:

Henrik Rydberg (10):
      janitor: Use more common row/column names
      Reset accumulated movement at finger configuration change
      Unify detection of finger configuration changes
      Reset scroll state on finger configuration change
      Correctly report zero fingers
      Do not reuse tracking ids after a no-touch event
      Make all movement computations work on pointing subset
      Filter non-zero finger width events
      Hold MT data during pure button events
      Only emit multi-finger button events for real button events

Cheers!

---

### Post by Taoye on 2010-04-18
Hey guys,

I'm having trouble installing this driver.

- I have the bcm5974-dkms package from the mactel repo
- I got the source by doing: git clone [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)
- I installed xserver-xorg-dev and then did make, make install from the multitouch directory
- I pasted the "InputClass" section from this thread into my xorg.conf

When I reboot the computer I get an error that my xorg.conf is not parseable because InputClass and MatchIsTouchpad are not valid keywords... if I remove the line, it parses properly but the multitouch driver isn't loaded, it seems to ignore the InputClass section. 

My PC is a MacBook Pro 5,5 and I'm running Lucid beta 2 (with updates as of tonight).

Any advice?

---

### Post by NiñoScript on 2010-04-19
Ok, I didn't have time this weekend, I forgot I had to study, do homework, and go to my girlfriend's mother's birthday :P

But as soon as I can, I will be doing the video I promised.

There are things that I think you are not aware, for example, I realized that MacOSX only detects a finger as the one for clicking if it is a thumb. It probably detects the size of the blob… In the video I'll use an application that I found once that let's you see the raw info of the trackpad, if I remember right, it's maximum 11 blobs of different sizes and shapes

---

### Post by kosumi68 on 2010-04-19
> **NiñoScript said:**
> 
There are things that I think you are not aware, for example, I realized that MacOSX only detects a finger as the one for clicking if it is a thumb. It probably detects the size of the blob…


I interpret this the following way:

Case A
------

A1. No fingers on the trackpad

A2. Put the index finger in the middle of the pad

A3. Press to click

Doing this, the pointer will still move noticably as the finger gets pressed harder against the surface. Correct?

Case B
------

B1. No fingers on the trackpad

B2. Put thumb in the middle of the pad

B3. Press to click

Doing the whole sequence, the pointer stays put at the same place. Correct?

If the interpretation is correct, the problem is not that hard, after all.

---

### Post by Taoye on 2010-04-19
OK it seems that moving the InputClass section to the bottom of my xorg.conf got it to load, but it still doesn't work. The module is unloading and I'm seeing a "can't grab device" error. Here's a snippet from my Xorg.0.log:

```
(II) config/udev: Adding input device bcm5974 (/dev/input/event5)
(**) bcm5974: Applying InputClass "evdev touchpad catchall"
(**) bcm5974: Applying InputClass "touchpad catchall"
(**) bcm5974: Applying InputClass "Multitouch Touchpad"
(II) LoadModule: "multitouch"
(II) Loading /usr/lib/xorg/modules/input/multitouch.so
(II) Module multitouch: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) bcm5974: always reports core events
(II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/event5"
(II) multitouch: devname: bcm5974
(II) multitouch: devid: 5ac 236 1
(II) multitouch: caps: left mtdata ibt touch_major touch_minor width_major width_minor orientation position_x position_y
(II) multitouch: touch: 0 2048
(II) multitouch: width: 0 2048
(II) multitouch: orientation: -16384 16384
(II) multitouch: position_x: -4460 5166
(II) multitouch: position_y: -75 6700
(II) pointer_control
(**) bcm5974: (accel) keeping acceleration scheme 1
(**) bcm5974: (accel) acceleration profile 0
(II) pointer_control
(**) bcm5974: (accel) acceleration factor: 2.000
(**) bcm5974: (accel) acceleration threshold: 4
(II) device control: on
(EE) multitouch: cannot grab device
[dix] couldn't enable device 11
(EE) Couldn't init device "bcm5974"
(II) UnloadModule: "multitouch"
(II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
(**) bcm5974: Applying InputClass "Multitouch Touchpad"
(**) bcm5974: always reports core events
(II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/mouse1"
(EE) multitouch: cannot configure device
(EE) Couldn't init device "bcm5974"
(II) UnloadModule: "multitouch"
```

I still have the synaptics section in my xorg.conf. Should it be there? Can someone show me their working xorg.conf? I've also tried blacklisting usbhid and then adding bcm5974 and usbhid into /etc/modules without effect.

---

### Post by kosumi68 on 2010-04-19
Hi Taoye,

thanks for providing the log output. It seems the multitouch driver fails to grab the device, suggesting some other device grabbed it first. Since you say you already have synaptics loaded, that is most likely the problem. Simply remove the synaptics section and you might be ok.

---

### Post by Taoye on 2010-04-19
Hey, thanks for the reply, I also tried that. When I boot without the synaptics section I see the following slightly different output in Xorg.0.log:

```
(II) config/udev: Adding input device bcm5974 (/dev/input/event6)
(**) bcm5974: Applying InputClass "evdev touchpad catchall"
(**) bcm5974: Applying InputClass "touchpad catchall"
(**) bcm5974: Applying InputClass "Multitouch Touchpad"
(II) LoadModule: "multitouch"
(II) Loading /usr/lib/xorg/modules/input/multitouch.so
(II) Module multitouch: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) bcm5974: always reports core events
(II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/event6"
(II) multitouch: devname: bcm5974
(II) multitouch: devid: 5ac 236 1
(II) multitouch: caps: left mtdata ibt touch_major touch_minor width_major width_minor orientation position_x position_y
(II) multitouch: touch: 0 2048
(II) multitouch: width: 0 2048
(II) multitouch: orientation: -16384 16384
(II) multitouch: position_x: -4460 5166
(II) multitouch: position_y: -75 6700
(II) pointer_control
(**) bcm5974: (accel) keeping acceleration scheme 1
(**) bcm5974: (accel) acceleration profile 0
(II) pointer_control
(**) bcm5974: (accel) acceleration factor: 2.000
(**) bcm5974: (accel) acceleration threshold: 4
(II) device control: on
(II) pointer_property
(II) pointer_property
(II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
(**) bcm5974: Applying InputClass "Multitouch Touchpad"
(**) bcm5974: always reports core events
(II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/mouse1"
(EE) multitouch: cannot configure device
(EE) Couldn't init device "bcm5974"
(II) UnloadModule: "multitouch"

```

Doing it this way, I still have keyboard and touchpad working but only basic functionality. It seems to succeed at grabbing the event device but it fails after the mouse1 part.

---

### Post by kosumi68 on 2010-04-19
The device gets loaded twice, once as an event device (correct), and once as a mouse (incorrect):

```

(II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)

```

Since the udev config is all new, I do not know how to remedy this problem (I am running karmic still), but ignoring the mouse should be possible, either at the udev level or xorg level.

---

### Post by Taoye on 2010-04-19
OK thanks, I'll see if I can figure that out.

Has somebody else gotten it working in Lucid? How have you configured it?

---

### Post by finy on 2010-04-19
hello,

i installed xserver-xorg-dev, fetched the code from git and installed by make && sudo make install. also, i added the karmic ppa and installed bcm5974-dkms.

my xorg.conf looks like this:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection
```

---

### Post by Taoye on 2010-04-19
For some reason that doesn't work for me... evdev and the macintosh button emulation both take over the device and the multitouch module always unloads.

I can insert InputClass sections into my xorg.conf to cause it to ignore mouse1 and event4, and then the multitouch module appears to load for event7 and it doesn't unload, but it doesn't seem to be working... I get basic touchpad pointing and two-finger scroll, but nothing else. It also seems to be incorrectly reporting parameters about the touchpad...

```
(II) config/udev: Adding input device bcm5974 (/dev/input/event7)
(**) bcm5974: Applying InputClass "evdev touchpad catchall"
(**) bcm5974: Applying InputClass "touchpad catchall"
(**) bcm5974: Applying InputClass "Multitouch Touchpad"
(II) LoadModule: "multitouch"
(II) Loading /usr/lib/xorg/modules/input/multitouch.so
(II) Module multitouch: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) bcm5974: always reports core events
(II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
(II) device control: init
(**) Option "Device" "/dev/input/event7"
(II) multitouch: devname: bcm5974
(II) multitouch: devid: 5ac 236 1
(II) multitouch: caps: left mtdata ibt touch_major touch_minor width_major width_minor orientation position_x position_y
(II) multitouch: touch: 0 2048
(II) multitouch: width: 0 2048
(II) multitouch: orientation: -16384 16384
(II) multitouch: position_x: -4460 5166
(II) multitouch: position_y: -75 6700
(II) pointer_control
(**) bcm5974: (accel) keeping acceleration scheme 1
(**) bcm5974: (accel) acceleration profile 0
(II) pointer_control
(**) bcm5974: (accel) acceleration factor: 2.000
(**) bcm5974: (accel) acceleration threshold: 4
(II) device control: on
(II) pointer_property
(II) pointer_property
(II) config/udev: Adding input device bcm5974 (/dev/input/mouse1)
(**) bcm5974: Ignoring device from InputClass "Mouse1 Catchall"
(II) config/udev: Adding input device applesmc (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device applesmc (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Ignoring device from InputClass "Macintosh Emulation Catchall"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) pointer_control
(II) pointer_control
```

Width and height are supposed to be 1200x800. Are there additional options for the multitouch driver that can be put in xorg.conf? I suppose I oughta wait for the final Lucid build for all the config stuff to settle down before getting deep into this.

---

### Post by kosumi68 on 2010-04-20
The 1280x800 resolution applies to the ABS_X event; the ABS_MT_POSITION_X event has a different resolution, the one you see in the logs. Nothing wrong there.

The macintosh mouse button emulation is a different device, not recognized as a touchpad, and does not effect you negatively in this case.

If you get two-finger scroll, it suggests it is actually working.

---

### Post by Taoye on 2010-04-20
You're right! It's working.

Here's why I thought it wasn't: three-finger swipe is working on the wrong axis. When I swipe left and right in Firefox it does nothing, but when I swipe up it goes back, down goes forward.

In Nautilus every direction of three finger swipe just selects the icon under the mouse, no back/forward events. [Edit: although on further reading this may be a fault with Nautilus... does anybody else get back/forward buttons working in Nautilus? With this driver or with a regular mouse?]

Two finger scrolling apparently works in both directions, although scrolling up doesn't always work... it seems like when I start scrolling from the bottom half of the touchpad, if my fingers aren't lined up horizontally it won't scroll.

I would love to see tapping to click implemented, and two-finger tap for right click... I hate having to click the all-in-one touchpad, and it hurts my finger after a while.

---

### Post by paulinchen on 2010-04-20
Maybe someone find this interesting:

[http://www.synaptics.com/solutions/technology/gestures/touchpad-linux](http://www.synaptics.com/solutions/technology/gestures/touchpad-linux)

Does anyone knows someone with access to an OEM? :P

---

### Post by kosumi68 on 2010-04-20
Interesting. Closed source makes me wonder about GPL infringements, especially when released this late in the game. They probably have the gesture patent mine field under control though, which could open some doors for us as well.

---

### Post by Taoye on 2010-04-20
On my integrated touchpad, if I start a vertical scroll from within the clicking area it usually ignores it, ie: it moves the pointer up until I reach the uppper part of the touchpad, at which point it starts the scroll... very annoying. It only scrolls in the clicking area if my two fingers are aligned horizontally. In OS X it doesn't seem matter what the orientation or location of the two fingers are, if they're going up, it scrolls up.

I suppose eventually there should be a user configurable option to disable the clicking area.... or, if tap to click is enabled, then disable the clicking area. Personally I find it really awkward... I never noticed this sort of behavior in OS X, but of course I'm the sort who likes tap to click. It's just so nice to tap with the glass touchpad.

---

### Post by kosumi68 on 2010-04-21
> **Taoye said:**
> In OS X it doesn't seem matter what the orientation or location of the two fingers are, if they're going up, it scrolls up.


Is this true if your scroll with a finger and a thumb?

> 
I suppose eventually there should be a user configurable option to disable the clicking area.... or, if tap to click is enabled, then disable the clicking area. Personally I find it really awkward... I never noticed this sort of behavior in OS X, but of course I'm the sort who likes tap to click. It's just so nice to tap with the glass touchpad.


It actually sounds like the synaptics driver is a better fit for you at this state. The clicking area is the only "advanced" feature that cannot accurately be implemented in synaptics, and the first one to get attention in this multitouch driver.

---

### Post by Taoye on 2010-04-26
Sorry for the delay-- it's exam period here and all.

I did a bit of testing with OS X: if I try to scroll with 2 fingers, even if one finger starts in the clicking area, it will scroll. However if I try to scroll using a thumb and finger, it moves the pointer. 

It feels like it detects the thumb, and sets it as the clicking finger. The clicking area seems to determine where it will detect the thumb... when I use a thumb+finger outside of the clicking area to scroll, it scrolls. Although the limits of the clicking area feel very "hazy."

I suppose you haven't implemented a way to differentiate the thumb from the other fingers? Currently using the multitouch driver it feels like any finger in the clicking area will be treated as the clicking finger, not just the thumb.

---

### Post by zeroti on 2010-04-26
is there a way to install this on a powerbook G4 with lucid? On OS X, I could use iScroll2 to get multitouch working.

---

### Post by kosumi68 on 2010-04-26
> **Taoye said:**
> Sorry for the delay-- it's exam period here and all.

I did a bit of testing with OS X: if I try to scroll with 2 fingers, even if one finger starts in the clicking area, it will scroll. However if I try to scroll using a thumb and finger, it moves the pointer. 

It feels like it detects the thumb, and sets it as the clicking finger. The clicking area seems to determine where it will detect the thumb... when I use a thumb+finger outside of the clicking area to scroll, it scrolls. Although the limits of the clicking area feel very "hazy."

I suppose you haven't implemented a way to differentiate the thumb from the other fingers? Currently using the multitouch driver it feels like any finger in the clicking area will be treated as the clicking finger, not just the thumb.

Thanks for this info! You are right, thumb detection is not in the mainline branch, but I do have something cooking. I am assuming now that thumb detection also affect the behavior of multi-finger clicks, so that two fingers on the pad and a thumb in the clicking area is a two-finger click, whereas using a non-thumb to click results in a three-finger click. Correct?

---

### Post by kosumi68 on 2010-04-26
Regarding gestures, are there any strong feelings about pinch-to-zoom? How about rotate? Both of these are fairly easy to implement, but the support in X is not very good. Ctrl +- key emulation could be used to zoom. For rotation; no clue how to map this in X.

---

### Post by kosumi68 on 2010-04-26
> **zeroti said:**
> is there a way to install this on a powerbook G4 with lucid? On OS X, I could use iScroll2 to get multitouch working.

What kernel module is used? If you have no idea, post the output of 'lsmod' here.

---

### Post by zeroti on 2010-04-26
> **kosumi68 said:**
> What kernel module is used? If you have no idea, post the output of 'lsmod' here.

```

sudoman@igo:~$ lsmod
Module                  Size  Used by
binfmt_misc             8530  1 
ppdev                   7877  0 
lp                      9304  0 
parport                39110  2 ppdev,lp
uinput                  8693  2 
ipv6                  299918  10 
radeon                802403  0 
ttm                    62566  1 radeon
drm_kms_helper         31219  1 radeon
drm                   192389  3 radeon,ttm,drm_kms_helper
rfcomm                 43733  8 
sco                    10661  2 
i2c_dev                 6771  0 
pmu_battery             1889  0 
therm_adt746x          10133  0 
apm_emu                 1468  0 
apm_emulation           7311  2 apm_emu
snd_powermac           68187  0 
snd_seq_dummy           1766  0 
snd_seq_oss            36232  0 
snd_seq_midi            6161  0 
snd_aoa_codec_tas      12436  2 
snd_aoa_fabric_layout    10954  2 
bridge                 57998  0 
snd_aoa                17240  2 snd_aoa_codec_tas,snd_aoa_fabric_layout
stp                     2244  1 bridge
snd_rawmidi            24746  1 snd_seq_midi
snd_aoa_i2sbus         20791  1 
bnep                   12779  2 
snd_seq_midi_event      7367  2 snd_seq_oss,snd_seq_midi
arc4                    1345  2 
snd_pcm_oss            47872  0 
ecb                     2495  2 
snd_mixer_oss          19382  1 snd_pcm_oss
l2cap                  37132  16 rfcomm,bnep
snd_seq                61897  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 37678  0 
snd_pcm                87095  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
b43                   188381  0 
snd_seq_device          7524  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  13383  2 
bluetooth              64147  9 rfcomm,sco,bnep,l2cap,btusb
mac80211              243283  1 b43
yenta_socket           25736  1 
snd_timer              24515  2 snd_seq,snd_pcm
cfg80211              152734  2 b43,mac80211
rsrc_nonstatic         11098  1 yenta_socket
evdev                  10257  23 
snd                    70628  17 snd_powermac,snd_seq_oss,snd_aoa_codec_tas,snd_aoa_fabric_layout,snd_aoa,snd_rawmidi,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
pmac_zilog             18110  0 
rtc_generic             1391  0 
serial_core            23813  1 pmac_zilog
snd_aoa_soundbus        4916  2 snd_aoa_fabric_layout,snd_aoa_i2sbus
uninorth_agp            8437  1 
rfkill                 20725  4 bluetooth,cfg80211
agpgart                39895  3 ttm,drm,uninorth_agp
pcmcia_core            40156  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               7534  1 snd
snd_page_alloc          7660  1 snd_pcm
usbhid                 44238  0 
hid                    78460  1 usbhid
ohci1394               35584  0 
ssb                    48664  1 b43
sungem                 32704  0 
ieee1394               97330  1 ohci1394
sungem_phy             12365  1 sungem
mmc_core               69051  1 ssb
windfarm_core          10420  0 

```

---

### Post by kosumi68 on 2010-04-26
Mm, not having looked at PPC at all, the output of "cat /proc/bus/input/devices" and "cat /var/log/Xorg.0.log" would also be helpful, but it seems there is no way to use your machine together with this effort.

Regarding multitouch support for old non-MT trackpads, there is a project doing that: [http://randomtruth.110mb.com/blog/](http://randomtruth.110mb.com/blog/). However, making it work is well beyond the scope of this thread. I suggest you start a new one.

---

### Post by zeroti on 2010-04-26
> **kosumi68 said:**
> Mm, not having looked at PPC at all, the output of "cat /proc/bus/input/devices" and "cat /var/log/Xorg.0.log" would also be helpful, but it seems there is no way to use your machine together with this effort.

Regarding multitouch support for old non-MT trackpads, there is a project doing that: [http://randomtruth.110mb.com/blog/](http://randomtruth.110mb.com/blog/). However, making it work is well beyond the scope of this thread. I suggest you start a new one.


```

sudoman@igo:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0017 Vendor=0001 Product=22c3 Version=0100
N: Name="ADB keyboard"
P: Phys=adb2:2.c3/input
S: Sysfs=/devices/virtual/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 0 0 0 0 0 0 0 0 0 0 feb0ffdf 3cfffff ffffffff fffffffe
B: LED=7

I: Bus=0017 Vendor=0001 Product=771f Version=0100
N: Name="ADB Powerbook buttons"
P: Phys=adb7:7.1f/input
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=100003
B: KEY=7b 0 2 0 e0000 0 0 0

I: Bus=0017 Vendor=0001 Product=3301 Version=0100
N: Name="ADB mouse"
P: Phys=adb3:3.01/input
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0001 Product=0001 Version=0100
N: Name="PMU"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=23
B: KEY=100000 0 0 0
B: SW=1

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd rfkill event5 
B: EV=100003
B: KEY=1ffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/devices/virtual/input/input8
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=7
B: KEY=70700 0 0 0 0 0 0 0 0
B: REL=103

```

```


     April 2010
Su Mo Tu We Th Fr Sa
             1  2  3
 4  5  6  7  8  9 10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30


sudoman@igo:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux igo 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 26 15:01:32 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:16:0) 1002:4e50:1002:4e50 ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xb8000000/134217728, 0xb0000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched fbdev as autoconfigured driver 1
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:10:0
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): TOTO SAYS 00000000b0000000
(II) RADEON(0): MMIO registers at 0x00000000b0000000: size 64KB
(II) RADEON(0): PCI bus 0 card 16 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) RADEON(0): VGAAccess option set to FALSE, VGA module load skipped
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP)" (ChipID = 0x4e50)
(--) RADEON(0): Linear framebuffer at 0x00000000b8000000
(II) RADEON(0): AGP card detected
(WW) RADEON(0): Failed to read PCI ROM!
(II) RADEON(0): Attempting to read un-POSTed bios
(WW) RADEON(0): Failed to read PCI ROM!
(WW) RADEON(0): Unrecognized BIOS signature, BIOS data will not be used
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card15
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card15
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(WW) RADEON(0): Video BIOS not detected, using default clock settings!
(II) RADEON(0): Probed PLL values: xtal: 27.000000 Mhz, sclk: 391.500000 Mhz, mclk: 202.500000 Mhz
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12500 max=35000; xclk=15464
(==) RADEON(0): Detected PowerBook with external DVI.
(II) RADEON(0): If this is not correct, try Option "MacModel" and consider reporting to the
(II) RADEON(0): xorg-driver-ati@lists.x.org mailing list with the contents of /proc/cpuinfo.
(II) RADEON(0): Existing panel PLL dividers will be used.
(WW) RADEON(0): Panel size 1280x854 is derived, this may not be correct.
If not, use PanelSize option to overwrite this setting
(II) RADEON(0): I2C bus "DVO" initialized.
(II) RADEON(0): I2C device "DVO:RADEON DVO Controller" registered at address 0x70.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Port0:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x64
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_DAC1
  DFP2: INTERNAL_DVO1
  DDC reg: 0x60
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x854"x60.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x854
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(**) RADEON(0): Display dimensions: (320, 220) mm
(**) RADEON(0): DPI set to (101, 147)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): Cannot access BIOS or it is not valid.
        If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
        RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit b8000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xbbffb800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 6909
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xbbffb800 0x7fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
(II) RADEON(0): Largest offscreen area available: 1280 x 6901
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xbbffb800 0xbbffb800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 338 x 225
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ADB keyboard (/dev/input/event1)
(**) ADB keyboard: Applying InputClass "evdev keyboard catchall"
(**) ADB keyboard: always reports core events
(**) ADB keyboard: Device: "/dev/input/event1"
(II) ADB keyboard: Found keys
(II) ADB keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "ADB keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ADB Powerbook buttons (/dev/input/event2)
(**) ADB Powerbook buttons: Applying InputClass "evdev keyboard catchall"
(**) ADB Powerbook buttons: always reports core events
(**) ADB Powerbook buttons: Device: "/dev/input/event2"
(II) ADB Powerbook buttons: Found keys
(II) ADB Powerbook buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ADB Powerbook buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ADB mouse (/dev/input/event3)
(**) ADB mouse: Applying InputClass "evdev pointer catchall"
(**) ADB mouse: always reports core events
(**) ADB mouse: Device: "/dev/input/event3"
(II) ADB mouse: Found 3 mouse buttons
(II) ADB mouse: Found relative axes
(II) ADB mouse: Found x and y relative axes
(II) ADB mouse: Configuring as mouse
(**) ADB mouse: YAxisMapping: buttons 4 and 5
(**) ADB mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ADB mouse" (type: MOUSE)
(II) ADB mouse: initialized for relative axes.
(II) config/udev: Adding input device ADB mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PMU (/dev/input/event4)
(**) PMU: Applying InputClass "evdev keyboard catchall"
(**) PMU: always reports core events
(**) PMU: Device: "/dev/input/event4"
(II) PMU: Found keys
(II) PMU: Configuring as keyboard
(II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event5)
(**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event5"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event6)
(**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event6"
(II) Mouseemu virtual mouse: Found 14 mouse buttons
(II) Mouseemu virtual mouse: Found scroll wheel(s)
(II) Mouseemu virtual mouse: Found relative axes
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(II) Mouseemu virtual mouse: initialized for relative axes.
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
Changing OV0_BASE_ADDR from 0xb8000000 to 0xb8400000
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x854"x0.0   79.81  1280 1296 1408 1536  854 855 858 866 -hsync -vsync (52.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c20  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 32  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.350   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.150 blueY: 0.115   whiteX: 0.320 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 79.8 MHz   Image Size:  321 x 214 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1536 h_border: 0
(II) RADEON(0): v_active: 854  v_sync: 855  v_sync_end 858 v_blanking: 866 v_border: 0
(II) RADEON(0):  LTN152W3
(II) RADEON(0):  LTN152W3
(II) RADEON(0): Monitor name: Color LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000610209c01010101
(II) RADEON(0):     050c0103802016780aa7a299594f8c26
(II) RADEON(0):     1d525400000001010101010101010101
(II) RADEON(0):     0101010101012d1f000051560c301070
(II) RADEON(0):     130041d610000018000000fe004c544e
(II) RADEON(0):     31353257330000000a20000000fe004c
(II) RADEON(0):     544e31353257330000000a20000000fc
(II) RADEON(0):     00436f6c6f72204c43440a202020000b
(II) RADEON(0): Panel infos found from DDC detailed: 1280x854
(II) RADEON(0): EDID vendor "APP", prod id 39968
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0

```

---

### Post by kosumi68 on 2010-04-26
Thanks for the info. Yep, the "ADB Mouse" is an old trackpad. Your best shot at getting multitouch working is the perl script by random, mentioned above. Good luck.

---

### Post by Taoye on 2010-04-26
> **kosumi68 said:**
> Regarding gestures, are there any strong feelings about pinch-to-zoom? How about rotate? Both of these are fairly easy to implement, but the support in X is not very good. Ctrl +- key emulation could be used to zoom. For rotation; no clue how to map this in X.

Personally, I rarely used the pinch to zoom... even in OS X it's pretty awkward and hard to accurately zoom, and it doesn't always work, for some reason OS X has a hard time reading the sides of my fingers. 

Rotate is pretty useful on the odd occasion though (mostly rotating photos)... the synaptics' oem gestures suite has got rotating, it must be possible somehow.

---

### Post by alexmurray on 2010-04-26
I'd be keen to use both pinch-to-zoom and rotate. Thanks for your great work on the multitouch stack.

---

### Post by npfthunfan on 2010-04-29
I'm really keen to try this out and do some testing... but... being a total noob I'm gonna need someone to give me step by step instructions as to compiling, etc...

---

### Post by NiñoScript on 2010-04-29
I still can't find the time to make the video I promised :(
I hate the exam periods >.<
I'll help now with an install guide for people like the guy above :) (like I was two months ago)

> **npfthunfan said:**
> […]  I'm gonna need someone to give me step by step instructions as to compiling, etc...

01.- First, add the mactel repository:
```
sudo apt-add-repository ppa:mactel-support/ppa
```

02.- EDIT: The Lucid repository added the bcm5974-dkms package, so this step is not needed, so go to step 03 :)
> I think the Lucid repository doesn't have bcm5974-dkms, so let's add the Karmic repository:
```
echo '
deb http://ppa.launchpad.net/mactel-support/ubuntu karmic main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu jaunty main'\
| sudo tee -a /etc/apt/sources.list
```

03.- Update apt-get to see the new packages in the repositories you just added:
```
sudo apt-get update
```

04.- Now, install some stuff we need:
```
sudo apt-get install bcm5974-dkms git-core xserver-xorg-dev
```

05.- Get the actual driver:
```
cd ~
git clone http://bitmath.org/git/multitouch.git
```

06.- Compile and install it:
```
cd ~/multitouch
sudo make install
```

07.- Tell your computer to use the driver:
```
echo '
Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection' | sudo tee -a /etc/X11/xorg.conf
```

08.- Before reading step 09, be sure you have a mouse connected or at least know how to open a terminal with the keyboard (ctrl+alt+t; alt+F2, then type gnome-terminal; or use gnome-do), just in case the cursor doesn't move. And be sure to read everything and take notes of step 11 just in case.

09.- Reboot or Logout/Login

10.- If it worked, jump to step 13

11.- If the cursor doesn't move, try this:
```
modprobe -r bcm5974
modprobe bcm5974
```

12.- If that didn't help, ask here! I don't know what happened :confused:

13.- Now that it's working: Enjoy! And be sure to come back here and report any bug or misbehaviour :)

---

### Post by kosumi68 on 2010-04-29
Great, NinoScript :-)

All valid packages should be available in lucid within a couple of hours, so from now on, link to the lucid ppa.

---

### Post by npfthunfan on 2010-04-29
Thanks Nino

I got permissions errors with step 2 and step 7... tried opening xorg.conf in gedit but it just opened as read-only

---

### Post by NiñoScript on 2010-04-29
> **npfthunfan said:**
> I got permissions errors with step 2 and step 7...

Ohh, you're right!
It's now fixed :D

> **npfthunfan said:**
> tried opening xorg.conf in gedit but it just opened as read-only

You should've used sudo or gksudo to make gedit have root privilegies
well, you can just copy/paste what I wrote now ;)

---

### Post by npfthunfan on 2010-04-30
Got an error on boot... :S

> **Ubuntu is running in low-graphics mode**
The following error was encountered. You may need to update your configuration to solve this

(EE) Problem parsing the config file
(EE) Error parsing the config file

Guessing there's a syntax error somewhere...

EDIT: Updated to Lucid... works fine...

---

### Post by npfthunfan on 2010-04-30
Now that I've got this working... I realise how much I use tap-to-click :S

---

### Post by NiñoScript on 2010-04-30
> **kosumi68 said:**
> Great, NinoScript :-)

All valid packages should be available in lucid within a couple of hours, so from now on, link to the lucid ppa.

Ok, just checked that it's in Lucid, so I removed the step where I said to add Karmic

---

### Post by kosumi68 on 2010-04-30
> **NiñoScript said:**
> Ok, just checked that it's in Lucid, so I removed the step where I said to add Karmic

Thanks Nino! Regarding the thumb detection, there was some correspondence some days ago, trying to pin down the exact behavior. I will implement a thumb detection according to my understanding as stated in those posts. If you have anything to add, please do :-)

And regarding the video, please do not feel you have to do it on my behalf - I think we will be fine anyways ;-)

Cheers!

---

### Post by NiñoScript on 2010-05-01
> **kosumi68 said:**
> Thanks Nino! Regarding the thumb detection, there was some correspondence some days ago, trying to pin down the exact behavior. I will implement a thumb detection according to my understanding as stated in those posts. If you have anything to add, please do :-)

And regarding the video, please do not feel you have to do it on my behalf - I think we will be fine anyways ;-)

Cheers!

I really wanted to, but I think there's no time right now for me to get a camera&#8230;

I'll do some tests now on MacOSX, BRB! :D

~~~~~~~~

I actually made some videos, I recorded them with Jing, and it turns out that it's a ~100MB swf file&#8230; I cannot upload it to youtube, and ffmpeg just extracts the audio, so I think tomorroy I'll re-record them or find how to upload them to youtube or at least a solutiong on how to compress and where to upload the video

bye bye! cya!

~~~~~~~~

I think it's actually better and faster if I just tell you what I found:

The driver recognizes up to **11 different blobs, with shape, size and position**.

[The side of my right hand, the side of my thumb and my four other fingers.]("http://i42.tinypic.com/2le1b2p.png")
[The same as above, plus my left fingers so you see the eleven blobs maximum.]("http://i40.tinypic.com/wc1wqt.jpg")

1 blob case:
[INDENT]There's a **variable threshold** for the first movement.
It depends on the position of the blob, center < sides < top &#8810; bottom.
It depends on the size of the blob, finger < thumb &#8810; hand. (With the side of my hand it just doesn't move anywhere)[/INDENT]

[Finger]("http://img691.imageshack.us/img691/1046/screenshot19g.png")
[Thumb Side]("http://img59.imageshack.us/img59/3517/screenshot18m.png")
[Hand Side]("http://img59.imageshack.us/img59/1473/screenshot17aa.png")

2 blob case:
[INDENT]If 1 of those blobs is the side of my hand, it behaves as the 1 blob case.
If both blobs are the side of my hands, it doesn't work*.
**If both blobs are normal fingers, it scrolls**, unless if they are put in a vertical line and move just the upper one or I'm pinching/rotating instead of just moving.
If just one of them is a thumb:[INDENT]&#8230; and the thumb starts above 1/3 of the trackpad vertically, and then I put my other finger and move it, it doesn't work*
&#8230; and **thumb starts below that 1/3, the moving finger will move the cursor until the clicking finger is above it**, in which case it won't work*[/INDENT]
If both blobs are thumbs, it sometimes scrolls, but it's mostly undefined behaviour, some cursor jumps and weird stuff[/INDENT]
* doesn't work: it doesn't move the cursor AND it doesn't scroll.

[Thumb just above 1/3 of the trackpad vertically, it doesn't move.]("http://img72.imageshack.us/img72/404/screenshot20.png")
[Normal situation.]("http://img32.imageshack.us/img32/5587/screenshot21a.png")
[Thumb goes above the other finger, it stops working.]("http://img688.imageshack.us/img688/2766/screenshot22v.png")

I'll go on with 3 and 4 blob cases other day :)

One thing to note before I go away, **is that if you have the side of your hand, it won't be counted for moving or scrolling**, so side of my hand + thumb on the low part and 2 fingers moving, will result in scrolling, and side of my and + 1 finger will just move the cursor.

Oh! and, by the way, I'm using mathematic notation here: &#8810; and &#8811; mean **much less than** and **much greater than**, respectively.

---

### Post by adamouser on 2010-05-01
hi ninoscript

ive installed the driver according to your installation guide. everything worked just fine. after the reboot I could not move the mouse using my touchpad. modprobe tells me some permission error. using sudo does not help (but  no errors then...)

i am using a dell adamo with lucid. touchpad hardware should be multitouch capable since multitouch works fine using win7. I thought this driver not only applies for macosx?

id appreciate every helpful hint!

thanks

---

### Post by NiñoScript on 2010-05-02
> **adamouser said:**
> "[&#8230;] I thought this driver not only applies for macosx?"
I don't think I can help you there&#8230;
I've only seen this working on MacBooks, but let's wait for the answer of those cool guys called developers :)

---

### Post by kosumi68 on 2010-05-02
> **NiñoScript said:**
> I really wanted to, but I think there's no time right now for me to get a camera…

I'll do some tests now on MacOSX, BRB! :D

~~~~~~~~


Truly outstanding, Nino! Thanks a bundle for the information, it seems we have movement very well covered. Multi-finger clicks are probably not as frequently used in OSX as in Ubuntu, but it would be great to also know what happens to the multi-finger clicks for the cases you describe.

Cheers!

---

### Post by kosumi68 on 2010-05-02
> **adamouser said:**
> hi ninoscript

ive installed the driver according to your installation guide. everything worked just fine. after the reboot I could not move the mouse using my touchpad. modprobe tells me some permission error. using sudo does not help (but  no errors then...)

i am using a dell adamo with lucid. touchpad hardware should be multitouch capable since multitouch works fine using win7. I thought this driver not only applies for macosx?

id appreciate every helpful hint!

thanks

Great to see this moving outside the mac area! However, there is a big hurdle: the MT capabilities of the kernel driver in use.

There are two distinct uses of the word "driver":

The first is the kernel input driver, which sets up the hardware as an input device. This driver must have the recent kernel multitouch protocol implemented, or it will not work. To find out which driver is in use on your machine, please do "cat /proc/bus/input/devices" and report the output here. (From your report it sounds like you tried to load the macbook-specific bcm5974 kernel driver on your machine, which simply will not work.)

The second is the Multitouch X Driver (multitouch), which is a xorg driver, transforming the input from the input device to gestures in the X window system. This one you probably got loaded successfully.

The symptoms of not having a MT-capable kernel driver but using the multitouch driver is a mouse that can click, but which does not move. Sounds just about right?

---

### Post by adamouser on 2010-05-02
hi kosumi

thanks for your quick reply. you are completely right. 

- tried to use bcm5974: mouse did not move
- x driver successfully loaded (default by lucid i guess)e

here is the output of my devices:
```
dominic@adamo:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 dell-laptop 
B: EV=120013
B: KEY=500f 2902003 8380307c f910f001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 
B: EV=3
B: KEY=8000 0 0 0 0 0 5003 0 2 300000 0 0 0 0

I: Bus=0003 Vendor=413c Product=8157 Version=0111
N: Name="HID 413c:8157"
P: Phys=usb-0000:00:1d.2-2.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2.1/8-2.1:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0003 Vendor=0c45 Product=63e8 Version=8828
N: Name="Integrated_Webcam_1.3M"
P: Phys=usb-0000:00:1d.7-5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0001 Vendor=111d Product=7675 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input12
U: Uniq=
H: Handlers=kbd event11 
B: EV=40001
B: SND=6

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event12 
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
U: Uniq=
H: Handlers=event13 
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
U: Uniq=
H: Handlers=event14 
B: EV=21
B: SW=4
```


what do you suggest? I am willing to help.

---

### Post by kosumi68 on 2010-05-02
Thanks for the data! So there is a synaptics pad in there, good. In order to be sure how it is handled, the output of "lsmod" is also needed. Thanks!

---

### Post by adamouser on 2010-05-03
here we go. thanks for your help by the way

```
dominic@adamo:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      51914  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
nls_utf8                1069  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 36110  0 
iwlagn                105566  0 
i915                  282354  3 
dell_wmi                1793  0 
hid                    67032  1 usbhid
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
iwlcore               105922  1 iwlagn
led_class               2864  1 iwlcore
zaurus                  2404  0 
uvcvideo               56990  0 
drm                   162471  4 i915,drm_kms_helper
cdc_ether               3541  1 zaurus
mac80211              204922  2 iwlagn,iwlcore
dell_laptop             6856  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbnet                 14943  2 zaurus,cdc_ether
mii                     4381  1 usbnet
cdc_wdm                 8218  0 
cdc_acm                13694  0 
dcdbas                  5422  1 dell_laptop
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126485  3 iwlagn,iwlcore,mac80211
intel_agp              24177  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  1 lp
ahci                   32008  4 
tg3                   109292  0 

```

and here is the content of /var/log/Xorg.0.log if this provides valuable information:
```
...
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
...

```

---

### Post by NiñoScript on 2010-05-04
I saw this software with really nice gestures, so I thought I should post the video here as inspirational material ;)

[INDENT][SIZE="4"][Jitouch 2]("http://www.youtube.com/watch?v=kIgcFqKtfek")[/SIZE][/INDENT]

---

### Post by joskapista on 2010-05-06
Hi,
Thanks for your work, I have a macbook 5,1 (late 2008 ) and Lucid, and the new driver that [NiñoScript]("http://ubuntuforums.org/member.php?u=70731") posted, works fine (one finger click and the other moves something, and two finger scroll). I have only one problem: tap and click doesn't work (the double click with the normal click is a bit difficult) or I don't know, how can I enable it. The other thing is that the cursor is a bit fast and if I make it slower under the global mouse preferences the mouse became too slow. You made a great job, I am really happy because touchpad was useless with the old driver.

---

### Post by boarder4021 on 2010-05-06
This literally saved my life - thank you so much for your work! Just a couple of tidbits: 

[LIST]
[*]CTRL-click doesn't work correctly as right click
[*]The trackpad doesn't ignore input when typing (even if the option is clicked)
[*]Any chance for multitouch support (like three-finger swipe)?
[/LIST]

Again - thank you so much for doing this and providing it to the community. Maybe someone could update the OP with the new instructions..?

---

### Post by dennda on 2010-05-07
How can I adjust parameters if there are any?

---

### Post by NerdsMcGee on 2010-05-08
> **boarder4021 said:**
> This literally saved my life - thank you so much for your work! Just a couple of tidbits: 

[LIST]
[*]CTRL-click doesn't work correctly as right click
[*]The trackpad doesn't ignore input when typing (even if the option is clicked)
[*]Any chance for multitouch support (like three-finger swipe)?
[/LIST]

Again - thank you so much for doing this and providing it to the community. Maybe someone could update the OP with the new instructions..?

Just wanted to add my 2 cents. Can we get three finger swipe to be left/right instead of up down for back/forward in say firefox?

Also, does anyone else seem to be mis-clicking a lot with a single finger move / click?

---

### Post by kosumi68 on 2010-05-08
While on the wishlist page, I wish there were more people sending patches and providing information ;-)

I plan to release alpha3 within a week from now, and it will include thumb detection and better support for the integrated trackpad. After that, beta1 will be out 15JUN2010, regardless of what features it includes.

Happy hacking!

---

### Post by kosumi68 on 2010-05-08
@adamouser: thanks for the information. Unfortunately, the new synaptics trackpads uses a protocol not (yet) publicly available. Not surprising, given their current multitouch selling drive. There was a discussion at the linux-input kernel mailing list about it, and we are all basically awaiting a reverse-engineering attempt.

---

### Post by teo_rossi on 2010-05-09
I get an "Unsupported ABI_XINPUT_VERSION" error when compiling multitouch.c on Ubuntu Lucid, with Synaptics touchpad.

---

### Post by adamouser on 2010-05-09
@kosumi68
Thanks for this information. Where can I follow the mentioned discussion. I'd like to stay updated on this.

---

### Post by kosumi68 on 2010-05-09
> **adamouser said:**
> @kosumi68
Thanks for this information. Where can I follow the mentioned discussion. I'd like to stay updated on this.

In this case, it is actually best to google for it, since information might appear in any of several forums.

---

### Post by kosumi68 on 2010-05-09
> **teo_rossi said:**
> I get an "Unsupported ABI_XINPUT_VERSION" error when compiling multitouch.c on Ubuntu Lucid, with Synaptics touchpad.

please provide the output of "make distclean; make".

---

### Post by alexmurray on 2010-05-10
@kosumi - Just noticed that both 2 and 3-finger click on my integrated trackpad (MBP5,1) doesn't allow dragging - moving fingers whilst clicked down with either 2 or 3 fingers doesn't work... any chance of fixing this or where should I look in the code to try and enable this myself?

EDIT - Ahh just realised you can do this by clicking down with 3 fingers, then removing 2 of the whilst still keeping one down. (Will leave this here for others in case). Excellent.

---

### Post by amd-64 on 2010-05-10
NiñoScript


I still cannot get this to work. Can you post your entire xorg.conf file. Thanks

---

### Post by joskapista on 2010-05-10
I made a few tests, maybe you can find it helpful (Macbook 5,1, Lucid):
 
[LIST]
[*][FONT=TimesNewRomanPSMT, serif]I 	came to realize that why is so difficult to make a double click: I 	have to make the second click exactly where the first click was. If 	this second click is not precise, that could cause that you move 	something involuntarily. Under OSX when I click, the driver stops 	the cursor for a very short time, and I have enough time to click 	into the same pixel on the touchpad.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]The 	movement of the cursor is a bit unusual, because I have the fancy 	that the horizontal  speed is higher than the vertical.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]The 	touchpad doesn't ignore input when I am typing.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]Tap 	to click doesn't work.[/FONT]
[/LIST]
 [FONT=TimesNewRomanPSMT, serif]I hope I could help. [/FONT] 
 [FONT=TimesNewRomanPSMT, serif][/FONT]

---

### Post by kwiksand on 2010-05-11
> **teo_rossi said:**
> I get an "Unsupported ABI_XINPUT_VERSION" error when compiling multitouch.c on Ubuntu Lucid, with Synaptics touchpad.

Probably not the best way of fixing it, but I changed the minimum version number for ABI_XINPUT_VERSION in multitouch.h and everything is working fine here! (Lucid)

---

### Post by kosumi68 on 2010-05-13
The alpha3 is coming up, scheduled for tomorrow. I updated the "next" branch in the git tree with the latest changes. If you experience anything odd, please holler. Shortlog since last master update appended.

Enjoy!


Henrik Rydberg (12):
      Add a README
      Simplify bit bookkeeping
      janitor: Move min/max and dist functions up to common.h
      Introduce MTFinger structure
      Add convenience methods for distance to capability...
      janitor: Split gesture code into memory refresh and parse
      Refactor parsor memory usage
      Add resting thumb detection to MTFinger
      Disable motion with resting thumbs
      Hold movement while clicking
      Add scale gesture
      Add rotation gesture

---

### Post by alexmurray on 2010-05-14
Sounds like some great progress will test tonight. Thanks for all your hard work Henrik, muchly appreciated.

---

### Post by kosumi68 on 2010-05-15
Multitouch X Driver v1.0-alpha3 released

This release contains a lot of improvements over alpha2. We have bug fixes that have been in the tree for a while, we have better support for integrated trackpads, we have thumb detection, and we have the first couple of "real" gestures. I mapped the scaling gesture to the zooming feature in compiz, you will probably find other interesting ways. :-)

Enjoy!

---

Shortlog:
      janitor: Use more common row/column names
      Reset accumulated movement at finger configuration change
      Unify detection of finger configuration changes
      Reset scroll state on finger configuration change
      Correctly report zero fingers
      Do not reuse tracking ids after a no-touch event
      Make all movement computations work on pointing subset
      Filter non-zero finger width events
      Hold MT data during pure button events
      Only emit multi-finger button events for real button events
      Increase touch/width signal-to-noise ratio
      Add a README
      Simplify bit bookkeeping
      janitor: Move min/max and dist functions up to common.h
      Introduce MTFinger structure
      Add convenience methods for distance to capability...
      janitor: Split gesture code into memory refresh and parse
      Refactor parsor memory usage
      Add resting thumb detection to MTFinger
      Disable motion with resting thumbs
      Hold movement while clicking
      Add scale gesture
      Add rotation gesture

---

### Post by kosumi68 on 2010-05-15
> **kwiksand said:**
> Probably not the best way of fixing it, but I changed the minimum version number for ABI_XINPUT_VERSION in multitouch.h and everything is working fine here! (Lucid)

Under what circumstances is this needed? A small patch perhaps? :-)

---

### Post by kosumi68 on 2010-05-16
> **joskapista said:**
> I made a few tests, maybe you can find it helpful (Macbook 5,1, Lucid):
 
[LIST]
[*][FONT=TimesNewRomanPSMT, serif]I 	came to realize that why is so difficult to make a double click: I 	have to make the second click exactly where the first click was. If 	this second click is not precise, that could cause that you move 	something involuntarily. Under OSX when I click, the driver stops 	the cursor for a very short time, and I have enough time to click 	into the same pixel on the touchpad.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]The 	movement of the cursor is a bit unusual, because I have the fancy 	that the horizontal  speed is higher than the vertical.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]The 	touchpad doesn't ignore input when I am typing.[/FONT]
[*][FONT=TimesNewRomanPSMT, serif]Tap 	to click doesn't work.[/FONT]
[/LIST]
 [FONT=TimesNewRomanPSMT, serif]I hope I could help. [/FONT] 
 [FONT=TimesNewRomanPSMT, serif][/FONT]

Thank you for testing. Clicking might work a lot better in alpha3, the movement is held while clicking, there is a parameter in gestures.c. The trackpad movement is following the screen size very closely in my experience. I have turned acceleration down to a minimum in System/Preferences/Mouse, that did it for me. Perhaps that makes a difference for you as well? The trackpad still is not disabled with keyboard presses, but on the other hand the thumb detection makes it behave pretty well. It would be great to hear what you think about it. Tap to click has not been implemented. :-)

Cheers!

---

### Post by teo_rossi on 2010-05-16
> **kosumi68 said:**
> please provide the output of "make distclean; make".

```
~/multitouch$ sudo make distclean; make
rm -rf bin obj
rm -rf debian/*.log debian/files
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c match/match.c -o obj/match/match.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/capabilities.c -o obj/src/capabilities.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/iobuffer.c -o obj/src/iobuffer.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/hwdata.c -o obj/src/hwdata.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/hwstate.c -o obj/src/hwstate.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/mtstate.c -o obj/src/mtstate.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/memory.c -o obj/src/memory.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/mtouch.c -o obj/src/mtouch.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/gestures.c -o obj/src/gestures.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/multitouch.c -o obj/src/multitouch.o
src/multitouch.c:137:2: error: #error "Unsupported ABI_XINPUT_VERSION"
make: *** [obj/src/multitouch.o] Errore 1

```

---

### Post by kosumi68 on 2010-05-16
> **teo_rossi said:**
> ```
~/multitouch$ sudo make distclean; make
rm -rf bin obj
rm -rf debian/*.log debian/files
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c match/match.c -o obj/match/match.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/capabilities.c -o obj/src/capabilities.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/iobuffer.c -o obj/src/iobuffer.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/hwdata.c -o obj/src/hwdata.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/hwstate.c -o obj/src/hwstate.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/mtstate.c -o obj/src/mtstate.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/memory.c -o obj/src/memory.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/mtouch.c -o obj/src/mtouch.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/gestures.c -o obj/src/gestures.o
gcc -I. -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/multitouch.c -o obj/src/multitouch.o
src/multitouch.c:137:2: error: #error "Unsupported ABI_XINPUT_VERSION"
make: *** [obj/src/multitouch.o] Errore 1

```

Thanks for the information. Odd, I do not see this on lucid. You have xserver-xorg-dev installed? What happens if you modify line 24 of multitouch.c to read "GET_ABI_MAJOR(ABI_XINPUT_VERSION) >= 0"?

---

### Post by teo_rossi on 2010-05-16
I tried to change line 24 but the same error is thrown. Instead, changing the 'GET_ABI_MAJOR(ABI_XINPUT_VERSION) == 7' with a '>=' makes the code compile without any errors. I still have to test the driver anyway.

---

### Post by kosumi68 on 2010-05-16
Thanks for the info! I have updated the master tree with a patch. A confirmation that it works would be good. Cheers!

---

### Post by teo_rossi on 2010-05-17
With the patch the code compiles fine, but XServer does not start after adding the InputClass section. I see the screen backlight turning on and off but no image is shown. I had to revert to the previous xorg.conf file to make it work again.

xorg.conf and log are attached.

---

### Post by kosumi68 on 2010-05-17
> **teo_rossi said:**
> With the patch the code compiles fine, but XServer does not start after adding the InputClass section. I see the screen backlight turning on and off but no image is shown. I had to revert to the previous xorg.conf file to make it work again.

xorg.conf and log are attached.

Hmm, your setup seems to be a Vaio with a synaptics trackpad, with two problems: 1) the new synaptics pads do not have MT event support in the kernel (yet), and 2) the synaptics X driver is loaded, so the multitouch X driver cannot grab the device. The second problem is solvable by removing the synaptics driver in the configuration, but the first problem does not currently have a solution. You will get as far as clicking the buttons, but moving the cursor will not work.

Regarding the xinput ABI, it seems you are running version 9, I suppose you have extra multitouch ubuntu packages loaded. Those are not needed here, and presumably needs some additional tweaking in the driver code. Will investigate.

---

### Post by teo_rossi on 2010-05-17
Yes I have a brand new VAIO CW2C5E, which has a bunch of problems with Ubuntu. Anyway, thank you very much for your fast replies. I was interested in this project because I couldn't use the built in multitouch features due to the fact that ubuntu doesn't recognize more than one finger. 

Please keep me up to date and tell me if new tests are needed. I will be glad to help.

---

### Post by joskapista on 2010-05-17
> **kosumi68 said:**
> Thank you for testing. Clicking might work a lot better in alpha3, the movement is held while clicking, there is a parameter in gestures.c. The trackpad movement is following the screen size very closely in my experience. I have turned acceleration down to a minimum in System/Preferences/Mouse, that did it for me. Perhaps that makes a difference for you as well? The trackpad still is not disabled with keyboard presses, but on the other hand the thumb detection makes it behave pretty well. It would be great to hear what you think about it. Tap to click has not been implemented. :-)

Cheers!

 I installed the alpha3. The setup that you suggest me was a good solution, the movement of the cursor is much more better. The thumb detection and the “movement held while click” works fine. I only miss the tap to click, I hope you will have time to implement it to the next version. Thanks for your work!

---

### Post by KilianValkhof on 2010-05-19
I successfully installed this on a macbook 5,5 but I would like to make a feature request:

Make three finger swipe left be back and three finger swipe right be forward, and make up/down 'go to top of page' and 'go to bottom of page'. This is the way it's done on a macbook, and it makes more sense: the page scrolls horizontally, so up/down should do things to the page, whereas the back/forward buttons point to the left and right, so moving your fingers in that direction would make 'sense', too. :)

Also, how can I test the rotating and zooming gestures?

---

### Post by cole.mickens on 2010-05-25
> **KilianValkhof said:**
> I successfully installed this on a macbook 5,5 but I would like to make a feature request:

Make three finger swipe left be back and three finger swipe right be forward, and make up/down 'go to top of page' and 'go to bottom of page'. This is the way it's done on a macbook, and it makes more sense: the page scrolls horizontally, so up/down should do things to the page, whereas the back/forward buttons point to the left and right, so moving your fingers in that direction would make 'sense', too. :)

Also, how can I test the rotating and zooming gestures?

I would love to echo the sentiments of this post. I can't get anything to happen when I pinch or rotate. Also mapping 3-up to back and 3-down to forward seems much less intuitive than 3-left being back and 3-right being forward.

Thank you so much for this driver. It's a godsend.

Also, do I need to do something to disable bcm5974? It still shows up when I do cat /proc/bus/input/devices.

---

### Post by kosumi68 on 2010-05-25
Thank you for your suggestions. Foremost, I interpret them as "there should be a way to configure the button mapping". Personally, I use three-finger left/right swipe to switch workspace in compiz, and like that a lot.

To switch swipe left/right up/down behavior, switch the button numbers (8, 9) on line 254 of src/multitouch.c with the numbers (10, 11) on line 258.

Testing gestures is mostly about finding something one would like to map to a gesture button. I have mapped buttons 12 and 13 to the "Enhanced Zoom Desktop" in compiz, that gives me a useful zooming function. One needs to use the Edit button in compizconfig in order to set buttons higher than 9.

Hope that helps.

---

### Post by cole.mickens on 2010-05-25
> **kosumi68 said:**
> Thank you for your suggestions. Foremost, I interpret them as "there should be a way to configure the button mapping". Personally, I use three-finger left/right swipe to switch workspace in compiz, and like that a lot.

To switch swipe left/right up/down behavior, switch the button numbers (8, 9) on line 254 of src/multitouch.c with the numbers (10, 11) on line 258.

Testing gestures is mostly about finding something one would like to map to a gesture button. I have mapped buttons 12 and 13 to the "Enhanced Zoom Desktop" in compiz, that gives me a useful zooming function. One needs to use the Edit button in compizconfig in order to set buttons higher than 9.

Hope that helps.

When I try to assign Button12 and Button13, it remarks the mouse binding as "Disabled". I did this on the move wall left, move wall right and then tried it out. Nothing happened (though see my thing about bcm5974 above, it still shows up in my proc/bus/input/devices, I don't know if that can cause a problem). Also, it sounds like a configuration utility would be nice. Can the driver be altered at runtime or would it be a pre-compilation configuration? I suppose it could still be made into a nice little tool. I might be able to help out with that if you'd like some additional man power.

---

### Post by kosumi68 on 2010-05-25
> **colemickens said:**
> When I try to assign Button12 and Button13, it remarks the mouse binding as "Disabled". I did this on the move wall left, move wall right and then tried it out. Nothing happened (though see my thing about bcm5974 above, it still shows up in my proc/bus/input/devices, I don't know if that can cause a problem). Also, it sounds like a configuration utility would be nice. Can the driver be altered at runtime or would it be a pre-compilation configuration? I suppose it could still be made into a nice little tool. I might be able to help out with that if you'd like some additional man power.

The bcm5974 is the kernel driver that makes MT possible in the first place, so you do not want to get rid of that. :-)

Help is highly appreciated. It probably makes sense to use the xinput property mechanism, so the configuration tool could be written in any or all languages, independently from this driver.

Thanks!

---

### Post by cole.mickens on 2010-05-25
> **kosumi68 said:**
> The bcm5974 is the kernel driver that makes MT possible in the first place, so you do not want to get rid of that. :-)

Help is highly appreciated. It probably makes sense to use the xinput property mechanism, so the configuration tool could be written in any or all languages, independently from this driver.

Thanks!

Any tips on Compiz? As soon as I set anything to Button12, it goes back to "Disabled" and forgets what I typed in. It's as if it's intentionally disregarding my setting because it's trying to verify it.

Actually, no matter what I type in the free form text, it seems to disregard it.

Well, that looks like a bug in compiz. Either way, it seems to be mapping the swipes to the back/forward button which seems problematic since customizng my trackpad makes my external mouse's button useless. Either way, still a huge leap in usability.

I can actually have compiz bind the finger swipes to some x tool I have that lets me execute arbitrary key commands. So I can map it to be the Alt+Left and Alt+Right.

It seems that 12/13/14/15 do not work for me. Rotating, pinching does not trigger the event properly. At least not when I bind it in Compiz. It works with the three finger swipes perfectly.

---

### Post by bobbytables on 2010-06-03
hi all!

i updated the first posting to my best knowledge. i myself run Gentoo, so i don't know if i got it completely right for Ubuntu.

i read through most of the thread but not everything, so:
please let me know about errors or things still missing.

---

### Post by oscargodson on 2010-06-08
This is great, and it FINALLY worked when i found this thread, but one issue... where did my tap to click go! :(

I didnt even know i used it that much! How can I add that back?

---

### Post by oscargodson on 2010-06-10
So, a few things... maybe someone knows how to do any of these?


[LIST]
[*]Right clicking...? sometimes you have to right click and i have no idea how right now...
[*]Tap to click? Someone suggested synaptics install for that pref pane... then someone said NOT to do that... anyone else?
[*]Two finger taps? Like Macs?
[/LIST]
Other than those things, its working great, but the tap to click and right click blows...

---

### Post by NiñoScript on 2010-06-10
I haven't been active for a while, too busy with exams, homework, etc&#8230; :(

> **oscargodson said:**
> [LIST][*]Right clicking...? sometimes you have to right click and i have no idea how right now...[/LIST]

For right clicking there are two ways:
[LIST]
[*]Put two fingers on your trackpad and click with both.
[*]Put two fingers on your trackpad and click with your thumb on the lower section.
[/LIST]
I hope that helps :)

---

### Post by JohnAtilano on 2010-06-12
I installed this on my MacBook Pro 5,1 running Lucid.  I'd like to uninstall and revert back to the default driver and Trackpad configuration utility.  How do I accomplish this?

Thanks!

---

### Post by NiñoScript on 2010-06-12
> **JohnAtilano said:**
> I installed this on my MacBook Pro 5,1 running Lucid.  I'd like to uninstall and revert back to the default driver and Trackpad configuration utility.  How do I accomplish this?

Thanks!
Try removing what you added to /etc/X11/xorg.conf and restart. I'm not completely sure, but I think that's it.

---

### Post by Wbdsgnr on 2010-06-16
Hey guys! 

Any news on the first beta? Was supposed to be released yesterday ;) Or is it already on the git? Thanks!

---

### Post by kosumi68 on 2010-06-16
Multitouch X Driver v1.0-beta1 Released

One day late, but here it is. The feature some of you have been waiting for is there; tapping. Tap-to-click and tap-and-hold to drag are included, turned on by default for touch screens without a left button. To use it also for trackpads, flip the switch in memory.c.

The bulk of the changes, however, is not features but a refactoring to support the coming addition to the MT protocol, the event slots. Parsing the kernel events is now fairly well abstracted into a conversion layer, which should work for all kernel drivers out there.

Apart from packaging and a parameter interface, which seems to have been picked up by others in this thread, the driver is now a fairly complete MT replacement for synaptics. Therefore, the next release will be the first release candidate, scheduled for 20JUL2010.

Enjoy!

---

Henrik Rydberg (15):
      Allow ABI_XINPUT versions greater than 7
      refactor: Move files
      refactor: Generate code for ABS_MT mapping
      refactor: Simplify capabilities
      refactor: Use the bitmask_t type
      refactor: Introduce mtdev
      refactor: Replace hwdata by mtdev
      janitor: Simplify gesture tracing
      janitor: Simplify gesture handling
      Control grabbing by parameter
      Increase event buffer size
      Increase stability against thumb and edge touches
      Correct mtdev API names
      Add tapping logic
      Multitouch 1.0-beta1

---

### Post by Maletor on 2010-06-16
How can we get this to replace the default synaptics package in the Lucid install. As I understand it, Lucid reads hardware config during the install (and determines if it is a MacBook) so this has go to be possible.

---

### Post by erasme on 2010-06-17
hi, I've got one issue when i try to get the files from the git repos, my question could be stupid and I don't want to bother you but I could'nt find any solution at the moment. 
when trying this:

> git clone [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)

i get this: 

> Initialized empty Git repository in /home/quentin/multitouch/.git/
error: Failed connect to bitmath.org:80; No such file or directory (curl_result = 7, http_code = 0, sha1 = e1e27bf0a55f3cd7ac5ed808cf711617c2fbb2c4)
error: Unable to find 9e22c50cd9f6c8a618005d053124640bf9172a32 under [http://bitmath.org/git/multitouch.git](http://bitmath.org/git/multitouch.git)
Cannot obtain needed tree 9e22c50cd9f6c8a618005d053124640bf9172a32
while processing commit 523d193b089111849873d9de0ec1bf29f4176fbc.
error: Fetch failed.

hope you can help me, and one more time, sorry if the answer is obvious.

---

### Post by teo_rossi on 2010-06-17
> **kosumi68 said:**
> Hmm, your setup seems to be a Vaio with a synaptics trackpad, with two problems: 1) the new synaptics pads do not have MT event support in the kernel (yet), and 2) the synaptics X driver is loaded, so the multitouch X driver cannot grab the device. The second problem is solvable by removing the synaptics driver in the configuration, but the first problem does not currently have a solution. You will get as far as clicking the buttons, but moving the cursor will not work.

Regarding the xinput ABI, it seems you are running version 9, I suppose you have extra multitouch ubuntu packages loaded. Those are not needed here, and presumably needs some additional tweaking in the driver code. Will investigate.

Any news on the support for my trackpad? I really miss the multitouch support in linux

EDIT: I get the following error when compiling with make:

```

In file included from include/mtdev-caps.h:27,
                 from mtdev/caps.c:22:
include/abs2mt.h:19: error: &#8216;MT_ABS_SIZE&#8217; undeclared here (not in a function)
make: *** [obj/mtdev/caps.o] Error 1


```

---

### Post by kosumi68 on 2010-06-17
> **teo_rossi said:**
> Any news on the support for my trackpad? I really miss the multitouch support in linux

EDIT: I get the following error when compiling with make:

```

In file included from include/mtdev-caps.h:27,
                 from mtdev/caps.c:22:
include/abs2mt.h:19: error: ‘MT_ABS_SIZE’ undeclared here (not in a function)
make: *** [obj/mtdev/caps.o] Error 1


```

Regarding your touchpad, I suggest you start a new thread about it, posting details about your machine, model, dmesg output, /proc/bus/input/devices output, /var/log/Xorg.0.log, lsmod output, and whatever else you can think of.

For the compile error, there was a mistake in include/common.h. Fixed and pushed, so it should work now. Thanks.

---

### Post by NiñoScript on 2010-06-17
How do I disable the tap-to-click feature now?

---

### Post by kosumi68 on 2010-06-18
> **NiñoScript said:**
> How do I disable the tap-to-click feature now?

If you are referring to the latest bug fix, it means one now toggles the use of tapping in memory.c. I updated the release statement as well.

Any reflections on the tapping functionality?

---

### Post by joskapista on 2010-06-18
I have problems with the tapping. If I would like to make a single click, I have to tap two times, and if I would like to make a double click, I have to tap 3, or often 4 times. The right click with two finger tap doesn't work.

---

### Post by kosumi68 on 2010-06-18
> **joskapista said:**
> I have problems with the tapping. If I would like to make a single click, I have to tap two times, and if I would like to make a double click, I have to tap 3, or often 4 times. The right click with two finger tap doesn't work.

It should definitely work to tap once to click, but the settings might be too tight, causing a lot of failures. There are a number of parameters to try and tweak in memory.c. You might want to try increasing the TAP_XMOVE and TAP_YMOVE, and/or modify the timings TAP_SETTLE_MS and TAP_GAP_MS.

---

### Post by moore.bryan on 2010-06-18
I've read through entire thread twice now and don't think I saw the answer... if it's there and I missed it, mea culpa.

I'm running Lucid on an Asus Eee PC 1005HA (with a multitouch touchpad). 

Lucid doesn't use xorg.conf any more, so I'm not sure where to get this going, and my lsmod doesn't list any synaptics items being loaded.

Help? Thanks, in-advance...

---

### Post by jonas_t on 2010-06-19
hm, newest version (and the one before) doesn't work on my mb 6,2. it compiles fine, install also does not report any errors. however, after adding the mt-driver to the xorg.conf and rebooting, the touchpad does not work - is dead. i had to disable the mt-driver in order to get the touchpad working again.

i'll attach the Xorg.0.log that from that session. X says that it loads the driver

[QUOTE=Xorg.0.log]
(**) bcm5974: Applying InputClass "touchpad"
(II) LoadModule: "multitouch"
(II) Loading /usr/lib/xorg/modules/input/multitouch.so
(II) Module multitouch: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
[/QUOTE]but later on also says

[QUOTE=Xorg.0.log]
(EE) multitouch: cannot configure device
(EE) Couldn't init device "bcm5974"
(II) UnloadModule: "multitouch"
[/QUOTE]

<edit>
kernel log at least found a device named bcm5974
[quote=dmesg]
[   19.552209] input: bcm5974 as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input9
[   19.552291] usbcore: registered new interface driver bcm5974
[/quote]</edit>


let me know if i can be of any other help by supplying other logs/details.

great work anyway!

---

### Post by kosumi68 on 2010-06-19
Thanks for the thorough test log. There has been no logic changes in the driver for a long time, so there is a possibility that something else changed. With all udev changes during the lucid development, it would not be surprising.

Your Xorg log shows the server is trying to attach the bcm5974 mouse device, fails to find the right protocol, exits and erroneously removes the driver, which is already in use by the correct event device. Sounds like a xserver bug. As a result, nothing works for you.

The bcm5974 appears in the input system as both a mouse device and an event device. This is very common, since the mousedev kernel module picks up a lot of devices. The udev rules should really filter out the mouse device if there is a corresponding event device, so this sounds like an udev bug.

To make it work, it might be possible to rewrite some udev rule, but I have not looked very closely at it.

---

### Post by jonas_t on 2010-06-19
that's somehow bad news, as i though to myself that the error is sitting in front of the linux box. :)

anyway - i'll be happy to test things (e.g., the udev thingy) to get the driver working. the default driver really sucks. ;)

---

### Post by alexmurray on 2010-06-19
You need to make sure you are running the bcm5974 driver from the mactel ppa also if you haven't already done this.

---

### Post by jonas_t on 2010-06-20
apparently, i haven't installed them yet as the ubuntu help page on the mbpro says that there is already a driver. i added the mactel repository for some other dependencies (as the wireless driver), but have not yet installed any touchpad driver manually.

 to make sure before proceeding: you are talking about the package bcm5974-dkms, right?

---

### Post by joskapista on 2010-06-20
I tried to setup the parameters that you wrote [(kosumi68]("http://ubuntuforums.org/member.php?u=592679")), but nothing changed. Tapping is still bad, I tried to tapping faster/slower harder/softer but nothing happened. 1 click is two tap, and a double click is  4 tap. Right click with tapping is impossible. Thanks

---

### Post by kosumi68 on 2010-06-20
> **joskapista said:**
> I tried to setup the parameters that you wrote [(kosumi68]("http://ubuntuforums.org/member.php?u=592679")), but nothing changed. Tapping is still bad, I tried to tapping faster/slower harder/softer but nothing happened. 1 click is two tap, and a double click is  4 tap. Right click with tapping is impossible. Thanks

Ok, not what I get here, but hey. :-)

If you feel like debugging, running the command

```

sudo ./bin/src/test /dev/input/eventX

```

will help. You need to know the event number currently assigned to bcm5974:

```

grep bcm5974 /proc/bus/input/devices -A4 | grep H:

```

and you need to have your driver set to non-grabbing (recompile, make, make install, log out, log in):

```

diff --git a/src/mtouch.c b/src/mtouch.c
index 14c0fd9..6341b56 100644
--- a/src/mtouch.c
+++ b/src/mtouch.c
@@ -21,7 +21,7 @@
 
 #include "mtouch.h"
 
-static const int use_grab = 1;
+static const int use_grab = 0;
 
 int configure_mtouch(struct MTouch *mt, int fd)
 {

```

That should make it possible to see exactly how the gestures are interpreted, and why there would be a double event happening.

---

### Post by alexmurray on 2010-06-20
> **jonas_t said:**
> you are talking about the package bcm5974-dkms, right?
Yes - the multitouch X driver requires this newer version of the bcm5974 kernel module since the default one shipped with Lucid doesn't contain all the required low-level multitouch event code. So you'll have no luck running multitouch without this.

---

### Post by Wbdsgnr on 2010-06-21
> **kosumi68 said:**
> Ok, not what I get here, but hey. :-)

If you feel like debugging, running the command



So I did feel like it ;) I'm having exactly the same problem, concerning double-tap to click. When running the test program, a single tap wouldn't output anything (besides motion). only when double tapping i'd get these lines:

> 
button bit: 0 1
button bit: 0 0
motion: 0 -3
button bit: 0 1
button bit: 0 0
button bit: 0 0
motion: -4 -3
motion: -4 -3
button bit: 0 1
button bit: 0 0
motion: 0 6
motion: 6 0
motion: 5 -3
button bit: 0 1
button bit: 0 0
button bit: 0 0
motion: 0 -3
button bit: 0 1
button bit: 0 0

this would have resulted in 5 clicks.
---------

I've been digging through the code, to see if I could help create a patch or something, but I need some info. I'm an embedded systems developer myself, meaning i'm used to low level stuff.. hardware interrupts. I'm not familiar with the whole event and function calls and API from this mouse driver. Is there anywhere I can find some information about this? As in.. what function is called when. And besides that, i'd need to understand how you built your driver. What files contain what functions and what function is doing what.. you lack a certain degree of commentaries haha. Besides that, i'm grateful that you're taking the effort of development!

---

### Post by kosumi68 on 2010-06-21
> **Wbdsgnr said:**
> 
I can find some information about this? As in.. what function is called when. And besides that, i'd need to understand how you built your driver. What files contain what functions and what function is doing what.. you lack a certain degree of commentaries haha. Besides that, i'm grateful that you're taking the effort of development!

Look at the function read_input() in driver/multitouch.c. It is the single point of entry of input events, and following the code from there should give you a picture of how it works.

Funny then that ohloh considers the project to be well-commented ;-) Reading the git log might help.

The driver was developed to aid the development of MT drivers and to support new hardware. Any help is appreciated. That would make me grateful, too. :-)

---

### Post by kosumi68 on 2010-06-21
... you are running the current git head, 71168e1fb, right?

EDIT: ok, I realize now that some of the code in the beta1 is old already, and the problem might already be fixed in the upcoming mtdev library. Will return shortly with a bugfix.

---

### Post by Wbdsgnr on 2010-06-21
Wonderful! If that's the only entry, that would make things easier :) Yeah, no offence meant as for as the comments in the code! I see you did comment on structs and stuff in the includes. And there's enough comments in the functions themselves, but I was pointing to a little function description above the functions. But, now I know the point of entry, the function names should become pretty self-explanatory! :)

---
I now see you did do that for important functions ;) I take back my words; you've commented quite well :P

---

### Post by kosumi68 on 2010-06-21
> **Wbdsgnr said:**
> Wonderful! If that's the only entry, that would make things easier :) Yeah, no offence meant as for as the comments in the code! I see you did comment on structs and stuff in the includes. And there's enough comments in the functions themselves, but I was pointing to a little function description above the functions. But, now I know the point of entry, the function names should become pretty self-explanatory! :)

---
I now see you did do that for important functions ;) I take back my words; you've commented quite well :P

Well, let's not get carried away. :-P

I pushed a patch to the repo, I am very interested to hear if it makes any difference.

Cheers!

---

### Post by Wbdsgnr on 2010-06-21
Haha. Hmm.. sorry to inform you, but now no tap will trigger an event. Single, double or triple.. nothing happens!

---

### Post by kosumi68 on 2010-06-21
> **Wbdsgnr said:**
> Haha. Hmm.. sorry to inform you, but now no tap will trigger an event. Single, double or triple.. nothing happens!

Good! then just change the variable use_tapping in memory.c to one. :-)

---

### Post by Wbdsgnr on 2010-06-21
Haha, smart ;) Well, you fixed it!! Thanks a lot :) it'll need some minor tweaks in the timing settings, but nothing major!

---

### Post by kosumi68 on 2010-06-24
There is a new package on the block: mtdev - Multitouch Protocol Translation Library. More information and git source can be grabbed from here: [http://bitmath.org/code/mtdev/](http://bitmath.org/code/mtdev/)

The mtdev package is an extract from this project, multitouch, but made more freely available in a joint effort with ubuntu.

As a heads up, I am in the process of modifying the multitouch driver to use the mtdev package, so next time there is a tree update, you will have to have the mtdev library installed on your machine. This will not happen just yet, but well before the next release point.

Cheers!

---

### Post by jonas_t on 2010-06-25
> **alexmurray said:**
> Yes - the multitouch X driver requires this newer version of the bcm5974 kernel module since the default one shipped with Lucid doesn't contain all the required low-level multitouch event code. So you'll have no luck running multitouch without this.

mhkay, i'll give it another try these days. thanks!

---

### Post by joskapista on 2010-06-27
Sorry for being late with the answer. It seemed a little bit difficult  to me to find the problem as you suggested. Yesterday I installed the updated version as [Wbdsgnr]("http://ubuntuforums.org/member.php?u=666511") did. The result: single right and left click with tap works, but a bit sensible. It works only if I tap very carefully, but it works now :) Double click is still difficult, I have to tap 3 times minimum.
thanks :)

edit: double click is OK, the problem is only the sensibility. It works only if I tap very softly

---

### Post by krims0n32 on 2010-07-07
Thanks for your work on this driver. It works better than the synaptics version, it has very annoying behaviour with two-finger scroll (it often makes the cursor jump and/or select a bunch of text directly after scroll).

Your driver works a lot better. However there seems to be a problem with tapping. For a single tap, I have to tap twice, and three times for a double tap. The tap sensitivity seems fine for me. Can you fix this please ? :)

Also is there a way to disable the touchpad when typing ?

---

### Post by krims0n32 on 2010-07-08
> **krims0n32 said:**
> Thanks for your work on this driver. It works better than the synaptics version, it has very annoying behaviour with two-finger scroll (it often makes the cursor jump and/or select a bunch of text directly after scroll).

Your driver works a lot better. However there seems to be a problem with tapping. For a single tap, I have to tap twice, and three times for a double tap. The tap sensitivity seems fine for me. Can you fix this please ? :)

Also is there a way to disable the touchpad when typing ?

I was able to get tapping to work properly by setting TAP_GAP_MS to 50 (10 works as well) in memory.c. Single, double and triple tapping works perfectly now.

The only things I am missing now is dragging (tapping and then tap/dragging doesn't work) and touchpad disable when typing. Oh and is there a var I can alter to set the vertical scrolling speed (two finger swipe) ? It is a bit slow at the moment :)

Other than that it works much better than synaptics :popcorn:

---

### Post by joskapista on 2010-07-08
WOW, it works now: single, double and right tap is working now with TAP_GAP_MS 10. Everything is fine now, maybe the sensibility of the tapping could be a bit better. It is not a serious thing, only a sense that I like to tap a bit harder than the driver let me tapping.

---

### Post by krims0n32 on 2010-07-09
> **joskapista said:**
> WOW, it works now: single, double and right tap is working now with TAP_GAP_MS 10. Everything is fine now, maybe the sensibility of the tapping could be a bit better. It is not a serious thing, only a sense that I like to tap a bit harder than the driver let me tapping.

Does dragging work for you ?

---

### Post by kosumi68 on 2010-07-10
Setting TAP_GAP_MS to 10 ms will essentially disable tap-and-hold, since it measures the maximum time between the taps. Rather, you might want to try

* Increase TAP_X/YMOVE -- allows for a larger side movement when tapping

* Increase TAP_TOUCH_MS -- allows for a slower tap, i.e., a longer time actually touching with the pad

Otherwise, I am glad you got it working. :-)

---

### Post by krims0n32 on 2010-07-10
> **kosumi68 said:**
> Setting TAP_GAP_MS to 10 ms will essentially disable tap-and-hold, since it measures the maximum time between the taps. Rather, you might want to try

* Increase TAP_X/YMOVE -- allows for a larger side movement when tapping

* Increase TAP_TOUCH_MS -- allows for a slower tap, i.e., a longer time actually touching with the pad

Otherwise, I am glad you got it working. :-)

I set TAP_GAP_MS to 200 again and dragging works, but double tapping doesn't :P I tried altering TAP_X/Y MOVE to 0.01 * and 10.0 * but this makes no difference. It looks like the TAP_TOUCH_MS value is preventing the double tap, if I double tap really slowly I can get it to work but it's not convenient that way.

So now I have either dragging or double tapping but I would like both :D Anymore parameters I can try tweaking ? TAP_TOUCH_MS didn't seem to work either.

---

### Post by kosumi68 on 2010-07-10
Hehe, it could help to know what hardware you have, and some ballpark measurement of how you tap. :-) A normal tap would have down-sometime-up, and a tap-to-hold would be down-sometime-up-someothertime-down. Double tapping is not implemented, if that is any consolation.

---

### Post by krims0n32 on 2010-07-10
> **kosumi68 said:**
> Hehe, it could help to know what hardware you have, and some ballpark measurement of how you tap. :-) A normal tap would have down-sometime-up, and a tap-to-hold would be down-sometime-up-someothertime-down. Double tapping is not implemented, if that is any consolation.

I am on a Macbook 5.1 :) Basicly I use double tapping to open a file, select text or maximize a window (double tapping in titlebar). I suspect this is what most users do. So if I want to open a file for example I just tap two times quickly. To select a line of text in a terminal I tap quickly three times. I'm not sure I understand how double tapping would not be implemented, if I want to drag a window or an icon I also tap quickly two times but keep my finger on the trackpad on the second tap. This works fine at the moment, without delay.

FYI I can double and triple tap without issues, I just have to wait like half a second between the taps for it to work. That's why I figured it would be tweakable somwhere in the code :D

---

### Post by kosumi68 on 2010-07-10
> **krims0n32 said:**
> I am on a Macbook 5.1 :) Basicly I use double tapping to open a file, select text or maximize a window (double tapping in titlebar). I suspect this is what most users do. So if I want to open a file for example I just tap two times quickly. To select a line of text in a terminal I tap quickly three times. I'm not sure I understand how double tapping would not be implemented, if I want to drag a window or an icon I also tap quickly two times but keep my finger on the trackpad on the second tap. This works fine at the moment, without delay.

FYI I can double and triple tap without issues, I just have to wait like half a second between the taps for it to work. That's why I figured it would be tweakable somwhere in the code :D

Oh, then all is well - almost. :-) The double tap would emit an extra button click when releasing the second tap quickly. Instead, the first button is released, and pressed again on the third tap. And yes, there are several timeouts that take effect depending on actions, thumb detection and such. The FINGER_THUMB_MS and BUTTON_HOLD_MS are two such numbers, in gesture.c. Maybe that could help.

---

### Post by krims0n32 on 2010-07-10
> **kosumi68 said:**
> Oh, then all is well - almost. :-) The double tap would emit an extra button click when releasing the second tap quickly. Instead, the first button is released, and pressed again on the third tap. And yes, there are several timeouts that take effect depending on actions, thumb detection and such. The FINGER_THUMB_MS and BUTTON_HOLD_MS are two such numbers, in gesture.c. Maybe that could help.

I tried changing them but no change. Anything I can do to debug this ? I am proficient in C but am having trouble figuring out what does what in the code ;)

---

### Post by simar.mohar on 2010-07-14
Does this driver work for Synaptiics touchpad V7.2 .In ubuntu xinput --list-props shows Synaptics Capabilities 10100.

But it seems to work perfectly true multitouch in windows.

---

### Post by kosumi68 on 2010-07-19
There will be no release today. Apart from the planned transition to mtdev, which will appear in Maverick, nothing really happened for a while, so I will simply postpone the release until transferring to the new version becomes simpler. There has also been talk about a parameter interface; who knows, something might even have surfaced until then. :-)

---

### Post by labaom on 2010-07-22
Edit: Does this work on Macbook 7,1?

---

### Post by der_eismann on 2010-07-23
hope the new release comes soon...

i was following the instructions today, but after rebooting i couldn't move my mouse. after i removed the line from xorg.conf and rebooted, everything worked well again.

any idea? synaptics touchpad.

---

### Post by NiñoScript on 2010-07-23
> **der_eismann said:**
> hope the new release comes soon...

i was following the instructions today, but after rebooting i couldn't move my mouse. after i removed the line from xorg.conf and rebooted, everything worked well again.

any idea? synaptics touchpad.
That is known to happen when you first install it :)
Reload the module like this:```
modprobe -r bcm5974
modprobe bcm5974
```

Or read this little guide: [http://ubuntuforums.org/showpost.php?p=9193610&postcount=130](http://ubuntuforums.org/showpost.php?p=9193610&postcount=130)

---

### Post by labaom on 2010-07-23
I installed this and the multitouch works great. However, I enjoyed the two finger scroll that was used on my Macbook that came with Ubuntu (in the mouse settings). Now after I installed this I am using this as my two finger scroll. The reason I hate this one is because it is really really really slow compared to the other one. Is it possible I can disable the two finger scroll from this xf86 input so I can go back to using the default two finger scroll? I hope that makes sense.

---

### Post by der_eismann on 2010-07-24
Maybe someone could add this to the start post.

But I got this error:

```
philipp@philipp-laptop:~$ modprobe -r bcm5974
philipp@philipp-laptop:~$ modprobe bcm5974
FATAL: Error inserting bcm5974 (/lib/modules/2.6.32-24-generic/updates/dkms/bcm5974.ko): Operation not permitted
```

Any idea now?

---

### Post by NiñoScript on 2010-07-24
It seems you have to be root to do that, put "sudo " before each command.
I didn't notice it, as I always use root when playing in the terminal :P

---

### Post by der_eismann on 2010-07-25
```
philipp@philipp-laptop:~$ sudo modprobe -r bcm5974
[sudo] password for philipp: 
philipp@philipp-laptop:~$ sudo modprobe bcm5974
```

But it still doesn't work, trying to restart later.

---

### Post by labaom on 2010-07-29
Is there a way to make 2 finger scrolling to skip more steps? It is much harder to scroll with this enable than the one by default. But I do enjoy the multitouch. Also sometimes at startup after wifi connects my mouse freeze and I have to log off and log back on.. its a bit annoying.

---

### Post by kosumi68 on 2010-07-30
> **labaom said:**
> Is there a way to make 2 finger scrolling to skip more steps? It is much harder to scroll with this enable than the one by default. But I do enjoy the multitouch. Also sometimes at startup after wifi connects my mouse freeze and I have to log off and log back on.. its a bit annoying.

Try changing
```

static const float vscroll_fraction = 0.05;

```
in driver/multitouch.c

Cheers!

---

### Post by Enrique Fdez on 2010-08-10
> **labaom said:**
> Edit: Does this work on Macbook 7,1?
Hi, it does.
I'm currently using it because of click-to-drag funcionality.
However, I've lost tap-to-click (but I think I can enable it) and the graphical touchpad configuration tool.

---

### Post by furok23 on 2010-08-22
does anyone have a working variant of this driver for lucid and its respective kernel version?

i just pulled a total noob move and install this one for use with the bcm5974 driver and, epic fail, my mousepad stopped working and i had to reinitialise the SMH config with no mouse lol

---

### Post by alexmurray on 2010-08-22
You just need bcm5974 from the mactel-support repo (which is available for Lucid).

---

### Post by furok23 on 2010-08-23
Wellllllllllll call me a big throbbing noob, but I tried to add the mactel repo last night and it basically would let me access the packages.  Maybe I'm a re-tard. Or just Linux dumb. Which is more likely lol

also, this driver is just for the Linux system ya? In other words, it won't replace the driver on my mac side like a firmware replacement, ya?

---

### Post by alexmurray on 2010-08-23
You can add the mactel-repo by typing the following in a terminal:

```
sudo add-apt-repository ppa:mactel-support/ppa
```

Then install the updated version of bcm5974 by typing:

```
sudo apt-get update && sudo apt-get install bcm5974-dkms
```

And yes, this is just a driver for you Ubuntu Linux install - it won't and actually can't affect you Mac side installation or the firmware itself.

---

### Post by furok23 on 2010-08-24
got it workin now! alex youda man. 

ill keep following this thread and try to post useful info.

---

### Post by SwedishWings on 2010-08-29
One feature i really love to see (which is present in the OSX driver) is to be able to do this:

1) Start a drag by tapping
2) Move the item
3) RELEASE the drag finger
4) Resume dragging by, but from another position on the pad.

This works on my MBP 5,1 with OSX 10.6

Any chance this can be added?

Thanks,
Mike

---

### Post by dngfng on 2010-08-30
> **alexmurray said:**
> You can add the mactel-repo by typing the following in a terminal:

```
sudo add-apt-repository ppa:mactel-support/ppa
```Then install the updated version of bcm5974 by typing:

```
sudo apt-get update && sudo apt-get install bcm5974-dkms
```And yes, this is just a driver for you Ubuntu Linux install - it won't and actually can't affect you Mac side installation or the firmware itself.

I installed these drivers - the two fingered (secondary click) seems to kind of work. On the desktop i get the secondary click menu.

But when i try todo this on a file sitting on the desktop it performace a primary click.

Also I have noticed that unlike OSX you still can't use one finger to drag ant the other to "hold" the left mouse button (lower left corner).

It would be handy if someone could sumorize the current state of multitouch support.

---

### Post by bash321 on 2010-09-01
is there anyway to get this to work with one click tapping and not interfering when you are typing? as the old trackpad driver use to painfully do!! on a macbook pro 5.1

---

### Post by joskapista on 2010-09-02
Hello,
I had a few minutes to play with the source, and I was able (maybe) to find the best parameters:
scrolling  (in moultitouch.c):
static const float vscroll_fraction = 0.03;
tap to click (in memory.c):
#define TAP_XMOVE(c) (0.2 * get_cap_xsize(c))
#define TAP_YMOVE(c) (0.2 * get_cap_ysize(c))
static const int TAP_SETTLE_MS = 250;
static const int TAP_GAP_MS = 80;

I have only one problem: I would like to find the parameters of the touchpad cursor speed. Thanks

---

### Post by Greevous on 2010-09-11
> **joskapista said:**
> 

I have only one problem: I would like to find the parameters of the touchpad cursor speed. Thanks

I would like to find these as well. I mean, the speed and sensitivity is much, much better than what I originally got with Lucid, but it's still a bit quick. 

Also I've read some comments and opinions about tap-to-click and I think that it's really convenient as long as there's a palm-detect threshold somewhere to prevent accidental clicks. In my experience on Ubuntu, the pressure of full-on clicking on the 5,1 Macbook trackpad will sometimes cause the mouse to move slightly in the process and you end up clicking somewhere else entirely. 

It's especially annoying when "Submit" and "Cancel" buttons are right next to each other, if you know what I mean.

---

### Post by lvanderree on 2010-09-12
I could not compile multitouch (from git)

It returned:
```

gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c mtdev/mapgen.c -o obj/mtdev/mapgen.o
mtdev/mapgen.c: In function ‘init_caps’:
mtdev/mapgen.c:35: error: ‘MT_SLOT_ABS_EVENTS’ undeclared (first use in this function)
mtdev/mapgen.c:35: error: (Each undeclared identifier is reported only once
mtdev/mapgen.c:35: error: for each function it appears in.)

```

So what I did was made a small change to include/common.h:
```

/* includes available in 2.6.36 */
#ifndef ABS_MT_SLOT
#define ABS_MT_SLOT             0x2f    /* MT slot being modified */
#endif
#ifndef MT_SLOT_ABS_EVENTS
#define MT_SLOT_ABS_EVENTS {    \
        ABS_MT_TOUCH_MAJOR,     \
        ABS_MT_TOUCH_MINOR,     \
        ABS_MT_WIDTH_MAJOR,     \
        ABS_MT_WIDTH_MINOR,     \
        ABS_MT_ORIENTATION,     \
        ABS_MT_POSITION_X,      \
        ABS_MT_POSITION_Y,      \
        ABS_MT_TOOL_TYPE,       \
        ABS_MT_BLOB_ID,         \
        ABS_MT_TRACKING_ID,     \
        ABS_MT_PRESSURE,        \
}
#endif

```

adding an extra ifndef MT_SLOT_ABS_EVENTS which makes it compile, I haven't seen it working yet though (need to read more about what to do now ;))

---

### Post by lvanderree on 2010-09-12
Well I can see the driver is working, when running something like gesturetest but How do I configure gnome to make use of this all?

I don't like the synaptics driver since it does not recognize my palms and only supports two-finger scrolling and right-clicking (with two fingers) as a multitouch feature, but without synaptics I cannot tap, and non of the recognized gestures are translated to actions in gnome or any app.

Ps. I am running Maverick and I don't see lines with ENV{x11_driver} in my 66-xorg-synaptics.rules 

I also tried adding:
```

Section "InputClass"
    MatchIsTouchpad "true"
        Identifier      "Multitouch Touchpad"
        Driver          "multitouch"
EndSection

```
but than my mouse won't even move anymore, which can be a good thing, but again how do i configure this?

---

### Post by axflash on 2010-09-13
Hi,

I've enjoyed this driver in Fedora 13 on my Macbook Pro 6,2 - worked like a charm. Recently installed Ubunto 10.10 beta on it, and I don't have much luck. I installed it as before, and added the xorg.conf entry to load it. When Xorg starts, the pointer does not move. I have tried reloading bcm5974, but that doesn't change anything. If I remove the MatchIsTouchpad in xorg.conf, it works but then the keyboard doesn't work (I guess it ends up loading for all input devices). My Xorg.0.log for the multitouch part looks like this:

[     3.457] (II) config/udev: Adding input device bcm5974 (/dev/input/event4)
[     3.457] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[     3.457] (**) bcm5974: Applying InputClass "touchpad catchall"
[     3.457] (**) bcm5974: Applying InputClass "touchpad"
[     3.457] (II) LoadModule: "multitouch"
[     3.458] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[     3.458] (II) Module multitouch: vendor="X.Org Foundation"
[     3.458]    compiled for 1.9.0, module version = 0.1.0
[     3.458]    Module class: X.Org XInput Driver
[     3.458]    ABI class: X.Org XInput driver, version 11.0
[     3.459] (**) bcm5974: always reports core events
[     3.459] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
[     3.459] (II) device control: init
[     3.459] (**) Option "Device" "/dev/input/event4"
[     3.465] (II) multitouch: devname: bcm5974
[     3.465] (II) multitouch: devid: 5ac 236 1
[     3.465] (II) multitouch: caps: left mtdata ibt
[     3.465] (II) multitouch: 0: min: 0 max: 2048
[     3.465] (II) multitouch: 1: min: 0 max: 2048
[     3.465] (II) multitouch: 2: min: 0 max: 2048
[     3.465] (II) multitouch: 3: min: 0 max: 2048
[     3.465] (II) multitouch: 4: min: -16384 max: 16384
[     3.465] (II) multitouch: 5: min: -4460 max: 5166
[     3.465] (II) multitouch: 6: min: -75 max: 6700
[     3.476] (II) pointer_control
[     3.476] (**) bcm5974: (accel) keeping acceleration scheme 1
[     3.476] (**) bcm5974: (accel) acceleration profile 0
[     3.476] (**) bcm5974: (accel) acceleration factor: 2.000
[     3.476] (**) bcm5974: (accel) acceleration threshold: 4
[     3.476] (II) device control: on
[     3.493] (II) pointer_property
[     3.493] (II) pointer_property
[     3.493] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse0)
[     3.493] (**) bcm5974: Applying InputClass "touchpad catchall"
[     3.493] (**) bcm5974: Applying InputClass "touchpad"
[     3.493] (**) bcm5974: always reports core events
[     3.493] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD)
[     3.493] (II) device control: init
[     3.493] (**) Option "Device" "/dev/input/mouse0"
[     3.501] (EE) multitouch: cannot configure device
[     3.501] (EE) Couldn't init device "bcm5974"
[     3.501] (II) UnloadModule: "multitouch"

Seems like it's trying to add it twice, failing the second time, and then unloading multitouch because of that?

Any ideas?

---

### Post by axflash on 2010-09-13
Hi,

Played around a bit with the xorg.conf.d files, I'm attaching my Xorg.0.log as it stands now. I now don't see multitouch getting unloaded, but I still can't move the cursor. By accident I discovered that clicks do go through, as I'm able to double click my username in the gdm login screen and have it ask for the password.

Still stumped...

---

### Post by Twiggy794 on 2010-09-19
Just got Lucid up and running on my Macbook Pro 6,2, this driver is great!  For some reason though, I'm not seeing Buttons 10/11 in my Compiz config.  Trying to set that manually doesn't work (as others have pointed out in this thread).  I'm trying to simulate the same behavior the OP posted, where left/right swipes switch desktop.  Anybody have ideas?  Thanks!

---

### Post by lvanderree on 2010-09-19
I still cannot seem to get the multitouch extension to work.

I think the problem I am facing has been seen before here, but I cannot seem to find the solution, so any help would be appreciated.

I'm running Maverik and have attached my xorg.0.log

Can maybe someone post his xorg.conf, I didn't see anyone already has.

Thanks in advance!

---

### Post by axflash on 2010-09-20
> **lvanderree said:**
> I still cannot seem to get the multitouch extension to work.

I think the problem I am facing has been seen before here, but I cannot seem to find the solution, so any help would be appreciated.

I'm running Maverik and have attached my xorg.0.log

Can maybe someone post his xorg.conf, I didn't see anyone already has.

Thanks in advance!

This is the same issue that I reported on Maverick. I have talked to the udev maintainer, and he says that udev doesn't do device filtering. So this is most likely a bug in either Xorg or the multitouch driver.

Unless you want to get your hands dirty and try to fix it yourself, seems we have to wait until a version is released that is tested with 10.10. The git repo hasn't been updated in months, I'm eagerly awaiting the version that just uses the mtdev libs in 10.10.

---

### Post by Twiggy794 on 2010-09-20
> **axflash said:**
> This is the same issue that I reported on Maverick. I have talked to the udev maintainer, and he says that udev doesn't do device filtering. So this is most likely a bug in either Xorg or the multitouch driver.

Unless you want to get your hands dirty and try to fix it yourself, seems we have to wait until a version is released that is tested with 10.10. The git repo hasn't been updated in months, I'm eagerly awaiting the version that just uses the mtdev libs in 10.10.

It looks like the maintainer isn't really touching this much anymore (can't blame him with Maverick's multitouch support) but I would be willing to jump in and start working on the driver if somebody else with more Xorg knowledge than me was also willing.

---

### Post by Twiggy794 on 2010-09-21
Been digging around in the source code for a few days and I'm starting to make sense of what's going on here.  Two things.

First: If you're having trouble configuring buttons above Button9 in Compiz, set it in gconf-editor.  It's a UI bug in the compizconfig-settings manager that has 9 buttons hardcoded into the dropdown list when selecting a binding.  Doing this I was able to enable 3-finger swiping to rotate the desktop cube.

Second: I am working on getting this driver to work with my Magic Mouse.  For the most part, it does work.  The only issue is that it processes movement on the touch surface as pointer movement (like a touchpad) rather than using the device's normal optical track.  I'm trying to figure out how to get this working, but if anybody else has some experience or can provide guidance it would be much appreciated.  

I sent a PM to the driver author but my assumption is that they're wrapped up in Maverick fixes and he's probably not too concerned with the current implementation anyways considering uTouch is about to go live for all users.

---

### Post by jfanaian on 2010-09-23
Has anyone been able to get this working on Maverick? I have the same issue other users are reporting, where I can't move the mouse but can click when I enable the drivers. 

I know that they are working on better MT in Karmic, but while we wait for that roll out, I would love to get these drivers working.

Thanks!

---

### Post by NiñoScript on 2010-09-26
> **jfanaian said:**
> I have the same issue other users are reporting, where I can't move the mouse but can click when I enable the drivers.

I guess this is the same little problem that has always happened when installing this driver.
Take the time to read the whole topic, it's been fun following it :) 

But if you don't have the time to do that, at least read [**[SIZE="3"][COLOR="Blue"]this post[/COLOR][/SIZE]**]("http://ubuntuforums.org/showpost.php?p=9193610&postcount=130")

---

### Post by axflash on 2010-09-26
> **NiñoScript said:**
> I guess this is the same little problem that has always happened when installing this driver.
Take the time to read the whole topic, it's been fun following it :) 

But if you don't have the time to do that, at least read [**[SIZE=3][COLOR=Blue]this post[/COLOR][/SIZE]**]("http://ubuntuforums.org/showpost.php?p=9193610&postcount=130")

See [http://ubuntuforums.org/showpost.php?p=9839864&postcount=250](http://ubuntuforums.org/showpost.php?p=9839864&postcount=250)
It's not the same problem. The fact is that the driver works fine in current/older distros, but it does not work in the 10.10 beta (maverick). See musings about why that may be the case in this page and the previous.

---

### Post by axflash on 2010-10-04
> **axflash said:**
> See [http://ubuntuforums.org/showpost.php?p=9839864&postcount=250](http://ubuntuforums.org/showpost.php?p=9839864&postcount=250)
It's not the same problem. The fact is that the driver works fine in current/older distros, but it does not work in the 10.10 beta (maverick). See musings about why that may be the case in this page and the previous.

FWIW, I just tried with the 10.10 release candidate, and the issue is still exactly the same.

---

### Post by kosumi68 on 2010-10-12
Multitouch X Driver v1.0-rc1 Released

A somewhat longer wait than expected, but here is the release which uses the mtdev library. As you might be aware, lots of things are happening right now regarding gestures, and you can follow it on [https://launchpad.net/utouch/](https://launchpad.net/utouch/).

The plan for the Multitouch X Driver is to gradually move over to using utouch-grail, without losing any functionality. No time frame set as of yet. ;-)

Enjoy,
Henrik

---

### Post by axflash on 2010-10-12
Works like a charm now, thanks a lot Henrik!

---

### Post by chiklit on 2010-10-12
Just installed rc1 and it seems to be working fine on my MacBookPro 5,5. I was wondering though if there's a way to configure the gestures. 

Currently three-finger swipe up and down does forward/back in Chrome, I'd like it to be three-finger swipe left/right instead. And I'd like to map three-finger swipe up to Ctrl+W.

---

### Post by axflash on 2010-10-12
> **chiklit said:**
> Just installed rc1 and it seems to be working fine on my MacBookPro 5,5. I was wondering though if there's a way to configure the gestures. 

Currently three-finger swipe up and down does forward/back in Chrome, I'd like it to be three-finger swipe left/right instead. And I'd like to map three-finger swipe up to Ctrl+W.

So far the only option you have is to edit the source. In driver/multitouch.c, starting at line 234. Change the:

    button_scroll(local, 8, 9, &vswipe, step, gs->dy);

to

    button_scroll(local, 10, 11, &hswipe, step, gs->dx);

and vice versa on line 238.

---

### Post by axflash on 2010-10-12
> **axflash said:**
> So far the only option you have is to edit the source. In driver/multitouch.c, starting at line 234. Change the:

    button_scroll(local, 8, 9, &vswipe, step, gs->dy);

to

    button_scroll(local, 10, 11, &hswipe, step, gs->dx);

and vice versa on line 238.

That copy paste was a bit too eager, only change the 8/9 and 10/11, not the 6th argument to button_scroll()

---

### Post by chiklit on 2010-10-12
Thanks, looks like that worked.

Also, preemptive trouble shooting in case anybody else had the same problem I did compiling it the first time:

I had to [download]("http://bitmath.org/code/mtdev/"), compile and install mtdev separately before compiling the rc1 version. I also copied mtdev-plumbing.h into the include directory of the multitouch driver. I don't know if this was actually necessary but make seemed to want it in order to compile the driver.

EDIT: Ignore those instructions just download libmtdev-dev. (Thanks kosumi68)

---

### Post by kosumi68 on 2010-10-13
> **chiklit said:**
> Thanks, looks like that worked.

Also, preemptive trouble shooting in case anybody else had the same problem I did compiling it the first time:

I had to [download]("http://bitmath.org/code/mtdev/"), compile and install mtdev separately before compiling the rc1 version. I also copied mtdev-plumbing.h into the include directory of the multitouch driver. I don't know if this was actually necessary but make seemed to want it in order to compile the driver.

Perhaps you meant mtdev-mapping.h? The full name of the needed package is libmtdev-dev, which installs said header files under /usr/include/, where they are normally found automatically.

---

### Post by chiklit on 2010-10-13
> **kosumi68 said:**
> Perhaps you meant mtdev-mapping.h? The full name of the needed package is libmtdev-dev, which installs said header files under /usr/include/, where they are normally found automatically.

Yeah, that was probably it. Couldn't remember which one it wanted.

---

### Post by RossMc on 2010-10-14
Hi, 

Can anyone help me get this installed? I am new to Linux and have just installed ubuntu on my Mac and I have downloaded something and have the multitouch folder in my home space. How do I get it installed from there?

Thanks, Ross

---

### Post by RossMc on 2010-10-14
When I type sudo make install I get this message.

gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1 -O3 -fPIC -c src/capabilities.c -o obj/src/capabilities.o
In file included from include/capabilities.h:25,
                 from src/capabilities.c:22:
include/common.h:30: fatal error: mtdev-mapping.h: No such file or directory
compilation terminated.

---

### Post by Joe Zuyuz on 2010-10-14
I did get it to work in Maverick on a 2010 MacBook Pro, after a lot of  restarting and throwing about of more terminal commands than I'm used to applying. (It rejected the mactel repository until after I updated to  Maverick)

Is it typical for the thumb-recognition to function intermittently? It  works right when I set down my thumb and index finger down, but the  cursor just kind of sticks occasionally. The driver works like a charm, otherwise, but a tiny problem every few seconds can be as bad as a big problem. :(

---

### Post by RossMc on 2010-10-14
I just installed it all following the instructions on page 13 and now Linux won't boot LOL!

---

### Post by kosumi68 on 2010-10-16
Integrated button support for the Magic Trackpad

Just pushed a small patch that recognizes the Magic Trackpad as an integrated button device. This enables the special click-and drag logic also found on the later Macbooks.

Enjoy,
Henrik

---

### Post by freddy33 on 2010-10-18
I have a VAIO with the Magic Trackpad of Apple and it works great, thanks a lot!

I just have one issue: With the actual click on the new pads, the Tap-to-click behavior is annoying. How can it be deactivated?

Thanks again for the good job.

---

### Post by freddy33 on 2010-10-19
OK, found it :)
I changed in memory.c the easy to understand:
#define use_tapping 0

Recompiled, installed and worked immediately.

So, one last question: Do you plan integration with gpointing-device-settings for configuration of multitouch? Or you will have your own configuration tool?

Hope this driver will be distributed soon :)

---

### Post by nickaardo on 2010-10-19
Hi,

First thanks for this nice work, it's really annoying to have a Macbook and not be able to use all its functionalities on a Linux system.

I just have a bug and wasn't able to find a bug tracker to fill it, so i will post it here.

The driver work very well when you adjust some parameters, but sometimes it crash, its random, don't know exactly when it happens, or why. Here is a paste from my Xorg.0.log : 
```
[ 14705.358] (II) pointer_property
[ 14705.358] (II) pointer_property
[ 14848.662] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[ 14848.663] 
Backtrace:
[ 14848.663] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[ 14848.663] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a0824]
[ 14848.663] 2: /usr/bin/X (xf86PostButtonEventP+0xcf) [0x47bdaf]
[ 14848.663] 3: /usr/bin/X (xf86PostButtonEvent+0xb9) [0x47bed9]
[ 14848.663] 4: /usr/lib/xorg/modules/input/multitouch.so (0x7fbd8ce5d000+0x496d) [0x7fbd8ce6196d]
[ 14848.663] 5: /usr/lib/xorg/modules/input/multitouch.so (0x7fbd8ce5d000+0x4b88) [0x7fbd8ce61b88]
[ 14848.663] 6: /usr/bin/X (0x400000+0x6b837) [0x46b837]
[ 14848.663] 7: /usr/bin/X (0x400000+0x11f4e3) [0x51f4e3]
[ 14848.663] 8: /lib/libpthread.so.0 (0x7fbd93611000+0xfb40) [0x7fbd93620b40]
[ 14848.663] 9: /lib/librt.so.1 (clock_gettime+0x27) [0x7fbd928e50a7]
[ 14848.663] 10: /usr/bin/X (GetTimeInMillis+0x11) [0x4631c1]
[ 14848.663] 11: /usr/bin/X (0x400000+0xac269) [0x4ac269]
[ 14848.663] 12: /usr/bin/X (0x400000+0xac298) [0x4ac298]
[ 14848.663] 13: /usr/bin/X (WakeupHandler+0x4b) [0x4315bb]
[ 14848.663] 14: /usr/bin/X (WaitForSomething+0x1d7) [0x45b3f7]
[ 14848.664] 15: /usr/bin/X (0x400000+0x2bfd2) [0x42bfd2]
[ 14848.664] 16: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[ 14848.664] 17: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fbd9257cd8e]
[ 14848.664] 18: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[ 14899.471] (II) pointer_property
[ 14899.471] (II) pointer_property
[
```

I am running Ubuntu 10.10 on a Macbook 5.1
Feel free to ask if you need more data.
Really hope that someone will be able to fix this bug :S

Thanks

---

### Post by Tech2077 on 2010-10-19
how hard would it be to add 4 or 5 finger gestures, because i would like to code in the shortcuts to enter expose mode on compiz and other stuff, and is there a plan for a customizable GUI soon? Also, how would one go along adding to the code to set off keystrokes instead of buttons, since the expose mode with compiz by four finger vertical scroll and alt-tab application switching is my most critical want from multitouch.

---

### Post by paulinchen on 2010-10-20
Help!!!

I get some weird issues using this driver with Maverick. 
Sometimes I'm not able to take a click, sometimes the mouse moves to the left edge and stays there whatever I do.
This happens without any reason during the day.

Any ideas how to fix this?

---

### Post by kosumi68 on 2010-10-21
xf86-input-multitouch v1.0-rc2 released

This release is foremost about helping out getting fully functional integrated trackpads for maverick, both the macbook and the wireless ones. To that end, this version is also available in the Mactel PPA, and can be downloaded as
```

sudo apt-get install xf86-input-multitouch

```

A minimal setup to go into /etc/X11/xorg.conf
```

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection

```

Please note that there is (still) no configuration possibilities. I anyone wants to step forwards and implement it, please do. :-)

Shortlog since v1.0-rc1 appended.

Enjoy,
Henrik

      Enable integrated button support for the Magic Trackpad
      Adjust thumb detection based on kernel touch width...
      Do not grab by default
      Turn tapping on by default
      Support palm detection for trackpads without width support
      Increase vscroll speed by a factor of two
      Package as xf86-input-multitouch
      xf86-input-multitouch v1.0-rc2

---

### Post by smoors on 2010-10-21
Henrik, you made my day!! This update is just lovely.. i can confirm that i can now select text by dragging and move windows with the integrated touchpad on a macbook pro mid 2009 with maverick. 
I believe that i have to use more 'pressure' now to do a tap - sometimes i try to tap, but it does not get recognized. I'm not even sure if it depends on just the pressure or maybe even the size of the part of my finger which is touching the touchpad. Thanks so much for this update!

---

### Post by kennethsime on 2010-10-21
Henrik, I cannot for the life of me figure out how to install this. I've added the Mactel-Support PPA, done sudo-apt update, then sudo apt-get install xf86-input-multitouch, and then it tells me it can't find the package. I've tried looking through the mactel PPA in Software Center, and it doesn't show up there. I've tried looking for it in synaptic, that doesn't show up. I can't install the .deb from the launchpad because it's an i386 .deb file.

How does one install this? What am I missing?

---

### Post by Tech2077 on 2010-10-21
It hasn't finished building, check in a hour or two

---

### Post by cros13 on 2010-10-24
> **smoors said:**
> Henrik, you made my day!! This update is just lovely.. i can confirm that i can now select text by dragging and move windows with the integrated touchpad on a macbook pro mid 2009 with maverick. 
I believe that i have to use more 'pressure' now to do a tap - sometimes i try to tap, but it does not get recognized. I'm not even sure if it depends on just the pressure or maybe even the size of the part of my finger which is touching the touchpad. Thanks so much for this update!

I'm seeing the same issue with my MacBook Pro 5,3.

---

### Post by kwiksand on 2010-10-24
Hi, 

Loving RC2 on Maverick, touchpad seems to work perfectly now, but I can't disable Tap-to-Click any longer via Mouse or Pointing Device Preferences.

I know that you (Kosumi) said there was no configuration support as yet, but can this be turned off if compiled via the Git repository.  Or via gconf or something??

---

### Post by Espen11 on 2010-10-24
Thanks for providing this driver. It works on my MBP 7.1 running 10.10. I'v been waiting to rest my thumb on the pad while navigating with my index finger. ;) 

However, i'm also experiencing some problems with tapping. Tapping doesn't work while am resting my thumb on the touch/track -pad. 

Also, there is a delay/lag after each click. Both tapping (with one finger) and normal push-click.

And obviously all configuration possibilities have disappeared. I'm looking forward to this driver matures.

---

### Post by kennethsime on 2010-10-24
This works wonders. Thank you a thousand times over. We are one (major) step closer.

Has anyone had any success in emulating the smoothness of the OSX usage though?

I have tried playing with my acceleration and sensitivity to no end, and no luck in obtaining anything that's not jumpy and hard to use.

---

### Post by Jhime on 2010-10-25
This worked nicely. I have two issues though, I'll see if I have time to look at them myself sometime (not this week):

1. The pointer seem a bit to sensitive, even if I turn down acceleration in preferences it's a bit jumpy.
2. In OS X, I've noticed that once the driver determines that I have my thumb on the trackpad, it ignores all movement in that part until I take the thumb off. This also helps with the jumpyness as the pointer doesn't move for slight thumb movements.

Thanks.

Edit: duh, my link was to a post and not to the thread, so I didn't see the numerous replies already stating this.

---

### Post by mrmayor92 on 2010-10-25
can someone explain how to install this to a complete noob to ubuntu? much appreciated :)

---

### Post by wiznillyp on 2010-10-25
To install this, check the Wiki here: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Touchpad](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Touchpad) 

Be sure to install the PPA first (instructions at the top of the link above).

kosumi68,

I am using the new driver, this is getting much better!  Thanks!  Two comments, if you do not mind:

[LIST=1]
[*]Still can't seem to disable the touchpad while typing.  I am pissing myself off!  Any tips?
[*]Any way to enable some momentum on the scrolling ala OSX/iOS?  Meaning, if you scroll quickly the scrolling will continue against some friction after the swiping motion.
[/LIST]
Again, thanks for your efforts.

---

### Post by paulinchen on 2010-10-27
Using this driver a couple of weeks now, but since I'm updated to maverick the touchpad sometimes freezes, means I am not able to tab or click on anything.

Anyone know a trick how to fix this?

---

### Post by fhjlx on 2010-10-28
> **paulinchen said:**
> Using this driver a couple of weeks now, but since I'm updated to maverick the touchpad sometimes freezes, means I am not able to tab or click on anything.

Anyone know a trick how to fix this?

I have this same issue. I'm on 10.10 with a Macbook Pro 5,3

---

### Post by paulinchen on 2010-10-28
Glad I'm not the only one ...

Do you compiled it yourself or are you using the driver from the ppa?

One thing I found out while trying to reproduce the bug, is that it always happens a few minutes after starting a call via skype.
And more strange than that, I can still move the pointer but I'm not able to trigger the edge effects of compiz.

---

### Post by fhjlx on 2010-10-28
I installed from the macintel ppa. My problem actually that I am unable to move the pointer. I can click just fine but the pointer stays in the same position.

---

### Post by paulinchen on 2010-10-28
strange, for me its just the opposite: can move the pointer, but cannot tab or click anywhere.

Where is the position of the pointer when it stops moving, cause sometimes mine is just moving to the left edge and stays there. I can move it along the edge but move it back to somewhere else on the screen

I found out that it has nothing to do with skype.

Uninstalled the driver for now, cause its really not usable for me

---

### Post by matamoscas on 2010-11-03
My touchpad on my MBP7,1 mostly works.

Except it has a hyper active auto-clicking "feature" =)

I have tried clicking the "disable while typing" and adjusting basically everything that I can (I am not knowledgeable enough to hack at the kernel level), and simply can't get a comfortable usable touchpad.

Is that the current state?

Or, am I missing something?

I would really love to continue to use Ubuntu.

---

### Post by dre1187 on 2010-11-04
Im trying to install this driver to use the magic trackpad on a non apple computer. I am running 10.04. I have installed the mactel:ppa but it doesnt allow me to install it via sudo apt-get install xf86-input-multitouch. any ideas?

---

### Post by linuxopjemac on 2010-11-04
You have to be in 10.10. You might just want to download it yourself and install it manually:
[https://launchpad.net/~mactel-support/+archive/ppa/+files/xf86-input-multitouch_1.0%7Erc2-mactel1_i386.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/xf86-input-multitouch_1.0%7Erc2-mactel1_i386.deb)
[https://launchpad.net/~mactel-support/+archive/ppa/+files/xf86-input-multitouch_1.0%7Erc2-mactel1_amd64.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/xf86-input-multitouch_1.0%7Erc2-mactel1_amd64.deb)

---

### Post by nickaardo on 2010-11-04
Having the same problem as paulinchen and fhjlx
I am on a macbook 5.1 with maverick 64.

On startup everything works perfectly, but at random times the driver crash and :
- I cannot click but can move the pointer.
Or
- The pointer is stuck on the left top of the screen and i can only move it verticaly.

I noticed that this crash hapenned usually some time after launching skype or pidgin. Maybe it has something to do with the notifications or compiz.. dunno...

Really hope that this bug will be fixed because its unusable...

---

### Post by labaom on 2010-11-05
I would really enjoy a bug free version of this. This way I would use Ubuntu more.

---

### Post by paulinchen on 2010-11-06
properly it has something to do with compiz, cause for me it happens even I'm not using skype or else...

---

### Post by kwiksand on 2010-11-06
I can't remember for the life of me, but how did we remove tap to click in Ubuntu 10.04 using the same driver?  This was never a problem before.

---

### Post by smoors on 2010-11-06
Hi,

i've got exactly the same problem.. IIRC, the problem occurs even without skype, but using skype makes it occur faster. But are you sure that this is a problem with this driver? 
Yesterday i've tried to use my mighty mouse when i couldn't click anymore with the touchpad, and that didn't work either.

---

### Post by paulinchen on 2010-11-09
it never happened again since I went back to the regular driver, so I'm sure it has something to do with this driver.

---

### Post by nickaardo on 2010-11-10
Same for me, never happened with the old driver :(

---

### Post by babybruin on 2010-11-22
this driver is great, I first installed ubuntu and could not click and drag anything with the synaptics driver.  I was unuseable.  only thing missing for me is the ability to disable touchpad while typing, or perhaps just disable touch altogether.

I struggled for like a week trying to get the syndaemon workaround to disable when typing while using the multitouch driver, but it seems syndaemon has no effect when the driver is loaded.

---

### Post by smoors on 2010-11-23
Are there any news to the freeze issue? Is this already reported as a bug somewhere?

---

### Post by BlueDragonX on 2010-12-05
I'm experiencing the freeze issue as well...

I've also discovered that the thumb has a bug that sometimes causes tapping to be disabled for some time.  After a while of having my thumb down on the touchpad while moving the cursor I will attempt to tap and it will fail.  I've introduced additional logging into the driver and discovered that it is reporting my thumb as being on the touchpad even after letting up, and doesn't fix itself for a matter of seconds, sometimes minutes, and sometimes never.  This usually happens after having my thumb down on the touchpad for a number of seconds.

I'm not using Ubuntu, though, I'm using Gentoo.  The driver's a good start but I think it could use some improvement so I've started working on some tweaks with usability to start with.

If anyone else using Gentoo runs into this and needs some ebuilds, shoot me a PM.  I've got ebuilds and patches for all the multitouch stuff, though some of it's a work in progress.  mtdev and xf86-input-multitouch is good to go, though.

---

### Post by BlueDragonX on 2010-12-05
I've disabled thumb detection (by ignoring m->thumb) in my build and things seem to be working fine on that front.  Meaning, I have not had the touchpad ignore tapping due to this issue.  Of course, my touchpad is no longer disabled while typing, but I'd rather that be the case than have the bug.  I can probably hack around it, but we'll see.

I've confirmed that the freezing issue is related to the the multitouch driver crashing.  It seems to happen during times of high load.  I was able to cause the driver to crash by compiling empathy and its dependencies a moment ago.  Here are the resulting entries in Xorg.0.log:

```

[ 33017.758] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[ 33017.758]
Backtrace:
[ 33017.758] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a12e8]
[ 33017.758] 1: /usr/bin/X (mieqEnqueue+0x1eb) [0x4a0c7b]
[ 33017.758] 2: /usr/bin/X (xf86PostButtonEventP+0xca) [0x47d5ba]
[ 33017.758] 3: /usr/bin/X (xf86PostButtonEvent+0xb9) [0x47d6e9]
[ 33017.758] 4: /usr/lib64/xorg/modules/input/multitouch.so (0x7fc84d1f6000+0x3d53) [0x7fc84d1f9d53]
[ 33017.758] 5: /usr/lib64/xorg/modules/input/multitouch.so (0x7fc84d1f6000+0x3f1e) [0x7fc84d1f9f1e]
[ 33017.758] 6: /usr/lib64/xorg/modules/input/multitouch.so (0x7fc84d1f6000+0x4128) [0x7fc84d1fa128]
[ 33017.758] 7: /usr/bin/X (0x400000+0x6cad7) [0x46cad7]
[ 33017.758] 8: /usr/bin/X (0x400000+0x117569) [0x517569]
[ 33017.758] 9: /lib/libpthread.so.0 (0x7fc852f7e000+0xf010) [0x7fc852f8d010]
[ 33017.758] 10: /lib/librt.so.1 (clock_gettime+0x5) [0x7fc8522512d5]
[ 33017.758] 11: /usr/bin/X (GetTimeInMillis+0x11) [0x465ca1]
[ 33017.758] 12: /usr/bin/X (0x400000+0xb6ff9) [0x4b6ff9]
[ 33017.758] 13: /usr/bin/X (0x400000+0xb7028) [0x4b7028]
[ 33017.758] 14: /usr/bin/X (WakeupHandler+0x43) [0x4346d3]
[ 33017.759] 15: /usr/bin/X (WaitForSomething+0x1d6) [0x45c996]
[ 33017.759] 16: /usr/bin/X (0x400000+0x2f2b2) [0x42f2b2]
[ 33017.759] 17: /usr/bin/X (0x400000+0x24da5) [0x424da5]
[ 33017.759] 18: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7fc851f12bbd]
[ 33017.759] 19: /usr/bin/X (0x400000+0x24959) [0x424959]

```

This does not happen when I use the synaptics driver.

The behavior during the crash is rather unusual.  The trackpad continues to function properly in the widget of the window you were focused on during the crash.  I also get debug logging out of the multitouch driver after the crash, so it's fielding events but X's input layer seems to be horked.

EDIT: Looks like we're triggering this code in xorg's mieq.c file:
```

    else {
        static int stuck = 0;
        /* Toss events which come in late.  Usually this means your server's
         * stuck in an infinite loop somewhere, but SIGIO is still getting
         * handled. */
        if (((oldtail + 1) % QUEUE_SIZE) == miEventQueue.head) {
            if (!stuck) {
                ErrorF("[mi] EQ overflowing. The server is probably stuck "
                        "in an infinite loop.\n");
                xorg_backtrace();
                stuck = 1;
            }
#ifdef XQUARTZ
            pthread_mutex_unlock(&miEventQueueMutex);
#endif
	        return;
        }
        stuck = 0;
    }

```

My brief glance at this tells me w're overflowing the queue size and being ignored.  I'll do some additional debugging and verify when I get some more time.  QUEUE_SIZE is 512.

---

### Post by jako on 2010-12-05
Many thanks for working on this. It's a real show stoppper for an otherwise nice Ubuntu on Mac distribution.

---

### Post by BlueDragonX on 2010-12-05
No problem.  I hope to help get this driver working and well integrated if I can.

I've decided to throw another wrench into the works.  I just picked up a Magic Mouse to play with.  The multitouch driver is treated like a mouse rather than a touchpad, so in the Gnome mouse preferences there's no touchpad tab, meaning sensitivity and acceleration is global for the multitouch touchpad and any mice on the system.  Will need to figure out how to deal with that.

In addition, I'm wondering how the Magic Mouse multitouch can be integrated?  I may take apart the existing driver and see what's under the hood.

---

### Post by BlueDragonX on 2010-12-06
It looks like the freezing issue on my machine is due to an issue in the nvidia driver when used with xorg 1.8.0+.  Stack traces from other people's machines show the input driver as well.

In addition, I've been running the thumb detection on for the last couple of hours and have not experienced any issues.  Oddly...I haven't changed anything.  So we'll see.

I may post my patch once I get the nvidia issue sorted.

---

### Post by smoors on 2010-12-06
> **BlueDragonX said:**
> 
I may post my patch once I get the nvidia issue sorted.

Yay, that's cool. I'm looking forward to test your patch!

---

### Post by dentifrice on 2010-12-10
Hey there,

I'm a little confused about the multitouch X driver and I have a few questions:
- what's the catch of using multitouch vs synaptics? (I read a report from a MacBookAir3 user - with the BCM5974 chipset - who used the latest synaptics and said it was working great)
- does it have second/third button emulation by default? On my MBA3,1, I didn't get that to work;
- its home being [http://bitmath.org/code/multitouch/](http://bitmath.org/code/multitouch/) AFAIK, where does one file bugreports?
- is it the right thread to get support (not just for Ubuntu)?

Thanks a lot in advance for any clarification!

---

### Post by kwiksand on 2010-12-10
As far as I was aware Synaptics didn't have
- Thumb down finger dragging
- Zoom/Rotate
- Multi finger swipe

So apart from right click and two finger scroll, no MT, I think!

---

### Post by dentifrice on 2010-12-10
> **kwiksand said:**
> As far as I was aware Synaptics didn't have
- Thumb down finger dragging
- Zoom/Rotate
- Multi finger swipe

So apart from right click and two finger scroll, no MT, I think!

Thanks for the clarification. Do you have mouse button emulation working with the multitouch driver? If so, does that require modifying the source?

---

### Post by BlueDragonX on 2010-12-10
Mouse button emulation works out of the box.

What distro are you using?  If you've got issues with the driver you can start by posting them in this thread, chances are they've already been worked out.

---

### Post by dentifrice on 2010-12-10
> **BlueDragonX said:**
> Mouse button emulation works out of the box.

What distro are you using?  If you've got issues with the driver you can start by posting them in this thread, chances are they've already been worked out.

Thanks. Then it confirms something is wrong with my config. I'm using Debian as a distro, so the solution shouldn't be very far from Ubuntu's.

My issues are:
- regular pointer freeze (as reported by other people);
- no mouse button emulation;

(I haven't tested other MT features as I'm mostly unaware of them :smile:)

I could also add something like « general weirdness ». The touchpad behaves in a strange way, and feels very imprecise; whenever I click on a menu item for instance, it jumps to the following entry 80% of the time. Add freezes to that, and I find it hardly usable. However, two finger scrolling works!

There's bcm5974/multitouch related error messages in my */var/log/Xorg.0.log*. I'm joining a trimmed version as an attachement, leaving the X server header so program versions are visible.

I'm using *mtdev 1.0.11* & *multitouch 1.0-rc2*. I uninstalled the *xserver-xorg-input-synaptics* package, to make sure I'm using *xf86-input-multitouch* and nothing else.

---

### Post by BlueDragonX on 2010-12-10
The attached log file doesn't indicate any issues.  The EE's at the end of the file are to report that the multitouch driver could not be loaded for /dev/input/mouse1, which is expected since that device won't support multitouch.

Multitouch is initialized and working on the /dev/input/event8 device.  You can see the multitouch initialization happening halfway through the file.

I'll upload my xf86-input-multitouch patch after a bit, it tweaks some of the settings to make it (in my opinion) more usable.  You should try it out and see if that fixes any of your problems.

EDIT: Attached my patch.  Keep in mind I rolled this for my own purposes and for Gentoo.

---

### Post by dentifrice on 2010-12-10
> **BlueDragonX said:**
> The attached log file doesn't indicate any issues.  The EE's at the end of the file are to report that the multitouch driver could not be loaded for /dev/input/mouse1, which is expected since that device won't support multitouch.

Multitouch is initialized and working on the /dev/input/event8 device.  You can see the multitouch initialization happening halfway through the file.

I'll upload my xf86-input-multitouch patch after a bit, it tweaks some of the settings to make it (in my opinion) more usable.  You should try it out and see if that fixes any of your problems.

Of course. Now it makes perfect sense :)

I still can't get button emulation to work though. Any idea what I could do to look further into that?

As for a usability patch, yay, that sounds pretty good :)

---

### Post by BlueDragonX on 2010-12-10
> **dentifrice said:**
> Of course. Now it makes perfect sense :)

I still can't get button emulation to work though. Any idea what I could do to look further into that?

As for a usability patch, yay, that sounds pretty good :)

I attached my patch to the previous post.  It's against 1.0-rc2 so you should be good to go.  By default it sets DEBUG_TAP=1 in the CFLAGS, which will add a line to the Xorg log every time you touch the pad, but it may help with figuring out why you're having issues.  However, the tweaks may solve the issue, but only one way to find out :P

And it may be interesting for you to 'tail -f /var/log/Xorg.0.log' in a console while you use your trackpad.

---

### Post by dentifrice on 2010-12-10
> **BlueDragonX said:**
> I attached my patch to the previous post.  It's against 1.0-rc2 so you should be good to go.  By default it sets DEBUG_TAP=1 in the CFLAGS, which will add a line to the Xorg log every time you touch the pad, but it may help with figuring out why you're having issues.  However, the tweaks may solve the issue, but only one way to find out :P

And it may be interesting for you to 'tail -f /var/log/Xorg.0.log' in a console while you use your trackpad.

Thanks! The patch applied cleanly. Unfortunately, it doesn't fix the mouse button emulation issue, but it does make the touchpad more usable *somehow*. I can now move the pointer with my right thumb, which was the main show stopper for me beforehand.

However, the only way to drag and move windows it to click at the very bottom of the touchpad, maintain the click and move with the same finger. In other words, having one finger using the pointer and another one clicking doesn't work. I find it pretty unpractical, but maybe that's a feature?

---

### Post by dentifrice on 2010-12-10
I forgot to mention that logging in /var/log/Xorg.0.log didn't occur for some reason.

---

### Post by dentifrice on 2010-12-10
> **dentifrice said:**
> However, the only way to drag and move windows it to click at the very bottom of the touchpad, maintain the click and move with the same finger. In other words, having one finger using the pointer and another one clicking doesn't work. I find it pretty unpractical, but maybe that's a feature?

As a result of that, selecting text is almost impossible.

---

### Post by BlueDragonX on 2010-12-10
> **dentifrice said:**
> Thanks! The patch applied cleanly. Unfortunately, it doesn't fix the mouse button emulation issue, but it does make the touchpad more usable *somehow*. I can now move the pointer with my right thumb, which was the main show stopper for me beforehand.

Well, my tweaks really do two things: increases the area in which it will accept double taps, reduces the timeouts for tapping and dragging, and reduces the "dead time" after a tap.  Basically I'm assuming the user is faster with their fingers.

> **dentifrice said:**
> However, the only way to drag and move windows it to click at the very bottom of the touchpad, maintain the click and move with the same finger. In other words, having one finger using the pointer and another one clicking doesn't work. I find it pretty unpractical, but maybe that's a feature?

The driver doesn't (yet?) support dragging with one finger and tapping with another.  It does support the more traditional quick-double-tap-and-drag functionality, but the way it is designed conflicts with double-taps.  Meaning, if your second tap is within X ms of the first, then it treats it as a drag, but if the second tap falls after that X ms, it's a double-tap.  Really it should be checking how long you hold down your finger on the second tap to determine whether it's a tap or a drag.

That bing said, I'm not the original developer, and up to this point I've only been tweaking constants in the existing code and adding debug output to better understand how it works.  Now that I know all that I may spend some time on the actual logic behind the whole thing to help improve usability.

---

### Post by dentifrice on 2010-12-10
@BlueDragonX: weird - I can point and click "normally" using multitouch w/o your patch.

In any case, thanks a lot for your help, and I sure hope you can improve the driver! Good luck!

---

### Post by *Legion* on 2011-01-02
I have been driven absolutely nuts by the two finger right-click functionality. I pretty much despise it in OS X too. Constant right-clicks when I'm just trying to do a damn normal click. I'm *SO* sorry my second finger happened to slightly touch the touchpad, stupid MacBook Pro!

I disabled it in the driver by altering "button.h" to make MT_BUTTON_RIGHT match MT_BUTTON_LEFT:

```

#define MT_BUTTON_LEFT 0
#define MT_BUTTON_MIDDLE 1
#define MT_BUTTON_RIGHT 0

```

Question #1: Is there a more proper way of banishing the hateful two-finger right-click feature to the Hades where it belongs?

Question #2: Is there a way of enabling Control+Click to behave as right click, as it is done in OS X? I tried installing mouseemu and running the mouseemu command as listed [here]("http://manpages.ubuntu.com/manpages/maverick/man8/mouseemu.8.html"), but control-click still does nothing.

I have looked for control-click as right-click in the past and have always come up empty. I find it hard to believe that Linux can be so customizable and yet this function could be so hard to replicate.

---

### Post by niQo on 2011-01-02
Hello,
I'm trying to make this driver work on arch linux with Apple magic trackpad, I have compiled and installed multitouch from git and mtdev v1.1.0.
I'm having a similar issue as axflash :
[http://georgia.ubuntuforums.org/showpost.php?p=9840651&postcount=251](http://georgia.ubuntuforums.org/showpost.php?p=9840651&postcount=251)

multitouch module is unloaded, I can click with magic trackpad but I can not move.

Any help ?

My xorg log :

```

[  1074.947] (II) config/udev: Adding input device trackpad (/dev/input/mouse1)
[  1074.947] (**) trackpad : Applying InputClass "Magic Trackpad"
[  1074.947] (**) trackpad : always reports core events
[  1074.947] (II) XINPUT: Adding extended input device "trackpad" (type: TOUCHPAD)
[  1074.947] (II) device control: init
[  1074.947] (**) Option "Device" "/dev/input/mouse1"
[  1074.956] (EE) multitouch: cannot configure device
[  1074.956] (EE) Couldn't init device "trackpad"
[  1074.956] (II) UnloadModule: "multitouch"
[  1074.956] (II) config/udev: Adding input device trackpad (/dev/input/event7)
[  1074.957] (**) trackpad: Applying InputClass "evdev pointer catchall"
[  1074.957] (**) trackpad: Applying InputClass "Magic Trackpad"
[  1074.957] (**) trackpad: always reports core events
[  1074.957] (II) XINPUT: Adding extended input device "trackpad" (type: TOUCHPAD)
[  1074.957] (II) device control: init
[  1074.957] (**) Option "Device" "/dev/input/event7"
[  1074.966] (II) multitouch: devname: trackpad
[  1074.966] (II) multitouch: devid: 5ac 30e 160
[  1074.966] (II) multitouch: caps: left right ibt
[  1075.006] (II) pointer_control
[  1075.006] (**) trackpad: (accel) keeping acceleration scheme 1
[  1075.006] (**) trackpad: (accel) acceleration profile 0
[  1075.006] (**) trackpad: (accel) acceleration factor: 2.000
[  1075.006] (**) trackpad: (accel) acceleration threshold: 4
[  1075.006] (II) device control: on
[  1075.033] (II) pointer_property
[  1075.033] (II) pointer_property


```

Magic trackpad xorg.conf :
/etc/X11/xorg.conf.d/60-magictrackpad.conf
```

Section "InputClass"
    Identifier      "Magic Trackpad"
    MatchUSBID "05ac:030e"
    Driver           "multitouch"
EndSection

```

---

### Post by BlueDragonX on 2011-01-03
I've just completed alpha1 of my multitouch driver and am in the process of testing it out on my machine.  Using it right now as I type with.  Seems to work well, but I already know it will undergo a partial rewrite here in a bit as it's not as efficient as I want it to be, and I need to incorporate tap-to-drag functionality, as well as pulling out all the configuration into the Xorg.conf file (all values are hardcoded at the moment).

Expect more to come in the following weeks.

---

### Post by ste.sancri on 2011-01-09
Hi! I'm a complete noob with ubuntu but when I first saw it I decided to put in on my macbbok pro 5.3.

I've followed the instruction do get two-fingers drag&drop and I've installed bcm5974.
I've also edit my xorg.conf file to let him move quickly because at first it was too slow for me. Here's what it looks like

```
Section "InputDevice"
Identifier    "Generic Keyboard"
Driver     "kbd"
Option     "XkbRules"    "xorg"
Option     "XkbModel"    "pc105"
Option     "XkbLayout"    "us"
EndSection

Section "InputDevice"
Identifier    "Configured Mouse"
Driver     "mouse"
Option     "CorePointer"
EndSection

Section "InputDevice"
Identifier    "Synaptics Touchpad"
Driver     "synaptics"
Option     "SendCoreEvents"    "true"
Option     "Device"     "/dev/input/mice"
Option     "Protocol"     "auto-dev"
#    Option     "CorePointer"
#    Option     "HorizEdgeScroll"    "0"
Option     "SHMConfig"     "True"

# exclusive grabbing of device
Option     "GrabEventDevice"    "1"

# simulate right button
Option     "MultiFingerButton"    "2"

# not using edge scrolling
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"

# use two finger scrolling
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1" 

# set to 0 if you don't want horizontal scrolling
# scroll speed, lower is faster
Option "HorizScrollDelta" "0"
Option "VertScrollDelta" "40"

# minimum pressure motion factor
Option "PressureMotionMinZ" "10"

# touch and untouch thresholds, higher numbers
# if you like to push hard, change to 30 or 40
Option "FingerLow" "16"
Option "FingerHigh" "23"
Option "FingerPress" "256"

# palm detect
Option "PalmDetect" "0"
Option "PalmMinWidth" "180"
Option "PalmMinZ" "10" 

# borders based on output from synclient
# controls the edge scrolling
# turned off by specifing the exact size /henrik
Option "LeftEdge" "0"
Option "RightEdge" "1280"
Option "TopEdge" "0"
Option "BottomEdge" "800"

# speeds, smaller number for a slower mouse
Option "MinSpeed" "0.8"
# 0.5 is very slow, 1.5 is very fast
Option "MaxSpeed" "1.2"
# up to 1.5 works ok
Option "AccelFactor" "0.10"

# tap times, change to suit your tapping habits
Option "MaxTapMove" "100"
Option "MaxTapTime" "223"
Option "MaxDoubleTapTime" "200"

# don't change these or two finger tap stops working
#Option "TapButton2" "3"
#Option "TapButton3" "2"
Option "TapButton2" "0"
Option "TapButton3" "0"

# must be commented out or normal tapping wont work
#Option "TapButton1" "0"

# not using corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "0"
Option "LTCornerButton" "0"
Option "LBCornerButton" "0" 
EndSection

```After upgrading the bcm driver (with sudo apt-get upgrade) drag and drop disappear and I have to follow the entire path to get bcm5974-dkms_1.1.4_all_test.deb to let it come back. What am I doing wrong?!
I've also experienced, after some reboots that the driver won't work even if I had put usbhid on my blacklist as I've seen on this forum.

Thank you very much for your support! I really appreciate your work. Hope to give my help some day!

Ste


EDIT: Just discovered that I can drag and drop with one finger. It just means that I've to get used to!

---

### Post by BlueDragonX on 2011-01-09
This thread is in regards to the multitouch driver, not the synaptics driver, which you're using.  If you need help with setting up the synaptics driver then I recommend creating a new post where people can see it.

---

### Post by ste.sancri on 2011-01-11
So sorry for that! I've make confusion!

---

### Post by dennis.jarosch on 2011-01-28
@BlueDragon: have you been looking into the code and the bugs recently?

I have tweaked the driver settings and implemented initial properties support, e.g. it's possible now for syndaemon to disable the touchpad during typing. Now, I have also experienced the freezing issue and I can only assume it's because of my increased usage of tapping.

I do actually think that there's a bug in the driver. If you output debugging messages in tickle_button (multitouch.c), you'll see in the logs that they are flooded with messages at some point. In my theory, this then causes the overflow in the X server that you mentioned. I just noticed this, but it seems that the flooding is related to buttons 3 - 6, i.e. vertical and horizontal scrolling. In any way, the driver posts _a lot_ of xf86PostButtonEvents. 

Dunno if kosumi is still working on the driver and reading this or busy with other stuff. Maybe he can chime in as well.

---

### Post by BlueDragonX on 2011-01-28
> **dennis.jarosch said:**
> @BlueDragon: have you been looking into the code and the bugs recently?

Actually I've completely rewritten the state tracking and gesture recognition in the driver.  The only thing that I haven't touched in the driver are the hwstate and capabilities.

I've been using an initial, feature incomplete driver for a week or so now and it's been working fine.  I'm in the process of adding in the missing features and making the driver fully configurable.  I'm making pretty good progress.

As for the tickle issue, that should no longer be a problem.  When the old driver sends a "click" the down event is immediately followed by an up event.  Aside from potentially flooding the event system, this means that in some situations clicks aren't recognized by the system.  One situation in particular which effects me is when I'm remoted into a virtual machines.  Tapping just doesn't work there, and this is why.  To resolve this I am adding a configurable delay between the down and up events, just like the synaptics driver.

That being said, the driver will be at least as configurable as the synaptics driver for the features that are there.

On the MacBook Air, I'm still not entirely convinced it's the multitouch driver that's causing the issue lockup issue.  I still have issues with the nVidia driver crashing, though it's less catostrophic now (it generally recovers and I don't have to restart X), so it might have been some combination of the two.  Basically, without debugging X directly, I have no proof one way or another, I'm just making guesses.  But perhaps the new multitouch driver will alleviate some of the "strain".

If you want to share your changes for disabling the touchpad on typing using the syndaemon I can integrate that as well.  Hadn't thought of that, honestly.  Though the landscape of the driver is completely different, now, I do have support for disabling the pad, so it shouldn't be too difficult.

---

### Post by dennis.jarosch on 2011-01-28
Wow, that was a quick reply and it sounds as if you've done a lot of work. ;-)

If you have already have a version that is configurable during run time, and guessing that you have taken synaptics as an example, you probably have all the pieces in place to have syndaemon deactivate the touchpad during typing.

I added properties to the driver, which basically is a struct and a few calls to tell it which ones it should consider, e.g. "Synaptics Off". But if I am not mistaken the runtime configurations (using synclient) should work the same way.

Have you exchanged ideas with the original developer? Will there be a merge with the multitouch driver or is your driver going to be a replacement?

If you want me to help you test your driver, I would love to check it out. I'm on a MacBook 5,5 so I cannot comment on the nvidia crashes. Things are fine on my laptop in this respect.

---

### Post by BlueDragonX on 2011-01-28
Yeah, I've put quite a few hours into it at this point.  My version I'm running on my Mac at the moment isn't configurable, and the gesture recognition for anything but scrolling is a bit finicky (though the only time I felt compelled to use them was when working in Inkscape - kind of an eye opener there).

It's evolved a bit since the version I'm running.  I looked a bit at the synaptics driver to see how it was configured and to get some sensible default values, but I didn't borrow from their code at all.  The code was already a lot cleaner than the synaptics driver, and I think I've only improved on that.  It certainly showcases my style, for better or for worse.

I haven't talked to the original author, Henrick Rydberg.  When I first started playing with it I wasn't sure if I was even going to take it this far, but it turned out to be a real interesting and challenging project and sucked me in.

After I'm done with this version I'll post the source here and share it with him and see if it can't get integrated.

I'm hoping I can get scaling and rotating working properly, then I'll consider myself ahead.

---

### Post by BlueDragonX on 2011-02-10
Gentlemen!  After much delay, I give you the (very unofficial) xf86-input-multitouch v1.1 alpha!  Available here:

[http://www.dev.fatalmachine.org/xf86-input-multitouch-1.1_alpha4.tar.gz](http://www.dev.fatalmachine.org/xf86-input-multitouch-1.1_alpha4.tar.gz)

Now...  I say unofficial because my efforts on this have been unrelated to the official xf86-input-multitouch driver.  I used the code base and rewrote the touch tracking and gesture recognition.  I humbly submit that I believe it is an improvement.  In any case, this one *is* fully configurable, and supports all of the same features as the original, though the gesture recognition is a completely different implementation.

Now, this is an "alpha" so I would appreciate everyone's feedback.  The README file contains all of the configuration information, as well as my email if you find bugs.

As an example, this is how I have mine configured:

```

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "multitouch"
    Option          "ClickTime" "50"
    Option          "IgnoreThumb" "False"
    Option          "TapDragEnable" "False"
    Option          "ScrollDistance" "300"
EndSection

```

As mentioned in previous posts, I intend to implement support for the synaptics daemon in order to disable the trackpad while typing.  That is the only immediate outstanding feature.

I will be contacting Henrick Rydberg to see if we can work out merging this.  I'll post up on how that progresses.

And if you're a Gentoo nut, I've got ebuilds for this and the mtdev library.  Ask and ye shall receive.

---

### Post by dennis.jarosch on 2011-02-11
Congratulations!

I submitted some patches to Henrik yesterday and we'll see whether he agrees to merge them to the original Multitouch X driver. These patches contain fixes to the annoying 'X server crash/hang' and the 'taps suddenly stop working' bugs. They also add support for the disabling of the touchpad during typing, making use of syndaemon.

Since that may be of use to you, I am attaching the relevant patch to this post. It's not a lot of code and I'm sure you'll see through it really quickly.

---

### Post by *Legion* on 2011-02-16
I'm a little confused on acceleration and sensitivity.

I notice that when I go to the General tab in Mouse Preferences in GNOME, if I alter the Acceleration slider, it impacts the response of the mouse cursor.

But if I alter Sensitivity, nothing at all happens.

I did not see anything related to acceleration or sensitivty in alpha 4's README, so is there no way to adjust sensitivity? I have had great results tweaking all of the other settings listed in the README to get a pointer that behaves like I want, in all ways except the speed of movement.

---

### Post by BlueDragonX on 2011-02-17
At present there is no way to adjust sensitivity.  I'll be integrating that feature shortly, along with a few tweaks and getting a project page set up for my version.

---

### Post by demheld on 2011-02-21
Hey there! 
I am also running this driver and it really works very good!
Thanks a lot for the effort of implementing it!

But I do have a few questions:

I really tried a lot of configurations and i am wondering what other people are using.
I'm running currently the following

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "multitouch"
    Option          "ClickTime" "50"
    Option          "MaxTapTime" "80"
    Option          "IgnoreThumb" "False"
    Option          "ScrollDistance" "150"
    Option          "FingerHigh" "5"
    Option          "FingerLow" "5" 
EndSection
```And the pinchtozoom is taking no effect..do i have to enable something (maybe Desktop effects?) further to take this effect?

cheers

---

### Post by Barnabooth on 2011-02-22
I am sorry if a dilettant like me is disturbing, but I would be grateful if someone could point me in the right direction to install this multitouch-1.1_alpha4? 
I have extracted the tar.gz file in /usr/local/src and been following this guide:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
but as there is no compile file in the package to run the command ./compile from, I am lost. I know I am ignorant and have overlooked the obvious, but I am willing to do some exercises, take my bumps and learn the best I can, as this touchpad-issue with random tapping-freezes & crashes is really annoying. (mbp5,5 & maverick by the way).

---

### Post by demheld on 2011-02-23
check page 13! ninoscript wrote a cool and easy help for getting it to work!

leave out step 5! this is for downloading the other driver! but you have the other version..blablaalphabla

in step 6: "cd" to the directory where you unpacked it and then "make"

---

### Post by Barnabooth on 2011-02-23
Thanks a lot!

---

### Post by *Legion* on 2011-02-23
> **BlueDragonX said:**
> At present there is no way to adjust sensitivity.  I'll be integrating that feature shortly, along with a few tweaks and getting a project page set up for my version.

OK. I appreciate the clarification. And I also greatly appreciate the driver. It now delivers sufficient support for the integrated-button MBP trackpad that I can finally use Linux on my 13" MBP comfortably. I'm sure thankful someone is putting in the effort to make this work.

---

### Post by NiñoScript on 2011-02-24
> **demheld said:**
> check page 13! ninoscript wrote a cool and easy help for getting it to work!

leave out step 5! this is for downloading the other driver! but you have the other version..blablaalphabla

in step 6: "cd" to the directory where you unpacked it and then "make"

Nice to know that still helps people,
maybe we could update my post with the new instructions, and if there's a project webpage coming, and it there :D

After 10 delightful months, I went back to Mac OS X where I have my beloved TextMate and Adium, but I'll try to switch to Ubuntu again in a few months, so I hope there are updated instructions by then :P
(I like switching OSs from time to time)

---

### Post by polhallen on 2011-02-25
Hi folks :-)
sorry for the intrusion.. I'd like buy new macbook pro (7.1 or new 8.1) and install debian. These package of ubuntu runs also in debian? Is there specific howto?
thanks!

Pol

---

### Post by agestrada on 2011-02-26
Hi all, 

I tried to build the driver and get the error 
```
include/common.h:30:27: error: mtdev-mapping.h: No such file or directory
```Then, I looked the thread and tried to install the package **libmtdev-dev** but I couldn't find it for Lucid, only Maverick and up. What else can I do to build the driver?

Thanks,

---

### Post by bradmurmz on 2011-02-27
@BlueDragonX ::

I will be happy to host an official page for this on my server. I would like to get some sort of official thing going so that we can get more people to switch to ubuntu on their macbooks. I am currently typing this from my macbook air 11" and love almost everything about it except the not so great multitouch support from the mactel repos... I also would like to learn more about building linux drivers as well, so I'm willing to help out any way that I can. PM me if you would like to get this going... I will do all the work involved in getting a site up.

---

### Post by wiznillyp on 2011-02-28
Anyone have any suggestions on how I can set the gestures like OSX?  Right now three-finger-up is "Back" and three-finger down is "forward". I want:[LIST]
[*]Three-finger-up: Home
[*]Three-finger-down: End
[*]Three-finger-left: Back
[*]Three-finger-right: Forward
[/LIST]

---

### Post by wartron on 2011-03-06
Does anyone here know where to change the source to bring the sensitivity down a little? The default is pretty high... thanks.

---

### Post by rafwes on 2011-03-12
Hello! 

I've installed 1.1 alpha and it works almost flawlessly. It seems much more accurate and aligned with default macos behavior than 1.0 rc2.

The only problem I faced so far is that the mouse will stop responding and halt the pointers movement. I have then to lift the finger and tap again to continue moving.

I suspected it could be something attributed to the thumb recognition since the pressure applied seemed to make a difference. By pressing harder it would loose focus easier than by moving lightly with the fingers.

Then I tried to change some of the settings under */etc/X11/xorg.conf* eg by adding* ThumbsSize "35"* to the InputClass to try to fix ist but this setting will prevent X from loading leaving me with a blank bash.

What am I doing wrong?

Thanks,
Raf

ps1: here is my config

```

Section "InputClass"
        MatchIsTouchpad "on"
        Identifier      "Touchpads"
        Driver          "multitouch"
EndSection
```

ps2: how can I revert to the old driver?

---

### Post by demheld on 2011-03-13
hello!
maybe you forgot to put option in front of it?
```

Option          "ThumbSize" "35"

```or maybe you should write ThumbSize instead of ThumbsSize (without the additional s )

for having the old driver to run just comment or delete the whole added Section "InputClass" in xorg.conf

---

### Post by rafwes on 2011-03-13
@demheld: Thank you, that did the trick! 

With some tinkering it gets very close to the behavior in MacOS. Here is my config file with some explanations:

```

Section "InputClass"
	MatchIsTouchpad "on"
	Identifier      "Touchpads"
	Driver          "multitouch"
	Option		"ThumbSize" "35"
	Option		"PalmSize" "55"
	Option		"ClickTime" "25"
	Option		"ScrollDistance" "300"
	Option		"TapDragEnable" "False"
EndSection

#ThumbSize 35        ->  Tracking isn't anymore mistaken as #thumbs
#PalmSize 50         ->  Prevents thumbclicks being recognized as palm
#ClickTime 25        ->  Makes taps more responsive
#ScrollDistance 300  ->  Scroll kicks in faster
#TapDragEnable False ->  Personal preference
```Two things are missing in my opinion:

1. Disable Trackpad while typing

I haven't found any option that will prevent accidental clicks while typing, this is hence the biggest problem so far.

2. Accelerated Scrolling

Scroll speed is could be accelerated as mouse tracking, default MacOS behavior would be ideal.


Anyhow, thank you all for these drivers and keep up the good work.

---

### Post by smoothlarryhughes on 2011-03-22
I was wondering if someone could points me in the right direction.  I am following all the steps on page 13, but when I get to step 5 to download the actual driver it does not work.  Where can I download an actual copy of the driver for install?  Once I get a copy of the drivers do I just use step 6 to install them?

I appreciate any help.

---

### Post by smoothlarryhughes on 2011-03-24
Is the bitmath site currently down?  I've been having trouble accessing it for the past 2 days to get the driver.  

Thanks all!

---

### Post by NiñoScript on 2011-03-24
Instead of downloading it with git (Step 05), try with [this one]("http://www.dev.fatalmachine.org/xf86-input-multitouch-1.1_alpha4.tar.gz") as seen on [page 34]("http://ubuntuforums.org/showthread.php?p=10447839#post10447839").

Instead of '~/multitouch' (Step 06), `cd` to the directory with the extracted files as explained on [page 35]("http://ubuntuforums.org/showthread.php?p=10485848#post10485848").

Instead of appending that to /etc/X11/xorg.conf (Step 07), try with:```
Section "InputClass"
	MatchIsTouchpad "on"
	Identifier      "Touchpads"
	Driver          "multitouch"
	Option		"ThumbSize"      "35"
	Option		"PalmSize"       "55"
	Option		"ClickTime"      "25"
	Option		"ScrollDistance" "300"
EndSection
``` as seen [above]("http://ubuntuforums.org/showthread.php?p=10557093#post10557093").

Hope that helps :)

---

### Post by kosumi68 on 2011-03-25
> **smoothlarryhughes said:**
> Is the bitmath site currently down?  I've been having trouble accessing it for the past 2 days to get the driver.  

Thanks all!

Just checked, it works as usual.

```

git clone http://bitmath.org/git/multitouch.git

```

There is also a package in ppa now.

---

### Post by kennethsime on 2011-03-25
So I've installed the drivers from the Mactel PPA via synaptic (terminal was not my friend today), and edited my xorg.conf , and rebooted. How do I actually enable the drivers? It doesn't seem to be working.

---

### Post by smoothlarryhughes on 2011-03-28
When I try to sudo make install after extracting the file I get the following error in the terminal. Can anyone help?  I downloaded and extracted [http://www.dev.fatalmachine.org/xf86-input-multitouch-1.1_alpha4.tar.gz](http://www.dev.fatalmachine.org/xf86-input-multitouch-1.1_alpha4.tar.gz) to /Downloads/mtouh

smoothlarryhughes@smoothlarryhughes:~/Downloads$ cd mtouh
smoothlarryhughes@smoothlarryhughes:~/Downloads/mtouh$ sudo make install
[sudo] password for smoothlarryhughes: 
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/capabilities.c -o obj/src/capabilities.o
In file included from include/capabilities.h:25,
                 from src/capabilities.c:22:
include/common.h:31: fatal error: mtdev-mapping.h: No such file or directory
compilation terminated.
make: *** [obj/src/capabilities.o] Error 1

Thanks!

---

### Post by pbhedlund on 2011-03-29
> **smoothlarryhughes said:**
> 
include/common.h:31: fatal error: mtdev-mapping.h: No such file or directory


Try "sudo apt-get install libmtdev-dev"

---

### Post by NiñoScript on 2011-03-29
OK, I think we **do** need an updated guide now.

so, we need to install these:
sudo apt-get install bcm5974-dkms git-core xserver-xorg-dev libmtdev-dev
right?

and, Kosumi said "There is also a package in ppa now", which one is it?

PD: I bought more ram, so now I just virtualize ubuntu when I need it, but that doesn't mean I don't want to help :)

---

### Post by lookitscook on 2011-03-31
great work guys. Just installed as per the instructions on page 13/36 on my macbook air 3.2 and it works fantastic. much smoother, easier clicking.

---

### Post by Aptorian on 2011-04-02
After upgrading to Natty the driver no longer works... pre-upgrade everything worked fine, but now my mouse will not move. When I try to compile BlueDragonX's version above I see the following error:

```
aptorian@Halcyon:~/Code/multitouch-1.1_alpha4$ cd ~/Downloads/multitouch-1.1_alpha4/
aptorian@Halcyon:~/Downloads/multitouch-1.1_alpha4$ make
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/capabilities.c -o obj/src/capabilities.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/hwstate.c -o obj/src/hwstate.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/mtstate.c -o obj/src/mtstate.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/gestures.c -o obj/src/gestures.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/mconfig.c -o obj/src/mconfig.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/mtouch.c -o obj/src/mtouch.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c src/trig.c -o obj/src/trig.o
gcc -Iinclude -I/usr/include/xorg -I/usr/include/pixman-1  -O3 -fPIC -c driver/multitouch.c -o obj/driver/multitouch.o
driver/multitouch.c:91:42: error: expected declaration specifiers or ‘...’ before ‘LocalDevicePtr’
driver/multitouch.c: In function ‘device_init’:
driver/multitouch.c:93:22: error: ‘local’ undeclared (first use in this function)
driver/multitouch.c:93:22: note: each undeclared identifier is reported only once for each function it appears in
driver/multitouch.c:143:8: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
/usr/include/xorg/xf86Xinput.h:151:23: note: declared here
driver/multitouch.c:151:8: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
/usr/include/xorg/xf86Xinput.h:151:23: note: declared here
driver/multitouch.c: At top level:
driver/multitouch.c:159:37: error: expected ‘)’ before ‘local’
driver/multitouch.c:175:38: error: expected ‘)’ before ‘local’
driver/multitouch.c:185:40: error: expected ‘)’ before ‘local’
driver/multitouch.c:190:44: error: expected ‘)’ before ‘local’
driver/multitouch.c:219:39: error: expected ‘)’ before ‘local’
driver/multitouch.c: In function ‘device_control’:
driver/multitouch.c:230:2: error: ‘LocalDevicePtr’ undeclared (first use in this function)
driver/multitouch.c:230:17: error: expected ‘;’ before ‘local’
driver/multitouch.c:234:27: error: ‘local’ undeclared (first use in this function)
driver/multitouch.c:234:3: error: too many arguments to function ‘device_init’
driver/multitouch.c:91:12: note: declared here
driver/multitouch.c: At top level:
driver/multitouch.c:251:49: error: expected declaration specifiers or ‘...’ before ‘IDevPtr’
driver/multitouch.c: In function ‘preinit’:
driver/multitouch.c:254:2: error: too many arguments to function ‘xf86AllocateInput’
/usr/include/xorg/xf86Xinput.h:163:14: note: declared here
driver/multitouch.c:261:16: error: ‘dev’ undeclared (first use in this function)
driver/multitouch.c:264:22: error: ‘read_input’ undeclared (first use in this function)
driver/multitouch.c:266:17: error: ‘XI86_POINTER_CAPABLE’ undeclared (first use in this function)
driver/multitouch.c:266:40: error: ‘XI86_SEND_DRAG_EVENTS’ undeclared (first use in this function)
driver/multitouch.c:267:7: error: ‘struct _InputInfoRec’ has no member named ‘conf_idev’
driver/multitouch.c:269:2: error: too many arguments to function ‘xf86CollectInputOptions’
/usr/include/xorg/xf86Xinput.h:185:23: note: declared here
driver/multitouch.c:276:18: error: ‘XI86_CONFIGURED’ undeclared (first use in this function)
driver/multitouch.c: At top level:
driver/multitouch.c:292:2: warning: initialization from incompatible pointer type
make: *** [obj/driver/multitouch.o] Error 1
aptorian@Halcyon:~/Downloads/multitouch-1.1_alpha4$
```

---

### Post by sauferkel on 2011-04-08
i used the configuration from the page 36....but the doubleclick is really heavy to do...is there anything i can change about?

---

### Post by BlueDragonX on 2011-04-08
> **Aptorian said:**
> After upgrading to Natty the driver no longer works...

Natty has a newer version of Xorg.  I've got to update the driver to work with it.  I'm updating X on my machines at the moment then I'll see what I can do.

I have a couple of features I intend to add to the driver, as well as rename it (not affiliated with the original developer, it's a fork after all).

A work in progress, as always.

---

### Post by buzzboy on 2011-04-10
EDIT: After a reboot the keyboard works fine. However when I ran the command I still cannot use the mouse. 
I tried this following the instructions on page 13. However, when I logged out and back in the mouse wouldn't work as it told me. But I couldn't get into terminal as most of my keyboard keys didn't work either.

---

### Post by buzzboy on 2011-04-11
Better question than my above. Being not but a wee noob I don't know how to reverse this so I can use my mouse again. Any help appreciated.

Figured it out. Still can't get touchpad to work though. Help much appreciated.

---

### Post by DarkTide on 2011-04-12
Has somebody else gotten it working in Lucid? How have you configured it?

---

### Post by BlueDragonX on 2011-04-14
Gentlemen!  I've made some progress on my fork of the driver.

Firstly, my code is now on github at [https://github.com/BlueDragonX/xf86-input-mtrack](https://github.com/BlueDragonX/xf86-input-mtrack).  To get your copy:

```

git clone git://github.com/BlueDragonX/xf86-input-mtrack.git

```

Secondly, my fork of the driver is now named xf86-input-mtrack.  The driver itself is referred to as mtrack in the configuration.  So:

```

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
EndSection

```

Thirdly, the trunk code at github works with Xorg 1.10, so you should be good for compiling on Natty.

Lastly, please report any issues to the issues tracker on github.

---

### Post by pbhedlund on 2011-04-15
> **BlueDragonX said:**
> Gentlemen!  I've made some progress on my fork of the driver.

Thank you. I have done some initial testing on my Macbook Air 3,2 running Natty and the driver works quite well.

---

### Post by BlueDragonX on 2011-04-15
> **pbhedlund said:**
> Thank you. I have done some initial testing on my Macbook Air 3,2 running Natty and the driver works quite well.

That's good to hear!  My Air 3,2 runs Gentoo, so I didn't actually get to test it against Natty.

Hopefully by the end of the day I'll have a Debian package and Gentoo ebuild available for download so people don't have to compile anymore.

---

### Post by BlueDragonX on 2011-04-15
Packages are now available for xf86-input-mtrack.  See my new thread at [http://ubuntuforums.org/showthread.php?p=10682051](http://ubuntuforums.org/showthread.php?p=10682051).

---

### Post by mikezackles on 2011-04-26
Thanks BlueDragonX!  Your fork works *much* better for me.  Thanks for documenting all the options too.  I've uploaded a package for Arch Linux here: [http://aur.archlinux.org/packages.php?ID=48505](http://aur.archlinux.org/packages.php?ID=48505)

---

### Post by BlueDragonX on 2011-04-27
> **mikezackles said:**
> Thanks BlueDragonX!  Your fork works *much* better for me.  Thanks for documenting all the options too.  I've uploaded a package for Arch Linux here: [http://aur.archlinux.org/packages.php?ID=48505](http://aur.archlinux.org/packages.php?ID=48505)

Thanks!  I added the (attributed) link in the other thread.

---

### Post by Jhinta on 2011-05-06
hi there so i have problem , how do i change (invert) xy and and maby axes?

---

### Post by BlueDragonX on 2011-05-06
> **Jhinta said:**
> hi there so i have problem , how do i change (invert) xy and and maby axes?

You don't.  Why would you want to?

---

### Post by Jhinta on 2011-05-06
> **BlueDragonX said:**
> You don't.  Why would you want to?

because i have my touch schreen working with this driver ( desire hd ubuntu)

[http://forum.xda-developers.com/showthread.php?t=1045910](http://forum.xda-developers.com/showthread.php?t=1045910)

---

### Post by BlueDragonX on 2011-05-06
> **Jhinta said:**
> because o have my touch schreen working with this driver ( desire hd ubuntu)

This is a trackpad driver, not a touchscreen driver. I will not be integrating any touchscreen features into this driver as it is only intended to support trackpads.

The code underneath the gesture recognition portion of the driver would be a good place to start if you want to create your own, though.

---

### Post by Jhinta on 2011-05-06
> **BlueDragonX said:**
> This is a trackpad driver, not a touchscreen driver. I will not be integrating any touchscreen features into this driver as it is only intended to support trackpads.

The code underneath the gesture recognition portion of the driver would be a good place to start if you want to create your own, though.

i know its a lot to ask but help :popcorn:

---

### Post by BlueDragonX on 2011-05-06
> **Jhinta said:**
> i know its a lot to ask but help :popcorn:

Asking nicely doesn't make it feasible. It just doesn't make any sense to built a monolithic touchpad/touchscreen driver.

Besides that, other people are already working on Ubuntu touchscreen support. Do some Googling.

If you want help, please open a new thread in the proper section. There are other people on the forums who are better able to help you with this.

---

### Post by Jhinta on 2011-05-06
> **BlueDragonX said:**
> Asking nicely doesn't make it feasible. It just doesn't make any sense to built a monolithic touchpad/touchscreen driver.

Besides that, other people are already working on Ubuntu touchscreen support. Do some Googling.

If you want help, please open a new thread in the proper section. There are other people on the forums who are better able to help you with this.

tnx anyway.

---

### Post by drunkmaster on 2011-06-13
Sorry for the lame question but I have configured synaptics driver (with two and three fingers tapping, scrolling etc) and want to have additional gestures like zooming and rotating, for example. Can I use your driver on top of synaptics? Or it's a replacement only without any configuration abilities?

---

### Post by BlueDragonX on 2011-06-13
This is a completely separate, stand-alone driver. You can not use the Synaptics driver and the mtrack driver on the same device.

The mtrack driver will only work on true multitouch devices which have kernel support.

---

### Post by skullmunky on 2012-04-02
the binaries link for Ubuntu is broken on github (dev.fatalmachine.org).

I tried getting the source and compiling but got this error:

```

configure.ac:21: error: must install xorg-macros 1.8 or later before running autoconf/autogen

```

I'm using 11.10.  

I installed xutils-dev but that didn't solve it. 

I also installed xorg-macros from source from X.org, but that didn't help either.  :confused:

---

### Post by Dr.Paneas on 2012-08-01
The Ubuntu binaries are broken.........

---

