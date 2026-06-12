---
title: "Alternative way to middle/right mouse-click!"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by volanin on 2008-05-11
I have patched and recompiled the synaptics driver in Hardy Heron to
make it more enjoyable to use the mousepad while using the macbook.
This package below add the option MultiFingerButton to synaptics.

Install it, and add this option to the InputDevice Section in your
xorg.conf, just like this:

```
	Option		"MultiFingerButton"	"1"
```
or
```
	Option		"MultiFingerButton"	"2"
```

With the value 1, you get middle-clicking if you click the button while
resting two fingers on the mousepad, and right-clicking while resting
three fingers.

With the value 2, it reverses, and you get right-clicking if you click
while resting two fingers on the mousepad, and middle-clicking while
resting three fingers. This is the behaviour in MacOSX.


Besides this, it makes the mouse arrow more stable:
If you put two fingers on the mousepad and release only one, the mouse
arrow moves. This is the default behaviour in Linux and Windows, but in
MacOSX, the mouse arrow stays put, and in my personal opinion, this is
a much better behaviour. This patch makes it behave just like MacOSX.


Try it out, and give your opinion.
If you don't like it, you can always revert to the default Ubuntu package!
:)


**[UPDATE: 12-MAY-2008]**
As requested, now I have built packages for both 32 and 64-bit!
The source code is also included for your pleasure!


**[UPDATE2: 18-MAY-2008]**
By invitation of cyberdork33, I am now part of the mactel-support PPA!
So you can have these packages automatically updated from now on.
Add these lines to your */etc/apt/sources.list*:

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```
And your synaptics driver will be auto-updated. Be aware that you still
need to add the MultiFingerButton lines above to your */etc/X11/xorg.conf*


**_ATTENTION_**: If you have previously manually-installed the packages in this
post, and you want to use the auto-update feature of mactel-support PPA,
you will have to force a reinstall of the packages attached below.

They are the very same packages from before, but the packages previously
posted here didn't follow the standard ubuntu version numbering system
and will never be updated.

To force-install a package, download the corresponding package below and
type this command:
```
sudo dpkg -i [PACKAGE_DEB_FILE]
```

---

---

### Post by sunbird on 2008-05-11
I'm interested, but running 64-bit. Any chance you'll do a version for 64-bit?

---

### Post by volanin on 2008-05-11
> **sunbird said:**
> I'm interested, but running 64-bit. Any chance you'll do a version for 64-bit?

I had it, but since 64-bit only gave me trouble, I reinstalled 32-bit
and deleted it... silly me!

I can compile it from the LiveCD, so it should be no problem.
Check it out here tomorrow!
:)

---

### Post by cyberdork33 on 2008-05-11
volanin, it would be best if you can get your source uploaded to the mactel-support ppa, then people can install it normally from there. Additionally, it should build for all the hardware types.

---

### Post by volanin on 2008-05-12
[QUOTE=sunbird]I'm interested, but running 64-bit. Any chance you'll do a version for 64-bit?[/QUOTE]

There you have it!
The link to it is in the first post.
Use it and report your experience here please!


[QUOTE=cyberdork33]volanin, it would be best if you can get your source uploaded to the mactel-support ppa, then people can install it normally from there. Additionally, it should build for all the hardware types.[/QUOTE]

Well, I didn't even know there was a mactel ppa!
Just tell me how I get in touch with the maintainer!
The patch is also included now, and it's very non-intrusive.
Compiling it for every platform should be no problem at all.
:)

---

### Post by cyberdork33 on 2008-05-12
> **volanin said:**
> There you have it!
The link to it is in the first post.
Use it and report your experience here please!




Well, I didn't even know there was a mactel ppa!
Just tell me how I get in touch with the maintainer!
The patch is also included now, and it's very non-intrusive.
Compiling it for every platform should be no problem at all.
:)
Request to join the Mactel-Support Team and I will approve you:
[https://edge.launchpad.net/~mactel-support](https://edge.launchpad.net/~mactel-support)

---

### Post by russo.mic on 2008-05-12
So,  synclient and syndaemon don't work anymore.  Still, I might roll with it like this for a bit, as I don't really need syndaemon if tapping is disabled. (tapping without the button that is).  

I love this feature, and it would be great if the driver would work with synclient and syndaemon.  

Thanks a bundle!

Russo

---

### Post by volanin on 2008-05-13
[QUOTE=russo.mic]So,  synclient and syndaemon don't work anymore.  Still, I might roll with it like this for a bit, as I don't really need syndaemon if tapping is disabled. (tapping without the button that is).  

I love this feature, and it would be great if the driver would work with synclient and syndaemon.  
Thanks a bundle!
Russo[/QUOTE]

Hmmmm...
Synclient and syndaemon work beautifully here.
Indeed, the patch does NOT touch their code at all.
Would you mind trying again?
:)

[QUOTE=cyberdork33]Request to join the Mactel-Support Team and I will approve you:
[https://edge.launchpad.net/~mactel-support](https://edge.launchpad.net/~mactel-support)[/QUOTE]

Request made!
:)

---

### Post by cyberdork33 on 2008-05-13
> **volanin said:**
> Request made!
:)
and approved.

Just as a reference in this new thread, the old discussion for this is here:
http://ubuntuforums.org/showthread.php?t=626112

---

### Post by issih on 2008-05-14
Thanks for this, its exactly what I was looking for, I can't stand tapping the pad for a click in any form, its no where near positive enough for my liking

IMHO with the large button, and this method of getting a right click, the macbook's touchpad is far more usable than any other device

Thanks again

---

### Post by sunbird on 2008-05-15
> **volanin said:**
> There you have it!
The link to it is in the first post.
Use it and report your experience here please!

Works great! Thanks for this. I hope that you can get it incorporated upstream as I cannot stand tapping on my touchpad (too many years in OS X I think). 

Mouse keys works for me but this is much more convenient! 

Nicely done!

---

### Post by dustynus on 2008-05-15
This is awesome, been looking for a fix on this for a few months now. Trackpad is now PERFECT in my opinion
:)

Thanks alot :guitar:

---

### Post by tehkain on 2008-05-15
Volanin nice patch! I updated the original one by Douglas Mayle for x.7 but I am glad you got this one up and running as it seems to work better and avoids mouse movement while clicking

---

### Post by skiwithpete on 2008-05-15
when using this deb, is the line(s) shown in the original post all I have to use, or do I need to further edit Xorg.conf as I had with other previous synaptics package versions?

And if so can you paste the best code to put into xorg.conf to accompany this deb? 

Cheers,

P

---

### Post by volanin on 2008-05-15
[QUOTE=issih]IMHO with the large button, and this method of getting a right click, the macbook's touchpad is far more usable than any other device[/QUOTE]

I totally agree with you there.
Even the two-button mousepads seem ackward after this!


[QUOTE=issih]Thanks for this, its exactly what I was looking for, I can't stand tapping the pad for a click in any form, its no where near positive enough for my liking[/QUOTE]
[QUOTE=sunbird]Nicely done![/QUOTE]
[QUOTE=dustynus]This is awesome, been looking for a fix on this for a few months now. Trackpad is now PERFECT in my opinion[/QUOTE]

Thank you a lot!
:)


[QUOTE=tehkain]Volanin nice patch! I updated the original one by Douglas Mayle for x.7 but I am glad you got this one up and running as it seems to work better and avoids mouse movement while clicking[/QUOTE]

Yes, I remember when you first posted this patch for Gutsy.
It was all I was looking for, but the arrow moving when you were going to
click something just pissed me off! So I made this patch, which is basically
a simplification of your Douglas Mayle's implementation, with the arrow
movement-locking additions.

Thank you a lot for taking the initiative of posting your deb here!
:)

---

### Post by volanin on 2008-05-15
[QUOTE=cyberdork33]and approved.[/QUOTE]

Thank you!
I am going to post this patch there this weekend.
:)


[QUOTE=skiwithpete]when using this deb, is the line(s) shown in the original post all I have to use, or do I need to further edit Xorg.conf as I had with other previous synaptics package versions?
And if so can you paste the best code to put into xorg.conf to accompany this deb?[/QUOTE]

The minimum xorg.conf to use this patch is something like this.
You should _merge it_ with your current xorg.conf setup.
Pay attention to the Section and Identifier names.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SendCoreEvents"	"true"
	Option		"MultiFingerButton"	"1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"Synaptics Touchpad"
EndSection
```

The MultiFingerButton value can be 1 or 2 depending of your taste.
I have found my perfect synaptics setup after a lot of experimentation.
For the macbook 3rd generation, my setup for synaptics is this:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SendCoreEvents"	"true"
	Option		"SHMConfig"		"on"

	Option		"MinSpeed"		"0.5"
	Option		"MaxSpeed"		"3.0"
	Option		"AccelFactor"		"0.15"
	Option		"FingerHigh"		"25"
	Option		"FingerLow"		"15"

	Option		"MultiFingerButton"	"1"
	Option		"HorizEdgeScroll"	"0"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"TapButton1"		"0"
	Option		"TapButton2"		"0"
	Option		"TapButton3"		"0"
EndSection
```

Enjoy!
:)

---

### Post by skiwithpete on 2008-05-16
Thanks volanin,

I have Macbook 4,1 this is the modified xorg.conf that I'm using with the modified synaptic driver from the first post.

It lets me do 2-finger scrolling in Firefox too.

But it jumps up a little just before it lets me scroll down.  Does anyone have any suggestions for change to it to stop this little jump?

EDIT: Actually, I can't 2/3 finger right click anymore as it makes the page jump, as I described above. - so I've had to comment out the bottom 4 lines.

P

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
	
	Option		"MinSpeed"		"0.5"
	Option		"MaxSpeed"		"3.0"
	Option		"AccelFactor"		"0.15"
	Option		"FingerHigh"		"25"
	Option		"FingerLow"		"15"

	Option		"MultiFingerButton"	"2"
	Option		"HorizEdgeScroll"	"0"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"TapButton1"		"0"
	Option		"TapButton2"		"0"
	Option		"TapButton3"		"0"
	Option		"VertTwoFingerScroll"   "True"
	Option		"HorizTwoFingerScroll"  "True"
	Option 		"VertScrollDelta"       "25"
	Option 		"HorizScrollDelta"      "30"

EndSection
```

---

### Post by volanin on 2008-05-18
Synaptics packages upload to the mactel-support PPA!
Check the first post again and enjoy!
:)


> But it jumps up a little just before it lets me scroll down. Does anyone have any suggestions for change to it to stop this little jump?

EDIT: Actually, I can't 2/3 finger right click anymore as it makes the page jump, as I described above. - so I've had to comment out the bottom 4 lines.

That's a problem that existed in the original Douglas Mayle's patch compiled
by thekain. Whenever you were going to place two or three finger in the pad,
the mouse arrow moved a little. That behaviour is fixed in my patch.

BUT, if you are going to use two-finger scrolling, I simply cannot lock the
arrow movement, or your page would not scroll at all. So you still experience
this behaviour, not by a small movement of the arrow, but by a small scrolling
of the page.

I will think of a solution to this problem and update the packages.
Stay tuned!
:)

---

### Post by cyberdork33 on 2008-05-18
> **volanin said:**
> Synaptics packages upload to the mactel-support PPA!
Check the first post again and enjoy!
:)
There is also a "mactel-support" project in launchpad (owned by the mactel-support team). It may be beneficial to upload sources there so that other can work on it too. We hadn't used it before, but it is just a thought. (we could also just create a sourceforge page or use bzr).

---

### Post by skiwithpete on 2008-05-18
Volanin,

Just thinking out loud about the two finger scroll jumps: 

1) you could put a tiny delay on scroll when second finger is placed to avoid the jumps.
2) you could devise some kind of 'ignore mouse position movements when 2nd finger applied'

Just some little ideas anyways.

P

---

### Post by hanzomon4 on 2008-05-19
Thank you so much!!!!

---

### Post by russo.mic on 2008-05-19
Both my syndaemon and synclient say incompadible driver version...

I have found that with this feature I don't really care, but I can see how some would.  

Thanks again!

Russo

---

### Post by skiwithpete on 2008-05-19
Just thought I'd make a note, that when I suspend my 4,1 my mouse functionality ceases. I can't 2/3 finger click, nor scroll.

I currently can't hibernate (don't know why yet), but like I say, suspend ruins the mouse.  Is that a problem on my local machine, or a prob for everyone on this .deb?

P

---

### Post by volanin on 2008-05-19
> Both my syndaemon and synclient say incompadible driver version...
I have found that with this feature I don't really care, but I can see how some would.
Thanks again!
Russo

Nah, it is me that should be thanking you for taking your time to report
your experiences. But this is a very strange bug, since both synclient
and syndaemon functionalities are not touched at all by this patch.
As I said, it works here flawlessly. One last thing:
What does *synclient -V* prints?
Here it prints version 0.14.6.


> Just thought I'd make a note, that when I suspend my 4,1 my mouse functionality ceases. I can't 2/3 finger click, nor scroll.

I currently can't hibernate (don't know why yet), but like I say, suspend ruins the mouse. Is that a problem on my local machine, or a prob for everyone on this .deb?

I don't think this has anything to do with this patch.
It does not touch the initialization or suspend/resume routines at all.
You will probably have this same bug with the original hardy DEB, but
since we can never be sure, and since I want to provide you with a
great experience, could you revert to the original hardy package
and re-test this? Thank you a lot!
:)

---

### Post by skiwithpete on 2008-05-20
Volanin,

I know this exposes me as a total newb, but I don't even know how to roll back to the old package... :(

---

### Post by volanin on 2008-05-20
> Volanin,
I know this exposes me as a total newb, but I don't even know how to roll back to the old package...

Hahahaha! That's ok!
You just have to append the desired version after the package name.
To downgrade the package to the original ubuntu version, try this:

```
sudo aptitude install xserver-xorg-input-synaptics=0.14.7~git20070706-1ubuntu4
```

After downgrading, your system will automatically tell you that
there are upgrades available. Just ignore them and test the
suspend as you did previously!
:)

---

### Post by skiwithpete on 2008-05-21
volanin,

I did the downgrade, then suspend, then found that the 2/3 click didn't work.  But wait, the 2/3 click button doesn't work on the old driver anyways!!!

But, when I tested the old scroll (right hand side of pad) that had stopped working with the old driver too.  So - you are correct that it is not your new .deb package to blame.

All I need now is the two finger scroll without the screen jump, and I'll be a happy camper (until someone realises that we can't pinch yet either).

P

---

### Post by saidmontiel on 2008-05-21
Friend, I've been trying to install the package you developed, but I can not do it. Im totally new with the ubuntu environment, I've never used a Linux system before... so that might be the problem in the first place. Could you guide me to do a complete installation of the package? I'd really appreciate that.

I downloaded all the files, I don't know how to install packages, so i just double-clicked on the file corresponding to my architecture,still it says "Wrong architecture 'i386'" what does it mean? and what is that ubuntu patch?

Thank you in advance friend.

Well i think I'm helpless with this specifically issue... the wrong architecture problem is generated because I have a PPC processor... buuu...

Anyway, if you can recommend an alternative method I'd be glad to try it.

---

### Post by skiwithpete on 2008-05-24
Hey volanin

I have been using your .deb since it came out and I've noticed that the distance my fingers have to be from one another to register a 3 finger touch is quite far apart.

Is there a setting to change that space between the fingers or is that set in the hardware?

Cheeers,

P

PS How goes the 2 finger scrolling?

---

### Post by Halsnalle on 2008-06-11
This is strange: I have middle/right click set up as per option 1 (right-click = three fingers), but I wanted to change it to option 2. Now, when I opened my xorg.conf, the option MultiFingerButton is not there... and adding it setting the option to 2 does not change anything. But I must have added it in the first place to get three-finger right-click working, right? How come I can't change the option?

Any suggestions for a confused Ubuntu newbie?

---

### Post by cyberdork33 on 2008-06-11
> **Halsnalle said:**
> This is strange: I have middle/right click set up as per option 1 (right-click = three fingers), but I wanted to change it to option 2. Now, when I opened my xorg.conf, the option MultiFingerButton is not there... and adding it setting the option to 2 does not change anything. But I must have added it in the first place to get three-finger right-click working, right? How come I can't change the option?

Any suggestions for a confused Ubuntu newbie?
Point of clarification... you are talking about tapping with three fingers, or putting three fingers on the pad, and clicking the button?

---

### Post by Halsnalle on 2008-06-12
> **cyberdork33 said:**
> Point of clarification... you are talking about (A) tapping with three fingers, or (B) putting three fingers on the pad, and clicking the button?

I'm talking about (A). For right-clicking, I'd like to tap two fingers instead of two (without having to click the button). Wrong thread? ;)

---

### Post by cyberdork33 on 2008-06-12
> **Halsnalle said:**
> I'm talking about (A). For right-clicking, I'd like to tap two fingers instead of two (without having to click the button). Wrong thread? ;)
yep, this is a patch for performing (B).

Check the synaptics man page for all the default options available:
```
man synaptics
```

You are specifically interested in the "TapButton#" options
[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

---

### Post by dustynus on 2008-06-16
How do you go about requesting that this be added to the ubuntu macbook wiki, because I think this deserves to be on there.

:guitar:

---

### Post by cyberdork33 on 2008-06-16
> **dustynus said:**
> How do you go about requesting that this be added to the ubuntu macbook wiki, because I think this deserves to be on there.

:guitar:

You don't need to request, you can add it yourself. This is really just an optional tweak which is probably why it hasn't been included already.

---

### Post by kosumi68 on 2008-06-26
This feature is great, but here is a strange thing:

1. Select portion of text in a window.

2. Paste it into something using the two-finger-and-click function.

3. Scroll in the window using the two-finger scroll function.

4. Click the button.

In my setting (MBA with the new bcm5974 driver), clicking the button at 4) pastes the text a second time. Does this happen to you to?

UPDATE: Please disregard, this was due to a bug in the bcm5974 driver, it works fine now. Sorry :)

---

### Post by volanin on 2008-07-01
I been absent from this forum for quite a long time so let me just clarify
some points raised in the last posts:


[QUOTE=skiwithpete]Just thinking out loud about the two finger scroll jumps:

1) you could put a tiny delay on scroll when second finger is placed to avoid the jumps.
2) you could devise some kind of 'ignore mouse position movements when 2nd finger applied'

Just some little ideas anyways.[/QUOTE]


Unfortunatelly, I personally consider the synaptics source code to be quite
confusing. It's full of huge functions that do a lot of things inside them,
and many times changing one thing breaks another...

I have tried all these ideas (and a couple more), but I cannot get the
mouse pointer to behave when two-finger scroll is used. I will keep on
trying, but recently I have been very short on time...


[QUOTE=skiwithpete]I have been using your .deb since it came out and I've noticed that the distance my fingers have to be from one another to register a 3 finger touch is quite far apart.

Is there a setting to change that space between the fingers or is that set in the hardware?[/QUOTE]


I honestly don't know.
In my system, I can put both fingers very close togheter and it still works
nicely. The patch does not touch any thing related to finger-spacing!
:)

---

### Post by midtown on 2008-07-19
> **volanin said:**
> I have tried all these ideas (and a couple more), but I cannot get the
mouse pointer to behave when two-finger scroll is used. I will keep on
trying, but recently I have been very short on time...

Thanks for this great package, it really is excellent! I also have the issue of scrolling up a little before scrolling down with two finger scroll. The issue is that the second finger generates a scroll relative to the first finger. So you put a finger down, and if the second finger is above it, it scrolls up, and if the second finger is below, it scrolls down. However if you are careful to place them evenly, it works fine.

However it would be nice to not scroll at all until the two fingers are moved together, and not on the second "tap", perhaps that is possible somehow.

---

### Post by thomas11 on 2008-07-20
Hi,

I'm a Slackware user who found this thread and the patch by googling. I now registered to be able to download it, but I'm wondering, have you submitted the patch upstream? Or made it available somewhere where it's downloadable freely? As it's not specific to Ubuntu, it would be nice if everyone could benefit from it.

Thanks for the good work!
Thomas

---

### Post by bmc5311 on 2008-09-16
[QUOTE=volanin;4935144]I have patched and recompiled the synaptics driver in Hardy Heron to
make it more enjoyable to use the mousepad while using the macbook.
This package below add the option MultiFingerButton to synaptics......

:guitar:

Dude - you are the best, I've waited for one of you smart guys to do this for the last year!

---

### Post by kosumi68 on 2008-09-17
> **thomas11 said:**
> Hi,

I'm a Slackware user who found this thread and the patch by googling. I now registered to be able to download it, but I'm wondering, have you submitted the patch upstream? Or made it available somewhere where it's downloadable freely? As it's not specific to Ubuntu, it would be nice if everyone could benefit from it.

Thanks for the good work!
Thomas

The two-finger scroll functionality has been included in synaptics-0.15.X, which will appear in Ubutuntu 8.10 (Intrepid). The default settings are also auto-detected, so the multi-touch features will work out-of-the-box.

---

### Post by hanzomon4 on 2008-09-18
How do I get this in Intrepid?

---

### Post by cyberdork33 on 2008-09-18
> **hanzomon4 said:**
> How do I get this in Intrepid?
I think this has been incorporated into synaptics now and is part of Intrepid. The option name has changed though... Try this:
[http://ubuntuforums.org/showpost.php?p=5813423&postcount=224](http://ubuntuforums.org/showpost.php?p=5813423&postcount=224)

---

### Post by hanzomon4 on 2008-09-20
It works... however it causes ubuntu to hard lock requiring a cold reboot

---

### Post by kosumi68 on 2008-09-21
> **hanzomon4 said:**
> It works... however it causes ubuntu to hard lock requiring a cold reboot

Could you please provide more details on what "it" is, what "it" is, and what "ubuntu" is? Nobody else has seen this problem before in conjuction with multi-finger clicks.

---

### Post by midtown on 2008-09-21
> **kosumi68 said:**
> Could you please provide more details on what "it" is, what "it" is, and what "ubuntu" is, please. Nobody else has seen this problem before in conjuction with multi-finger clicks.

Actually my Macbook hard-locks not rarely requiring a hard restart, while my other laptop doesn't. I never thought about it before but I wonder if it was to do with me using this custom synaptics.

---

### Post by kosumi68 on 2008-09-21
> **midtown said:**
> Actually my Macbook hard-locks not rarely requiring a hard restart, while my other laptop doesn't. I never thought about it before but I wonder if it was to do with me using this custom synaptics.

What version number is your custom synaptics?

---

### Post by hanzomon4 on 2008-09-21
I thought that my last two post would make it clear. I'm using intrepid and the stock  synaptics driver. Enabling the option linked to in cyberdorks post causes ubuntu to lockup requiring a hard reboot. ```
option   "ClickFinger2"     "3"
```

---

### Post by kosumi68 on 2008-09-21
> **hanzomon4 said:**
> I thought that my last two post would make it clear. I'm using intrepid and the stock  synaptics driver. Enabling the option linked to in cyberdorks post causes ubuntu to lockup requiring a hard reboot. ```
option   "ClickFinger2"     "3"
```

So hanzomon4 and midtown are the same person, talking about the same problem?

Since it seems difficult to reproduce this problem, the more information one can provide, the better it is. Can you give details on when the hardlock occurs, somehow proving it has to do with the option above?

---

### Post by hanzomon4 on 2008-09-21
> **kosumi68 said:**
> So hanzomon4 and midtown are the same person, talking about the same problem?

Since it seems difficult to reproduce this problem, the more information one can provide, the better it is. Can you give details on when the hardlock occurs, somehow proving it has to do with the option above?

WHAT!?!?!? I find your statements confusing, but anyway......

Yeah it didn't happen before I enabled the option and it doesn't happen when I disable it. Other then that it appears to be consistently random but definitely bound to happen.

---

### Post by midtown on 2008-09-21
> **kosumi68 said:**
> What version number is your custom synaptics?

How might I ascertain this, what specific package would I look at? I believe I installed it from the mactel ppa.

---

### Post by kosumi68 on 2008-09-21
> **hanzomon4 said:**
> WHAT!?!?!? I find your statements confusing, but anyway......


I did not count your first post in the thread, since it was a question - my apologies to midtown.

> 
Yeah it didn't happen before I enabled the option and it doesn't happen when I disable it. Other then that it appears to be consistently random but definitely bound to happen.


I filed a bug in launchpad, [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/272926](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/272926). However, it is likely to be tagged as incomplete with the current amount of information.

---

### Post by kosumi68 on 2008-09-21
> **midtown said:**
> How might I ascertain this, what specific package would I look at? I believe I installed it from the mactel ppa.

The simplest way to find out is probably to do
```

dpkg-query -W xserver-xorg-input-synaptics
synclient -V

```

However, if you installed it from the mactel hardy ppa, it is not likely to be the same problem; the fingerClick options first appeared in 0.15.0.

---

### Post by cyberdork33 on 2008-09-21
hanzomon4,

Are you sure the system is completely locked up? Can you CTRL+ALT+F1 and get to a terminal? After a lockup, can you post the contents of your Xorg log?

---

### Post by Rog-Mahal on 2008-09-22
Perhaps I missed something. I already had that package installed, so I just went ahead and added the line to my xorg.conf and my settings have not changed. Did I miss something? Even though I have the correct package, do I still need to force install the ones attached to volanin's original post?

Thanks

---

### Post by hanzomon4 on 2008-09-24
Xorg.0.log.old after freeze

```
(II) Synaptics touchpad driver version 0.15.2
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(II) Synaptics Touchpad: x-axis range 0 - 1215
(II) Synaptics Touchpad: y-axis range 0 - 386
(**) Option "Device" "/dev/input/event10"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "10"
(**) Option "RightEdge" "1200"
(**) Option "TopEdge" "10"
(**) Option "BottomEdge" "370"
(**) Option "FingerLow" "10"
(**) Option "FingerHigh" "20"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "MaxDoubleTapTime" "180"
(**) Option "VertScrollDelta" "20"
(**) Option "HorizScrollDelta" "50"
(**) Option "VertEdgeScroll" "0"
(**) Option "HorizEdgeScroll" "0"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "LockedDrags" "off"
(**) Option "RTCornerButton" "0"
(**) Option "RBCornerButton" "0"
(**) Option "LTCornerButton" "0"
(**) Option "LBCornerButton" "0"
(**) Option "TapButton1" "0"
(**) Option "TapButton2" "0"
(**) Option "TapButton3" "0"
(**) Option "ClickFinger2" "3"
(**) Option "SingleTapTimeout" "100"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: TOUCHPAD)
(II) Synaptics Touchpad: x-axis range 0 - 1215
(II) Synaptics Touchpad: y-axis range 0 - 386
(--) Synaptics Touchpad touchpad found
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(**) Option "xkb_variant" "mac"
(**) Video Bus: xkb_variant: "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Apple Computer Apple Internal Keyboard / Trackpad
(**) Apple Computer Apple Internal Keyboard / Trackpad: always reports core events
(**) Apple Computer Apple Internal Keyboard / Trackpad: Device: "/dev/input/event3"
(II) Apple Computer Apple Internal Keyboard / Trackpad: Found keys
(II) Apple Computer Apple Internal Keyboard / Trackpad: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple Computer Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Apple Computer Apple Internal Keyboard / Trackpad: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Apple Computer Apple Internal Keyboard / Trackpad: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Apple Computer Apple Internal Keyboard / Trackpad: xkb_layout: "us"
(**) Option "xkb_variant" "mac"
(**) Apple Computer Apple Internal Keyboard / Trackpad: xkb_variant: "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Apple Computer Apple Internal Keyboard / Trackpad: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device applesmc
(**) applesmc: always reports core events
(**) applesmc: Device: "/dev/input/event12"
(II) applesmc: Found x and y absolute axes
(WW) applesmc: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "applesmc"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(WW) Apple Computer Apple Internal Keyboard / Trackpad: unable to handle keycode 464
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Apple Computer Apple Internal Keyboard / Trackpad: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"

```

---

### Post by genius_1a2b on 2008-09-24
paypal wholesale ARMANI (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Bape (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale boot (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Burberry max (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Chanel (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Christan Audiger shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Timberland (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale UGG (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Versace shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale women jordans (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale WOWEN (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dunk(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale ED hardy shoes(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Evisu(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale GOODYEAR(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale dsq shoes(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dunk (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale ED hardy shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale COURT FORCE (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale converse (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale D&G shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dior shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale D&G shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale dsq shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))

---

### Post by luddek on 2008-10-15
Thanks this worked in debian
However the option touchpadoff was changed or something when I installed the package from the mactel repos. So at first I didn't think it worked. But now I'm happy.

/Luddek

---

### Post by Vistaus on 2008-10-24
Very weird, but only the middle-click works, no matter if I use         Option		"MultiFingerButton"	"1" of         Option		"MultiFingerButton"	"2" The right-click just won't work :(

Anybody got a solution for this? I do have a Synaptics touchpad...

Edit: Ow I found out that right-click does work, sometimes, but when it works, it works not with 3 fingers, it works with 4 fingers :S

Editedit: Ow, now it does work, via option 1. Trying option 2 now. Nope, only option 1 works, but I want option 2 to work (the Mac style).

---

### Post by dannyobrien on 2008-10-31
Is there a version of this patch for Intrepid? If so, how do I set it up?

---

### Post by midtown on 2008-10-31
> **dannyobrien said:**
> Is there a version of this patch for Intrepid? If so, how do I set it up?

This was already asked and answered on page 5 :)

---

### Post by volanin on 2008-10-31
I have not installed Intrepid yet (lack of time), but I should do so this
weekend, or the beginning of the next, and then I'll definitely try to
update this patch to the new Xorg input system.

Soon... soon!
:)

---

### Post by DatBugler on 2009-08-24
Hi,

I just installed Jaunty on my MacBook Pro. Is there a version around of this patch for the current version of xserver-xorg-input-synaptics? Thanks!

---

