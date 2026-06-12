---
title: "Laptop trackpad Ubuntu 7.04"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by tashmooclam on 2007-07-25
Someone else may have this issue recently. Someone may find this on a search.
When I started using Ubuntu 7.04 I found my trackpad super sensitive. I would move the cursor around and any link it touched in Firefox would be selected. It was annoying to say the least. 
I may have fixed it. 
System menu. Preferences, Mouse, Motion Tab. I moved Acceleration and sensitivity to about the middle of the bar. 
Under Drag and Drop, Threshold I moved it to Large. 
Now my trackpad seems to behave correctly.

---

### Post by yeastpuppet on 2007-07-25
Thank you, thank you, thank you, thank you!

This problem was driving me absolutely nuts, sometimes it seemed that just looking at the touchpad was enough to trigger the darned thing.

Obviously I never thought about looking in mouse preferences since, at least obvious to me, the touchpad is not a mouse.

Inch by inch, anything's a cinch

Yeastpuppet

:)

---

### Post by anewguy on 2007-07-25
If it's a touchpad, do these 2 things:

(1)  Add the following to your xorg.conf under the touchpad section:

Option   "SHMConfig"  "true"

(2) via synaptics package manager, install gsynaptics

Then just log off, hold ctrl, alt and press backspace, then release the keys (this will restart x).  Now you'll have a "touchpad" entry in the system/preferences menu where you can set the touchpad properties.:)

---

### Post by tashmooclam on 2007-07-26
Now Anewguy really knows something. 
I'm gonna buy a book, I could not even begin to fathom the instructions, excellent as they are.

---

### Post by anewguy on 2007-07-26
You may want to see this post for more detailed instructions:

[[COLOR="Cyan"]Installing gsynaptics[/COLOR]]("http://ubuntuforums.org/showthread.php?t=492984")

---

### Post by tashmooclam on 2007-07-26
Thanks. I hope in a week I may have it figured out.

---

### Post by tashmooclam on 2007-07-27
I see the solution using only menus.
GO TO: System menu...Administration menu...Synaptic Package Manager.
Select Search button...Search for: "Touchpad". Search returned various results.
The last result had a little ubuntu icon next to it, It was called "Synaptics touchpad driver for X.org server". Click it and there is a description of how it will help the touchpad work. 
This was entirely using a GUI.

---

### Post by HermanAB on 2007-07-27
Synaptic Touch Pad

The screen, keyboard and mouse is configured in /etc/X11/xorg.conf. There is also a Synaptic utility that can be used to configure the touch pad on the fly and it is a good way to figure out which settings you need to change. The full set of features can be displayed with:

    * # synclient -l 

Edit /etc/X11/xorg.conf and scroll down to the Synaptic area, then change and add the following:

    * Option "MaxTapMove" "0"
    * Option "MaxTapTime" "0"
    * Option "MaxDoubleTapTime" "0"
    * Option "CircularScrolling" "1"

That will turn off the pad tap-to-click which doesn't work properly and will turn on circular scrolling. Circular scrolling allows you to scroll up/down by moving your finger around the edge of the pad: Clockwise to go down, anti-clockwise to go up, which is a good simulation of a scroll wheel.

The next problem, is that at start-up, these changes get overwritten. One way to fix this is by overwriting the xorg.conf file from a backup copy, with a command at the end of /etc/rc.local. This works, since rc.local is the last configuration file that runs before X is started. Instead of a simple backup, I use RCS, so I can keep track of versions in the etc directory.

Save all the config files in RCS (Case is important in the next set of commands):

# cd /etc/X11
# mkdir RCS
# ci -u -t-Baseline *
# rcs -U *

Now add this to the end of /etc/rc.d/rc.local:

# Fix mousepad overwrite issue
cd /etc/X11
co -f xfree.conf

The overwrite problem is caused by /usr/lib/libDrakX/Xconfig/xfree.pm, so you could also hack that file if you are comfortable with Perl.

To make these changes take effect, you have to restart X.

Hope that helps!

Herman

---

### Post by anewguy on 2007-07-27
> **tashmooclam said:**
> I see the solution using only menus.
GO TO: System menu...Administration menu...Synaptic Package Manager.
Select Search button...Search for: "Touchpad". Search returned various results.
The last result had a little ubuntu icon next to it, It was called "Synaptics touchpad driver for X.org server". Click it and there is a description of how it will help the touchpad work. 
This was entirely using a GUI.

My understanding is that the package you mentioned is the driver for xwindows for the touchpad.  i believe that if a touchpad is detected when installing Ubuntu it will automatically install that package so that X can use the touchpad.

For actually configuring the touchpad, the easiest (and giu) way is to use gsynaptics.:)

---

