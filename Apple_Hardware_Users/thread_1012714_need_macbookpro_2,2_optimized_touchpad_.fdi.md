---
title: "need macbookpro 2,2 optimized touchpad .fdi"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by woodybrando on 2008-12-16
[LEFT][/LEFT]
Hi All,
I just installed ubuntu 8.10 onto my macbookpro 2,2 single boot. Having a few problems, the primary one being getting my touchpad just right. How I understand it, you want to strip all references to the touchpad out of the xorg.conf so that hal can automatically detect it. Then to fine tune the touchpad you create an .fdi file in /etc/hal/fdi/policy, with the adjustments you want.
Ideally I'd like the touchpad to not have any tapping, not 1,2 or 3 fingers. 
instead, I 'd like to have the ability to hold down 1,2 or 3 fingers and click the big button to have the same effect as tapping would. Also, I want to scroll horizontally and vertically by dragging two fingers. Any help would be much appreciated. Here's the situation:

I have only two .fdi files in /etc/hal/fdi/policy/
one that I copy and pasted from a macbook touchpad thread called 11-x11-synaptics.fdi
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<match key="info.product" contains="appletouch">
<merge key="input.x11_driver" type="string">synaptics</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.LeftEdge" type="string">10</merge>
<merge key="input.x11_options.RightEdge" type="string">1200</merge>
<merge key="input.x11_options.TopEdge" type="string">10</merge>
<merge key="input.x11_options.BottomEdge" type="string">370</merge>
<merge key="input.x11_options.FingerLow" type="string">10</merge>
<merge key="input.x11_options.FingerHigh" type="string">20</merge>
<merge key="input.x11_options.MaxTimeTap" type="string">180</merge>
<merge key="input.x11_options.MaxTimeMove" type="string">220</merge>
<merge key="input.x11_options.SingleTapTimeout" type="string">100</merge>
<merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
<merge key="input.x11_options.LockedDrags" type="string">off</merge>
<merge key="input.x11_options.MinSpeed" type="string">1.10</merge>
<merge key="input.x11_options.MaxSpeed" type="string">1.30</merge>
<merge key="input.x11_options.AccelFactor" type="string">0.08</merge>
<merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
<merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
<merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
<merge key="input.x11_options.RTCornerButton" type="string">0</merge>
<merge key="input.x11_options.RBCornerButton" type="string">3</merge>
<merge key="input.x11_options.LBCornerButton" type="string">0</merge>
<merge key="input.x11_options.LTCornerButton" type="string">0</merge>
<!merge key="input.x11_options.TapButton1" type="string">1</merge>
<merge key="input.x11_options.TapButton2" type="string">3</merge>
<merge key="input.x11_options.TapButton3" type="string">2</merge>
</match>
</match>
</device>
</deviceinfo>

```
and a preferences.fdi that was installed automatically but doesn't say anything about a touchpad.
also, my xorg.conf looks like this:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

thanks,
jayson
[www.oldchildprojects.com](www.oldchildprojects.com)

---

### Post by rr33333 on 2008-12-16
welcome to our website: [www.voguejordan.com](www.voguejordan.com) ,We hope become your reliable shoes supplier in China. Authentic Shoes with original box,we insists that " Customer the highest, Quality first ". Our products include Air Jordan series,Mix jordan series, Air max Shoes series, Air force one, Nike shox series shoes, Adidas Shoes, Timberland Shoes, Prada Shoes,Gucci shoes,puma shoes,lv bags, and Bape, Lacoste,Polo T-shirt,Evisu hoody,Evisu coat etc. we are looking forward to building sincere and long-term business relationships with you.

---

### Post by bryonak on 2008-12-16
Informatively posted question, nice!
Your xorg.conf looks nice, the lspci output and the preferences.fdi are irrelevant for this.

In order to disable tapping, just set the TapButtonX (1,2,3) options in your touchpad.fdi to 0 instead of 1, 2 or 3.
I mean your "11-x11-.." file... the name doesn't matter, it gets loaded as long as it's in the policy folder. Give it a descriptive name like appletouch.fdi or touchpad.fdi.

For horizontal scrolling, just set your HorizTwoFingerScroll parameter to true. You might also want to fine tune the HorizScrollDelta parameter.

It's easiest to edit the files by issuing```
gksudo gedit /etc/hal/fdi/policy/<filename>.fdi
```Don't forget saving ;)

In order to make the changes take effect, you have to reload your touchpad kernel module. Unload it in the terminal with ```
sudo modprobe -r appletouch
```Now your touchpad won't work. Load the module again with ```
sudo modprobe appletouch
```which will apply the changed configuration file.


I haven't got a list taylored to your 2.2 since I own a 3.1, but here's my touchpad configuration file anyway, you might want to get some ideas from it:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
	<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">false</merge>
	<merge key="input.x11_options.LeftEdge" type="string">0</merge>
	<merge key="input.x11_options.RightEdge" type="string">1150</merge>
	<merge key="input.x11_options.TopEdge" type="string">0</merge>
	<merge key="input.x11_options.BottomEdge" type="string">800</merge>
	<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
	<merge key="input.x11_options.ClickFinger2" type="string">3</merge>
	<merge key="input.x11_options.ClickFinger3" type="string">2</merge>
	<merge key="input.x11_options.FingerLow" type="string">3</merge>
	<merge key="input.x11_options.FingerHigh" type="string">10</merge>
	<merge key="input.x11_options.MaxTapTime" type="string">100</merge>
	<merge key="input.x11_options.MaxTapMove" type="string">30</merge>
	<merge key="input.x11_options.MaxDoubleTapTime" type="string">220</merge>
	<merge key="input.x11_options.MaxTripleTapTime" type="string">220</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.MinSpeed" type="string">0.3</merge>
	<merge key="input.x11_options.MaxSpeed" type="string">1.5</merge>
	<merge key="input.x11_options.AccelFactor" type="string">0.6</merge>
	<merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
	<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.VertScrollDelta" type="string">10</merge>
	<merge key="input.x11_options.HorizScrollDelta" type="string">15</merge>
	<merge key="input.x11_options.RTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.RBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.TapButton1" type="string">1</merge>
	<merge key="input.x11_options.TapButton2" type="string">3</merge>
	<merge key="input.x11_options.TapButton3" type="string">2</merge>
	<merge key="input.x11_options.PalmDetect" type="string">true</merge>
	<merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
	<merge key="input.x11_options.PalmMinZ" type="string">200</merge>

	<merge key="input.x11_options.ClickTime" type="string">80</merge>
	<merge key="input.x11_options.FastTaps" type="string">false</merge>
	<merge key="input.x11_options.EdgeMotionMinZ" type="string">30</merge>
	<merge key="input.x11_options.EdgeMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.EdgeMotionMinSpeed" type="string">1</merge>
	<merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">40</merge>
	<merge key="input.x11_options.EdgeMotionUseAlways" type="string">off</merge>
	<merge key="input.x11_options.PressureMotionMinZ" type="string">30</merge>
	<merge key="input.x11_options.PressureMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.PressureMotionMinFactor" type="string">1</merge>
	<merge key="input.x11_options.PressureMotionMaxFactor" type="string">1</merge>
	<merge key="input.x11_options.UpDownScrolling" type="string">true</merge>
	<merge key="input.x11_options.LeftRightScrolling" type="string">true</merge>
	<merge key="input.x11_options.UpDownRepeat" type="string">true</merge>
	<merge key="input.x11_options.LeftRightRepeat" type="string">false</merge>
	<merge key="input.x11_options.ScrollButtonRepeat" type="string">100</merge>
	<merge key="input.x11_options.EmulateMidButtonTime" type="string">75</merge>
	<merge key="input.x11_options.TouchpadOff" type="string">0</merge>
	<merge key="input.x11_options.GuestMouseOff" type="string">false</merge>
	<merge key="input.x11_options.CircularScrolling" type="string">off</merge>
	<merge key="input.x11_options.CircScrollDelta" type="string">0.1</merge>
	<merge key="input.x11_options.CircScrollTrigger" type="string">0</merge>
	<merge key="input.x11_options.CircularPad" type="string">false</merge>
	<merge key="input.x11_options.CoastingSpeed" type="string">0</merge>
	<merge key="input.x11_options.SingleTapTimeout" type="string">150</merge>
	<merge key="input.x11_options.TwoFingerButton1" type="string">2</merge>
	<merge key="input.x11_options.FingerPress" type="string">20</merge>
	<merge key="input.x11_options.TrackstickSpeed" type="string">0.0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by woodybrando on 2008-12-16
thanks for the help bryonak,
i went ahead and copy and pasted your appletouch.fdi into my /etc/hal/fdi/policy directory figuring not too much changed between the macbookpro 2,2 and 3,1 (but you reminded me that the 3,1 came out about ten days after I bought the 2,2, ouch.) Anyway I restarted the module like you showed me, and now i've got everything working. Although, the scrolling is a little too speedy for me. 

Also, do you get a lot of incidental horizontal scrolling when you're just trying to scroll vertically? I do, especially when lifting my fingers off the pad, the cursor does a little horizontal jump. Should I change the delta to a number higher or lower than 15 to degrease the horizontal scroll?
(just answered my own question with a little experimentation, seems like lower numbers speed things up and higher numbers calm them down, set my HorizontalScrollDelta to 20 and VerticalScrollDelta to 50 and it calmed the scrolling down a lot.

Also, do you use gsynaptics or qsynaptics or do you just adjust settings in your .fdi? 

Also, it seems like SHMConfig was the problem. Atleast that seems like the big difference between your .fdi and the one I was using. Yours has SHMConfig set to false and mine was set to true. Anyone know why turning it off would fix things?

also, is there a place to go to find definitions for all these touchpad options?



thanks again,
jayson
[www.oldchildprojects.com](www.oldchildprojects.com)

---

### Post by bryonak on 2008-12-16
> **woodybrando said:**
> 
Also, do you get a lot of incidental horizontal scrolling when you're just trying to scroll vertically? I do, especially when lifting my fingers off the pad, the cursor does a little horizontal jump. Should I change the delta to a number higher or lower than 15 to degrease the horizontal scroll?
(just answered my own question with a little experimentation, seems like lower numbers speed things up and higher numbers calm them down, set my HorizontalScrollDelta to 20 and VerticalScrollDelta to 50 and it calmed the scrolling down a lot.

I only scroll horizontally in images, otherwise my windows (file browser, firefox and the like) are always big enough to show the content in it's horizontal entirety ;)
Good thing you figured that out though.
*edit*: I've missed you were first referring to vertical scroll... I think that's implementation specific... if you move your fingers exactly simultaneously, it won't jump around. The advantage of this implementation is that you can scroll by holding one finger down and then tapping with the other finger below/above the first one. The vertical distance between the two fingers will define the amount of scrolling. It takes getting used to (as most computer interaction does), but I actually use it more than the OSX-style two-finger scrolling.


> 
Also, do you use gsynaptics or qsynaptics or do you just adjust settings in your .fdi? 

Also, it seems like SHMConfig was the problem. Atleast that seems like the big difference between your .fdi and the one I was using. Yours has SHMConfig set to false and mine was set to true. Anyone know why turning it off would fix things?

There's that thing about SHMConfig... if this option is enabled, the RAM space of your touchpad driver is shared to anyone who cares to access it. This is regarded a security flaw by many, others claim it a good thing for modifying the driver with tools like Gsynaptics.
In the future, it will (and should) probably be disabled completely and Gsynaptics should do it "properly" with appropriate access rights, but for now, it remains useful for diagnosis and graphical editing of the config.

As you see I turned it off because I'm completely fine with editing the config file by hand. So I obviously don't use the GUI tools.

> 
also, is there a place to go to find definitions for all these touchpad options?

Open a terminal and type ```
man synaptics
```
Or maybe you prefer the [HTML version]("http://manpages.ubuntu.com/manpages/intrepid/man4/synaptics.html") of the manual page.

> thanks again
You're welcome (they even implemented a "thanks" button in these forums ;))

---

### Post by woodybrando on 2008-12-16
yeah, where is the thank you button i was trying to figure that out but gave up. Is there a button on the page somewhere?

also, horizontal scrolling is still being weird and jumps even with the horizontal delta turned up to 50. I think it might have something to do with edge detect. Also, I just figured out what you meant by holding one finger down and tapping a second finger above and below it, or right or left of it to scroll. That's pretty cool. I'll give that a try instead of the os x style two finger slide.

also, the touchpad gets weird when I go to click on a small button, or try to resize a window, it's not sensitive or something, or it's oversensitive and jumps right past the spot i'm trying to grab or click. I'll play with acceleration or minSpeed. And post my appletouch.fdi when I get it just right.

man synaptics, who'd have thought to look there? ;) 

also, where did you get those numbers for the left, right, top and bottom edge? Cause I'm wondering if they're different for my 2,2 macbookpro.

edit:
okay so here's an appletouch.fdi that's working pretty nicely for me. turned off one and two finger tapping, but kept 3 finger tap for pasting. one and two finger click is still enabled. turned off vertical scroll. and used right and bottom edge reported by volanin's method (below):
```


<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
	<merge key="input.x11_driver" type="string">synaptics</merge>
	<merge key="input.x11_options.SHMConfig" type="string">false</merge>
	<merge key="input.x11_options.LeftEdge" type="string">0</merge>
	<merge key="input.x11_options.RightEdge" type="string">1215</merge>
	<merge key="input.x11_options.TopEdge" type="string">0</merge>
	<merge key="input.x11_options.BottomEdge" type="string">386</merge>
	<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
	<merge key="input.x11_options.ClickFinger2" type="string">3</merge>
	<merge key="input.x11_options.ClickFinger3" type="string">2</merge>
	<merge key="input.x11_options.FingerLow" type="string">3</merge>
	<merge key="input.x11_options.FingerHigh" type="string">10</merge>
	<merge key="input.x11_options.MaxTapTime" type="string">100</merge>
	<merge key="input.x11_options.MaxTapMove" type="string">30</merge>
	<merge key="input.x11_options.MaxDoubleTapTime" type="string">220</merge>
	<merge key="input.x11_options.MaxTripleTapTime" type="string">220</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.MinSpeed" type="string">0.35</merge>
	<merge key="input.x11_options.MaxSpeed" type="string">1.5</merge>
	<merge key="input.x11_options.AccelFactor" type="string">0.11</merge>
	<merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
	<merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
	<merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
	<merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
	<merge key="input.x11_options.RTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.RBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LBCornerButton" type="string">0</merge>
	<merge key="input.x11_options.LTCornerButton" type="string">0</merge>
	<merge key="input.x11_options.TapButton1" type="string">0</merge>
	<merge key="input.x11_options.TapButton2" type="string">0</merge>
	<merge key="input.x11_options.TapButton3" type="string">2</merge>
	<merge key="input.x11_options.PalmDetect" type="string">true</merge>
	<merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
	<merge key="input.x11_options.PalmMinZ" type="string">200</merge>
	<merge key="input.x11_options.ClickTime" type="string">80</merge>
	<merge key="input.x11_options.FastTaps" type="string">false</merge>
	<merge key="input.x11_options.EdgeMotionMinZ" type="string">30</merge>
	<merge key="input.x11_options.EdgeMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.EdgeMotionMinSpeed" type="string">1</merge>
	<merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">40</merge>
	<merge key="input.x11_options.EdgeMotionUseAlways" type="string">off</merge>
	<merge key="input.x11_options.PressureMotionMinZ" type="string">30</merge>
	<merge key="input.x11_options.PressureMotionMaxZ" type="string">160</merge>
	<merge key="input.x11_options.PressureMotionMinFactor" type="string">1</merge>
	<merge key="input.x11_options.PressureMotionMaxFactor" type="string">1</merge>
	<merge key="input.x11_options.UpDownScrolling" type="string">true</merge>
	<merge key="input.x11_options.LeftRightScrolling" type="string">true</merge>
	<merge key="input.x11_options.UpDownRepeat" type="string">true</merge>
	<merge key="input.x11_options.LeftRightRepeat" type="string">false</merge>
	<merge key="input.x11_options.ScrollButtonRepeat" type="string">100</merge>
	<merge key="input.x11_options.EmulateMidButtonTime" type="string">75</merge>
	<merge key="input.x11_options.TouchpadOff" type="string">0</merge>
	<merge key="input.x11_options.GuestMouseOff" type="string">false</merge>
	<merge key="input.x11_options.CircularScrolling" type="string">off</merge>
	<merge key="input.x11_options.CircScrollDelta" type="string">0.1</merge>
	<merge key="input.x11_options.CircScrollTrigger" type="string">0</merge>
	<merge key="input.x11_options.CircularPad" type="string">false</merge>
	<merge key="input.x11_options.CoastingSpeed" type="string">0</merge>
	<merge key="input.x11_options.SingleTapTimeout" type="string">150</merge>
	<merge key="input.x11_options.TwoFingerButton1" type="string">2</merge>
	<merge key="input.x11_options.FingerPress" type="string">20</merge>
	<merge key="input.x11_options.TrackstickSpeed" type="string">0.0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by cyberdork33 on 2008-12-17
Well, I am trying to find a link, but there is a command you can run and then move your finger around to the extents of your touchpad to determine what the edge numbers should be...

EDIT:
ok try this command:
```
synclient -m 1
```Sorry, I do not have a way to test if it is right right now.

[http://linux.die.net/man/1/synclient](http://linux.die.net/man/1/synclient)

---

### Post by volanin on 2008-12-17
The command below will do the job.
On my Macbook 2,1 the result is the following:

```
$ cat /var/log/Xorg.0.log | grep -A2 Synaptics

(II) Synaptics touchpad driver version 0.15.2
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
```

This is the information returned by the device.
If I use cyberdork33 method, I get:

```
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   6.305  1210  381   5 1  0  0 0 0 0 0  00000000   0  0  0   0   0
```

Which means 1210x381 at the bottom-right corner.
A little less than the previous info.

So a good parameter for the Egde variables would be:
For two-finger scroll:

```
<merge key="input.x11_options.LeftEdge" type="string">0</merge>
<merge key="input.x11_options.TopEdge" type="string">0</merge>
<merge key="input.x11_options.RightEdge" type="string">1599</merge>
<merge key="input.x11_options.BottomEdge" type="string">386</merge>
```

This will make the whole touchpad area useful for moving the mouse arrow.
But if you use vertical one-finger scrolling, use:

```
<merge key="input.x11_options.RightEdge" type="string">1150</merge
```

This will reserve a portion on the right side of the touchpad for the
scrolling region. To scroll, just slide your finger there.

And if you use horizontal one-finger scrolling, use:

```
<merge key="input.x11_options.BottomEdge" type="string">350</merge>
```


Be aware that if you put any number greater than the maximum X/Y of the
touchpad, it will make no difference. It will be the same as using the
maximum values.
:)

---

### Post by bryonak on 2008-12-17
> **woodybrando said:**
> yeah, where is the thank you button i was trying to figure that out but gave up. Is there a button on the page somewhere?
Every message has got one, on the bottom right corner... ;)

> also, horizontal scrolling is still being weird and jumps even with the horizontal delta turned up to 50. I think it might have something to do with edge detect.
I never tried to figure out (since I don't use it that much), but does it help modifying the Edge parameters like volanin posted? If you want to try cyberdork's approach (with synclient), you have to turn on the SHMConfig.
My width setting is a bit smaller (and taylored to a MBP 3.1), because I additionaly use the right edge for one-finger scrolling (the VertEdgeScroll option).

> Also, I just figured out what you meant by holding one finger down and tapping a second finger above and below it, or right or left of it to scroll. That's pretty cool. I'll give that a try instead of the os x style two finger slide.
I hope you like it, since I'm not aware that it's possible to change it to exactly the same behaviour as in OSX. It has benefits and disadvantages (having to get used to it being the main one).


> man symantics, who'd have thought to look there? ;) 
synaptics, it's called synaptics (now that's the pedant in me...)

Apart from that, I think everything has been said. Feel free to keep posting if you encounter difficulties though ;)


Aside: would you care putting [code ][/code] tags around things like text file data, long console output and the like? It makes it more readable and shortens the height of your posting.

---

### Post by cyberdork33 on 2008-12-17
> **volanin said:**
> The command below will do the job.
On my Macbook 2,1 the result is the following:

```
$ cat /var/log/Xorg.0.log | grep -A2 Synaptics

(II) Synaptics touchpad driver version 0.15.2
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
```This is the information returned by the device.
If I use cyberdork33 method, I get:

```
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   6.305  1210  381   5 1  0  0 0 0 0 0  00000000   0  0  0   0   0
```Which means 1210x381 at the bottom-right corner.
A little less than the previous info.

So a good parameter for the Egde variables would be:
For two-finger scroll:

```
<merge key="input.x11_options.LeftEdge" type="string">0</merge>
<merge key="input.x11_options.TopEdge" type="string">0</merge>
<merge key="input.x11_options.RightEdge" type="string">1599</merge>
<merge key="input.x11_options.BottomEdge" type="string">386</merge>
```This will make the whole touchpad area useful for moving the mouse arrow.
Now, I am not saying that it is wrong, just making discussion on the topic, but what good is it to make the "untouchable" portion of your touchpad available to functions? ;)

---

### Post by volanin on 2008-12-17
> **cyberdork33 said:**
> Now, I am not saying that it is wrong, just making discussion on the topic, but what good is it to make the "untouchable" portion of your touchpad available to functions? ;)

Well...
I still think it's a shame we can't use negative values for TopEgde and LeftEgde!
;)

---

### Post by cyberdork33 on 2008-12-19
> **volanin said:**
> Well...
I still think it's a shame we can't use negative values for TopEgde and LeftEgde!
;)

lol

---

### Post by alhead on 2008-12-28
So if I want to configure my touchpad, but I don't have a Mac, do I need to change
<match key="info.product" contains="appletouch">
to something else?  Is that the only thing I need to change?

I had the touchpad set up the way I wanted on 8.04, but since updating to 8.10 it hasn't worked.

---

### Post by alhead on 2008-12-28
I got it working.  I think changing "appletouch" to "Synaptics Touchpad" fixed it.

---

### Post by alhead on 2008-12-28
Ok, so I had it working, but now it's not, and I don't know what happened.  Will gsynaptics interfere with the fdi file?  Should I remove gsynaptics?

---

### Post by alhead on 2008-12-28
Sorry to reply to only myself so many times, but I *think* I have it working now, for real this time.  I had to uninstall gsynpatics, and I had to modify the settings in System -> Preferences -> Mouse.

I wanted two-finger scrolling, but not one-finger scrolling with the right side of the touchpad, and I wanted two-finger middle click tap, but not one-finger tap to click.  I had to turn vertical scrolling off in mouse settings, but tap to click on, then modify the fdi file according to my preferences (using Synaptics Touchpad, not appletouch).

---

### Post by lord enzo on 2009-03-28
It has been very usefull read how you resolve that problem because I have the same one in the linux mint felicia version. I will try...

:)

---

### Post by Bobnox on 2009-04-03
Thank everyone who contributed to this thread. My touchpad tap was very sensitive, making using it almost impossible. Adding the appletouch.fdi file did the trick.

---

