---
title: "Two finger click transformation"
date: 2007-11-28
forum: Apple Intel Users
---

### Post by tehkain on 2007-11-28
Hey all I patched the xserver-xorg-input-synaptics driver with the patch here:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

It adds OSX like 'Place two fingers on trackpad and click button for secondary click' ability to the touchpad. Real nice patch. For everyone using a x86 I have a deb of the modified driver here:
[https://launchpad.net/awn-py-applets/trunk/3.0rc1/+download/xserver-xorg-input-synaptics_0.14.6-0ubuntu11_i386.deb](https://launchpad.net/awn-py-applets/trunk/3.0rc1/+download/xserver-xorg-input-synaptics_0.14.6-0ubuntu11_i386.deb)

You need to add 
```
Option "TwoFingerButton1" "2"
```
to your synaptic section of the xorg. After that you'll be able to right-click by placing two fingers on the trackpad and clicking.

---

### Post by cyberdork33 on 2007-11-28
very nice, this sounds like it will make some people happy.

---

### Post by peabody on 2007-11-28
This sounds interesting...if I understand the way you describe it, this makes it so that touching the pad in two places at the same time results in a right click?   Does tapping have to be enabled for this to work?  I really hate tap clicking.

---

### Post by tehkain on 2007-11-28
> **peabody said:**
> This sounds interesting...if I understand the way you describe it, this makes it so that touching the pad in two places at the same time results in a right click?   Does tapping have to be enabled for this to work?  I really hate tap clicking.

Ah no not exactly. it emulates the OS X option 'Place two fingers on trackpad and click button for secondary click'

---

### Post by peabody on 2007-11-28
oh, okay, I didn't see this was in the apple forum (randomly clicked it from the front page).

Still, good to know.  I have an old g4 ibook I may put Linux on someday.

---

### Post by volanin on 2007-11-28
I have modified the patch to better suit mac-users.
Now you have a single option for synaptics: **MultiFingerClick**
It has the following options:


**MultiFingerClick = 0**
Completely disable this function.

**MultiFingerClick = 1**
Place TWO fingers on the pad and then CLICK the button, you get a MIDDLE click.
Place THREE fingers on the pad and then CLICK the button, you get a RIGHT click.

**MultiFingerClick = 2** (The reverse)
Place TWO fingers on the pad and then CLICK the button, you get a RIGHT click.
Place THREE fingers on the pad and then CLICK the button, you get a MIDDLE click.


To make it even better, DISABLE tapclick:
```
Option          "MultiFingerClick"      "2"
Option          "TapButton1"            "0"
Option          "TapButton2"            "0"
Option          "TapButton3"            "0"
```

Patch and DEB attached!
:)

---

### Post by tehkain on 2007-11-28
Good stuff, I will try it when I get home.

---

### Post by cyberdork33 on 2007-11-28
> **peabody said:**
> oh, okay, I didn't see this was in the apple forum (randomly clicked it from the front page).

Still, good to know.  I have an old g4 ibook I may put Linux on someday.
This shouldn't be limited to Macs, any synaptics hardware (newer touchpads) that supports it should be able to use it.

---

### Post by volanin on 2007-11-29
Insomnia does wonders to human progress!
I made an update to the previous patch, to improve the feedback of the touchpad.


It is A LOT better than the previous one. The changelog:
[LIST][*]If **MultiFingerClick** is enabled, mouse movement while tapping with 2 or 3 fingers is disabled.
This makes the arrow stay still when you tap with multiple fingers, improving a lot the precision of the click.


[*]Many corrections to the behaviour of the mouse:
[LIST][*]If you tap the pad with multiple fingers, then click the button, and release the fingers, the middle/right
click will stay active until you release the button.


[*]If you are already holding the button for normal drag and then multitap, nothing will happen.[/LIST][/LIST]


The options are still the same as before.
For best results, and no interference from other functions, edit your xorg.conf and put these lines:

```
Option          "MultiFingerClick"      "1"
Option          "RTCornerButton"        "0"
Option          "RBCornerButton"        "0"
Option          "TapButton1"            "0"
Option          "TapButton2"            "0"
Option          "TapButton3"            "0"
```


Everything's attached. Enjoy!
:)

---

### Post by tehkain on 2007-11-29
Doesnt that disable two finger scrolling?

---

### Post by volanin on 2007-11-29
[WRONG]Yes, it does.[/WRONG]
Well, I can separate this in two options: MultiFingerClick and MultiFingerLock.
So that it does not lose any functionality. Doing that... hold on!
:)

EDIT: No, it DOES NOT DISABLE two-finger scrolling!
But the two separate options will be kept anyway.

---

### Post by volanin on 2007-11-29
OK!
That's probably the final version.
*(Although I always regret when I say this...)*

The option MultiFingerClick has been _renamed_ to **MultiFingerButton** to look more alike the other
options in synaptics configuration. Also, another option has been implemented: **MultiFingerLock**.
They do the following:


[LIST][*]**MultiFingerButton = 0**: *(The default)*
Completely disable this function.


[*]**MultiFingerButton = 1**:
Place TWO fingers on the pad and then CLICK the button, you get a MIDDLE click.
Place THREE fingers on the pad and then CLICK the button, you get a RIGHT click.


[*]**MultiFingerButton = 2**: *(The reverse)*
Place TWO fingers on the pad and then CLICK the button, you get a RIGHT click.
Place THREE fingers on the pad and then CLICK the button, you get a MIDDLE click.[/LIST]


[LIST][*]**MultiFingerLock = 0**: *(The default)*
Completely disable this function.


[*]**MultiFingerLock = 1**:
This will DISABLE the mouse movements if TWO or THREE fingers are on the pad.
This drastically improves the precision of the CLICKS above. (EDIT: and does NOT disable two-finger scrolling!)[/LIST]

To make best use of these options, also disable tap-clicking and corner-clicking.
I recommend the configuration below:

```
Option          "MultiFingerButton"     "2"
Option          "MultiFingerLock"       "1"
Option          "RTCornerButton"        "0"
Option          "RBCornerButton"        "0"
Option          "TapButton1"            "0"
Option          "TapButton2"            "0"
Option          "TapButton3"            "0"
```


The patch and the DEB are attached, as usual.
Enjoy and please, give feedback!
:)

---

### Post by cyberdork33 on 2007-11-29
> **volanin said:**
> 
[LIST]
[*]**MultiFingerButton = 0**: *(The default)*
Completely disable this function.
[*]**MultiFingerButton = 1**:
Place TWO fingers on the pad and then CLICK the button, you get a MIDDLE click.
Place THREE fingers on the pad and then CLICK the button, you get a RIGHT click.
[*]**MultiFingerButton = 2**: *(The reverse)*
Place TWO fingers on the pad and then CLICK the button, you get a RIGHT click.
Place THREE fingers on the pad and then CLICK the button, you get a MIDDLE click.[/LIST]I know you are probably tired of changes, but to really be consistent, shouldn't the form be something like: MultiFingerButton2 = 2 (button2, middle-click = 2 fingers, etc)

Also, you might want to submit this to the mactel folks, they might be interested in it, and if it gets in there, it will likely get into other kernels quickly.

---

### Post by volanin on 2007-11-29
Stupid-mode on!
I didn't understand anything about your suggestion!
:)

Are you suggesting me to implement a MultiFingerButton2 as well?
What would it do?


> Also, you might want to submit this to the mactel folks, they might be interested in it, and if it gets in there, it will likely get into other kernels quickly.

How do I do this? Have any ideas?
The mactel homepage has no contact link or bugzilla.

---

### Post by cyberdork33 on 2007-11-29
> **volanin said:**
> Stupid-mode on!
I didn't understand anything about your suggestion!
:)

Ok, I will try to use examples of existing options in synaptic... Multi-Finger Tapping specifically...

[quote=synaptics man page]```
       TapButton1 (Integer)
              Which mouse button is reported on a non-corner  one-finger  tap.
              Set to 0 to disable.

       TapButton2 (Integer)
              Which  mouse  button is reported on a non-corner two-finger tap.
              Set to 0 to disable.

       TapButton3 (Integer)
              Which mouse button is reported on a non-corner three-finger tap.
              Set to 0 to disable.
```[/quote]

In the same way:
MultiFingerButton1 would have an integer value to depict which button should be reported if you hold one finger on the trackpad and clicked, 
MultiFingerButton2 would have an integer value to depict which button should be reported if you hold two fingers on the trackpad and clicked,
MultiFingerButton3 would have an integer value to depict which button should be reported if you hold three fingers on the trackpad and clicked,
etc

> How do I do this? Have any ideas?
The mactel homepage has no contact link or bugzilla.I believe you just have to branch the mactel patches svn and add patches there... if this is a kernel patch....

you can probably join the mactel mailing list and ask about it there for more info.

---

### Post by volanin on 2007-11-29
> **cyberdork33 said:**
> In the same way:
MultiFingerButton1 would have an integer value to depict which button should be reported if you hold one finger on the trackpad and clicked, 
MultiFingerButton2 would have an integer value to depict which button should be reported if you hold two fingers on the trackpad and clicked,
MultiFingerButton3 would have an integer value to depict which button should be reported if you hold three fingers on the trackpad and clicked

Ah!
Great observation!
I might implement that later. It's not too hard and it's really more consistent.
:)


> I believe you just have to branch the mactel patches svn and add patches there... if this is a kernel patch....
you can probably join the mactel mailing list and ask about it there for more info.

Nah, no kernel. Just a small patch to the synaptics driver in X.org
I'll see about the mailing list, thanks!

---

### Post by cyberdork33 on 2007-11-29
> **volanin said:**
> Ah!
Great observation!
I might implement that later. It's not too hard and it's really more consistent.more versatile too, since, for whatever reason, I could make two-finger clicks do mouse button 7 or something if I wanted.

> Nah, no kernel. Just a small patch to the synaptics driver in X.org
I'll see about the mailing list, thanks! ah, got it, then you would want to submit to the xorg folks likely.
[http://www.x.org/wiki/#head-bf2236f6d98c143f032c442735cfcca0a49ee6d2](http://www.x.org/wiki/#head-bf2236f6d98c143f032c442735cfcca0a49ee6d2)

---

### Post by volanin on 2007-11-30
> **cyberdork33 said:**
> more versatile too, since, for whatever reason, I could make two-finger clicks do mouse button 7 or something if I wanted.

This has another problem.
It I implement MultiFingerButton{1,2,3}, this will work only for the LEFT button.
While for macs this is perfectly ok, for generic touchpads it's quite restrictive.

The "right" thing to do would be to implement this with the possibility of affecting any button.
But, some touchpads have up to 6 buttons! So I would have to create a LOT of options!

Like: MultiFinger1Button1, MultiFinger2Button1, MultiFinger3Button1... then MultiFinger1Button2...

Not good... not good.
Do you have a better idea?
The arguments to these options can only be a single number.
:)

---

### Post by cyberdork33 on 2007-11-30
> **volanin said:**
> This has another problem.
It I implement MultiFingerButton{1,2,3}, this will work only for the LEFT button.
While for macs this is perfectly ok, for generic touchpads it's quite restrictive.

The "right" thing to do would be to implement this with the possibility of affecting any button.
But, some touchpads have up to 6 buttons! So I would have to create a LOT of options!

Like: MultiFinger1Button1, MultiFinger2Button1, MultiFinger3Button1... then MultiFinger1Button2...

Not good... not good.
Do you have a better idea?
The arguments to these options can only be a single number.
:)

hmm... well, just assuming I did have a touchpad with 7 buttons, i wouldn't want to use this option to make the 'left click' do something different when i could just use the actual button that does it. ;)

No, I think that will be too cumbersome. We really have 3 variables: 1 - The 'real' button, 2 - the number of touched fingers, 3 - the button 'value' (fake button) Maybe it would be better to have the Option named MultiFinger1 (like you already have) and then pass two arguments, 1 as the real button, 2 as the new value...

MultiFinger2 = "1" "3" would mean that using 2 fingers and clicking button 1, results in the button3 signal. (i.e. 2-finger click to right click). Of course, on a Mac, the first argument would always be "1" (because there are no other 'real' buttons), but on other hardware, this could be 2,3,4, etc depending on the number of buttons that you have.

MultiFingerX = "Y" "Z"[LIST]
[*]X = Number of Fingers
[*]Y = 'Real' Button number
[*]Z = 'Reported' Button Number[/LIST]**EDIT**: Nevermind, saw your last line...
Is this a limit of the driver? There are other options in xorg that can take two values... Maybe it would be best to just patch for the left mouse button only, then let the xorg community expand it if they want.

---

### Post by WaySensei on 2007-12-26
This may be a stupid question...but I need to ask it...how do I apply the patch? I have extracted the archive and I just have a text document with the source code...what do I do next?

---

### Post by p0rtlandcubsfan on 2007-12-31
this doesn't work with anything except an ibook g4

---

### Post by tehkain on 2007-12-31
That is entirely false. I am using my package currently on my macbook c2d

---

### Post by cyberdork33 on 2008-01-02
> **p0rtlandcubsfan said:**
> this doesn't work with anything except an ibook g4

It was made specifically for Intel Macs, so if anything, it would work with them and not the G4 iBooks.

---

### Post by FunnyLookinHat on 2008-01-07
Any chance someone could post a amd64 compatible build of this package?  The newest macbooks are running on Core2 Duos and work great with the AMD64 version of ubuntu, so it would be nice to have this supported on that architecture as well.  : )

---

### Post by cyberdork33 on 2008-01-07
> **FunnyLookinHat said:**
> Any chance someone could post a amd64 compatible build of this package?  The newest macbooks are running on Core2 Duos and work great with the AMD64 version of ubuntu, so it would be nice to have this supported on that architecture as well.  : )
I don't think so, but the patch is posted so you should be able to compile.

---

### Post by Katjum on 2008-01-08
> **cyberdork33 said:**
> I don't think so, but the patch is posted so you should be able to compile.

This may be a dumb question (I'm new at this), but how exactly do you use this patch? (What do I need to download? How do I apply the patch?, etc.) Like FunnyLookinHat, I also have the AMD64 version of Ubuntu.

Thanks! :)

---

### Post by Katjum on 2008-01-13
> **Katjum said:**
> This may be a dumb question (I'm new at this), but how exactly do you use this patch? (What do I need to download? How do I apply the patch?, etc.) Like FunnyLookinHat, I also have the AMD64 version of Ubuntu.

Thanks! :)

I'm still looking for help if anyone knows how.

Thanks! :)

---

### Post by tuwe on 2008-01-17
> **Katjum said:**
> I'm still looking for help if anyone knows how.

Thanks! :)

EDIT: ok here's what i did:

create a working directory and get the synaptics driver sources:
```
mkdir ~/xserver-xorg-input-synaptics
cd ~/xserver-xorg-input-synaptics
apt-get source xserver-xorg-input-synaptics
```

download the latest patch from page 2 of this thread, save it to ~/xserver-xorg-input-synaptics,
unpack the patch and apply it:
```
gunzip xserver-xorg-input-synaptics-multifinger.patch.gz
cd xserver-xorg-input-synaptics-0.14.6/
patch -p1 < ../xserver-xorg-input-synaptics-multifinger.patch
```

compile it with
```
make
```
and create a debian package
```
sudo checkinstall -D
```

enter a reasonable description, e.g.: "Synaptics TouchPad driver for X.Org server (Two finger click transformation)" and review things like maintainer, name, etc., although everything should be ok.
Checkinstall will install the package for you.

do not forget to edit xorg.conf

hope this helps

i attached my deb for amd64, please tell me if it works for you too, thank you! (wow, my first deb package :))

---

### Post by Katjum on 2008-01-17
Thank you so much! Your deb package works for me too! :)

---

### Post by tuwe on 2008-03-08
Hi there, here's a package for hardy amd64.

---

### Post by cyberdork33 on 2008-03-08
has anyone submitted these patches to synaptics?

---

### Post by erktrek on 2008-03-10
These forums (and the people frequenting them) are excellent..

I did try to apply the patch against the most recent synaptic xorg release but got patch/compile errors (and am not experienced enough to nail those down) so did a manual install using "dpkg -i xxxx.deb". That appeared to do the trick. Things are now working great! Yeah!

... Now hopefully I didn't screw things up too badly by regressing the synaptic xorg version - but I assume that is the advantage of a "modular" Xorg..

Hey thanks again to all!

:guitar:

---

### Post by tuwe on 2008-03-12
> **cyberdork33 said:**
> has anyone submitted these patches to synaptics?

i don't think so, but i just tried to create a proper patch. not sure if i had success, though. could anyone review it? it is for the xserver-xorg-input-synaptics found in hardy as of today.

thanks.

---

### Post by wdahab on 2008-04-21
> **tuwe said:**
> i don't think so, but i just tried to create a proper patch. not sure if i had success, though. could anyone review it? it is for the xserver-xorg-input-synaptics found in hardy as of today.

thanks.

The patch fits perfectly, and on the same version of synaptics you used, in Hardy RC, but it isn't actually functioning. I'm using MB Core 2 Duo, 32bit. Were some of your edits to the original patch 64bit specific perhaps? I suppose, once Hardy actually goes live in a few days, there will perhaps be a lot more interest in getting this great feature (thanks for your work guys!) working as easily on Hardy as it was on Gutsy.

If anyone gets this to work nicely for x86, please post how (if you did anything special) and/or post a deb.

Also, for anyone attempting to patch/compile yourself and getting errors, you may find success by installing a few dev packages packages.

```
sudo apt-get install x-dev libx11-dev libxext-dev
```

---

### Post by shoponline on 2008-04-22
Hello! welcome to our website; [http://www.newnike-shoes.com](http://www.newnike-shoes.com)
we can supply low price with high quality products.You can view our website for the details. 
Thanks for your reading , pls email us if u have any questions about business . We hope that will make a long&great business with you in future.
Your satisfactions,Our pursuit!
Please Email me to get discount!!
website: [http://newnike-shoes.com](http://newnike-shoes.com)
MSN: [email]newnike-shoes@hotmail.com[/email] 
YAHOO: [email]newnike-shoes@yahoo.com.cn[/email]  
or E-mail:newnike.shoes100@gmail.com
Best regards

---

### Post by Who on 2008-04-22
> **wdahab said:**
> The patch fits perfectly, and on the same version of synaptics you used, in Hardy RC, but it isn't actually functioning. I'm using MB Core 2 Duo, 32bit. Were some of your edits to the original patch 64bit specific perhaps? I suppose, once Hardy actually goes live in a few days, there will perhaps be a lot more interest in getting this great feature (thanks for your work guys!) working as easily on Hardy as it was on Gutsy.

If anyone gets this to work nicely for x86, please post how (if you did anything special) and/or post a deb.

Also, for anyone attempting to patch/compile yourself and getting errors, you may find success by installing a few dev packages packages.

```
sudo apt-get install x-dev libx11-dev libxext-dev
```

Is any of this enabled by default, because I am _sure_ that I had two fingers + button 1 --> Button 3 working without patching

Admittedly, I can't make it work now, so maybe I was dreaming :S?

Any ideas?

---

### Post by NEI on 2008-05-14
Any news on this one for Hardy Final? I am really interested in a package. Thanks!

---

### Post by cyberdork33 on 2008-05-14
> **NEI said:**
> Any news on this one for Hardy Final? I am really interested in a package. Thanks!
Please post in the new Apple forum. There is a new thread on this here:
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---

### Post by NEI on 2008-05-15
Wow, thanks for the quick reply! Will try it this evening. :-)

---

