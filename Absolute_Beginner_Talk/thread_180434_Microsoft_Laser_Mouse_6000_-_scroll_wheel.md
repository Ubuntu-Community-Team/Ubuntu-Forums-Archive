---
title: "Microsoft Laser Mouse 6000 - scroll wheel?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Dixius99 on 2006-05-22
I'm sure this issue is answered somewhere already, but I have so many xorg.confs and imwheelrcs floating around in my head that I can't find it...

Anyway, I installed Breezy a few days ago, and got everything set up the way I like it, inlcuding using the side buttons on my Microsoft Laser Mouse 6000 for  forward/back, and the scroll wheel for scrolling.

I decided to upgrade to Dapper Flight 8 shortly thereafter, and I noticed that my forward and back buttons no longer worked, while the scroll wheel was still fine. Since then I've been attempting to find a configuration that works for me.

So, I followed a bunch of How-Tos (mostly the same ones I used for my initial configuration) and after much trial and error, the forward and back buttons now work! The problem is that the scroll wheel no longer scrolls, but instead now also does forward and back.

I'm sure I just have one minor thing off, but all of the 4/5 6/7 stuff is confusing me.

Here is the pertinent section from my xorg.conf file:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "ZAxisMapping" "4 5"
	Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

Here's what I added to my imwheelrc file:

```
".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```

And here's what's in my /etc/X11/Xsession.d/57xmodmap file (modified from the [IntellimouseMousemanBackForwardButtons]("https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons?highlight=%28mouse%29") How-to found in the Ubuntu wiki, on advice found elsewhere)

```
#/bin/bash
xmodmap -e "pointer = default" &
```

Any help would be greatly appreciated!

---

### Post by Dixius99 on 2006-05-22
Update:

I don't know if it is the best/most elegant solution, but merely removing imwheel seems to have fixed it!

---

### Post by robaal on 2007-05-23
I was able to get my Laser 6000 fully operational under Feisty Fawn thanks to this info.

I didn't have to remove imwheel though; [the guide at ubuntuguides.org]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#Install_.26_Configure_IMWheel") now includes a mention that a space between 6 and 7 on the line **exec imwheel -k -b "67" &** in /home/login/mouse might help under Feisty, so I did that and also rearranged the order in the second line of that file to ```
exec xmodmap -e "pointer = 1 2 3 4 5 6 7" &
``` when I was trying to fix it myself, and didn't change it back.
These are the only differences as far as I can tell.


I also didn't notice at first that I had "ImPS/2" as the protocol instead of "ExplorerPS/2" in xorg.conf, in case other people stumble onto this page (it was the first result for me when googling "laser mouse 6000" ubuntu),

---

