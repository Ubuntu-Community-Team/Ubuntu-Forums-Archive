---
title: "Need some help with Macbook touchpad"
date: 2008-11-20
forum: Apple Hardware Users
---

### Post by Oplix on 2008-11-20
I followed these instructions for configuring my Macbook's touchpad. 
[https://wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa")

Please note, I'm the idiot who wiped his hard drive and installed Ubuntu without checking which version of Macbook he's got. I'm about 90% I remembered correctly though, I'm just pointing this out for the record if it helps solve my problem.

The instructions on that page seemed to work. At least to some extent. 

I have full 2-finger touch scrolling function. Vertical and horizontal, that's working perfectly. However I'm still having problems with my right-click function. When I was running Mac, I used to have the touchpad perform a right-click by placing both fingers on the touchpad and pushing the 'mouse' button. 2 fingers on the touchpad meant that any clicks would be r-clicks.

I also used the 2-finger touch for scrolling.

Currently I have no right-click functionality. Only the 2-finger scrolling.

Since Ubuntu has a scrolling desktop, there are a few things I would like different from when I was running my Mac OS.

Instead of 2-finger contact to trigger page scrolling, I would like to have 3-finger contact scrolling instead. Is this possible? I would like the cursor to behave normally when 2 fingers are in contact with the touchpad, but I would like 2 fingered contact to change the clicks into right clicks.

I'm using Ubuntu 8.10.

This is what I've got in my appletouch.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.FingerLow" type="string">10</merge>
   <merge key="input.x11_options.FingerHigh" type="string">20</merge>
   <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
  </match>
 </device>
</deviceinfo>
```
(from wiki.ubuntu)

In a blind attempt to change my scrolling from 2 fingers into three I made the following small changes (which seemed logical at least, but didn't work unfortunately)

```
   <merge key="input.x11_options.VertThreeFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizThreeFingerScroll" type="string">1</merge>
```

So I've kind of got it working... Just need some help to finish what I've started.

---

### Post by regebro on 2008-11-20
> **Oplix said:**
> Please note, I'm the idiot who wiped his hard drive and installed Ubuntu without checking which version of Macbook he's got.
Doesn't matter, you can do:
  sudo dmidecode -s system-product-name
And it will tell you.

> Currently I have no right-click functionality. Only the 2-finger scrolling.
I can confirm this problem, I have the same one, on a MacBook 4,1.

---

### Post by Oplix on 2008-11-20
Thanks for telling me about that terminal command. I was right, it's a 1,1.

So is there currently no way to enable 2-fingered right clicking?

By the sounds of some threads it looked like there was.

---

### Post by alwayshere on 2008-11-20
i have a macbook 1.1 running ubuntu 8.10 as sole os

i three finger tap mouse pad for right click
to scroll i use the right side of the mouse pad 
to click i hit the button or i double tap the mouse pad with one finger

Im not to sure what your looking for so i hope this help

---

### Post by regebro on 2008-11-20
> **Oplix said:**
> Thanks for telling me about that terminal command. I was right, it's a 1,1.

So is there currently no way to enable 2-fingered right clicking?

By the sounds of some threads it looked like there was.

Oh, on fact, it works. I just misunderstood how it was supposed to work. Under OS X, I held down two fingers, and clicked. Here, I tap with two fingers. Three-fingers = middle button too.

So it works for me.


I'd like to get rid of all mouse-pad clicking, it's just crap IMO. I want to use the button. If people have hints on how to do that and still have some sort of right-clicking, it would be appreciated.

---

### Post by Oplix on 2008-11-20
[http://ubuntuforums.org/showthread.php?t=790589]("http://ubuntuforums.org/showthread.php?t=790589")

This thread seems to have a patch for what I'm looking for, but I'm not sure how to install it.

What I want is...

1 finger on the touchpad - button performs left clicks, moves the cursor.

2 fingers on the touchpad - Still moves the cursor around. Button performs right clicks

3 fingers on the touchpad - Does not move the cursor but instead scrolls. Button performs middle clicks.

Tapping the touchpad with any number of fingers will not do anything. The number of fingers on the touchpad will determine what type of mouseclick function the button beneath the touchpad performs when it's pressed, and whether the cursor will move when the fingers are moved, or whether the screen will scroll as the fingers move on the pad.

That patch in that thread really does sound like it will be perfect for me, if I could get that installed.

It's not EXACTLY what I specified above here, but it makes the touchpad respond exactly as it does in OS x

---

### Post by regebro on 2008-11-20
That sounds pretty good, if you find a solution, put it here. :)

As I understand it, the driver changes are already in 8.10, and I tried some configuration changes, but nothing happened, so I'm out of my depth here. :)

---

### Post by Oplix on 2008-11-20
there are options for using a touchpad under System/Preferences/Mouse.

However nothing for the right-click, and no settings to set things up specifically...

Really hoping someone can tell me how to install that patch.

---

### Post by regebro on 2008-11-20
I do have options, and I can disable mouse clicks there, but then right and mid click won't work either.

---

### Post by Oplix on 2008-11-29
Just bumping this, I still haven't managed to get it working properly, and still haven't figured out what to do with that patch.

---

### Post by cashman04 on 2008-11-30
If I'm reading it right it looks like you need to navigate to

/etc/X11/xorg.conf

Open the xorg.conf with text editor.  

It will look something like this.
> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

One of the devices will be your touchpad, find it and put this string of text there(the one from the "patch" page.

> Option		"MultiFingerButton"	"2"

If I'm reading right this will set up the right click how you use it in OSX.  I use it the same way.

I may be way off here, I was just browsing through here while bored at work. 

But from what i read it should work for you.

Also, if there is already a "MultiFingerButton" under it, check what the value it, change it to 2 if you need to.  Also  back up the xorg.conf file first.

---

### Post by kosumi68 on 2008-11-30
For Intrepid (8.10), you should avoid using xorg.conf, but rather use the fdi configuration. See [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook), touchpad section, for instructions.

Two-finger-and-button-click can be configured using the lines
```

        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

```

---

### Post by Oplix on 2008-11-30
I've tried the instructions you linked me. Copied and pasted them directly but they didn't seem to work.

I'm going to try the other way for older versions to see if that'll at least work.

Tried the xorg.conf way, definitely not going to work seeing as the file looks nothing like you said.

Here are the contents of /etc/hal/fdi/policy/appletouch.fdi (the tutorial said name didn't matter?)

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

It was copied DIRECTLY from the tutorial you linked. I've tried restarting, but it doesn't seem to be working for me.

---

### Post by Oplix on 2008-12-08
Woops, figured out what I did wrong there, I misread the description of what the example code did -_-

Sorry about the bump, to anyone else solving this, don't make the same mistake I did, read words like "click" and "tap" CAREFULLY!

Still a couple questions though. I have the right-click working as I'd like, but the touchpad is still a little glitchy...

When I leave a finger on the trackpad and tap with another finger, the cursor jumps and the page scrolls. It also seems that if I put 1 finger down before the other while my cursor is over the task bar, it brings up one of my minimized windows or cycles my foccus.

Thanks for the help so far, is there a solution to these other problems?

I'd also like to ask, you can see the code I used from that tutorial, but lower in that tutorial they go much more into detail on how to customize the trackpad, except the coding they give looks different than what I used.
example:
```
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "150"
        Option          "RightEdge"             "1070"

```

Would I just enter that code into a text document and put it in the same HAL directory folder as the other code I used (mind you that's just a small snippet of the entire code)?

Still sorta learning my way around Linux, at least I got the problem fixed for myself, I'd just like to know how to iron out some kinks and to have an understanding of what this other stuff is that I didn't use and how I would use it, had I wanted to.

---

### Post by cyberdork33 on 2008-12-10
> **Oplix said:**
> When I leave a finger on the trackpad and tap with another finger, the cursor jumps and the page scrolls. It also seems that if I put 1 finger down before the other while my cursor is over the task bar, it brings up one of my minimized windows or cycles my foccus.What are you expecting it to do? two fingers on the pad = scrolling, and scrolling on the desktop causes ubuntu to cycle through desktops. You should be either tapping with two fingers at once, or holding a finger on the touchpad and clicking the button if you are trying to access other "clicks".

> **Oplix said:**
> I'd also like to ask, you can see the code I used from that tutorial, but lower in that tutorial they go much more into detail on how to customize the trackpad, except the coding they give looks different than what I used.
example:
```
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "150"
        Option          "RightEdge"             "1070"

```

Would I just enter that code into a text document and put it in the same HAL directory folder as the other code I used (mind you that's just a small snippet of the entire code)?This format is how you used to enter options into your xorg.conf file. You should be moving away from that and using the HAL directory method. The good news is that all those options should work the same way, you just have to put them in that xml file format that is used for the HAL method.

For example, the "RightEdge" option you posted would need to be entered like so as a line in your fdi file:
```
<merge key="input.x11_options.RightEdge" type="string">1070</merge>
```
You can get a listing of all the options available to the driver by typing 'man synaptics' in at a terminal.

---

### Post by beauman on 2008-12-13
i updated the section to get right/middle click emu.

---

### Post by Oplix on 2009-01-03
> What are you expecting it to do? two fingers on the pad = scrolling, and scrolling on the desktop causes ubuntu to cycle through desktops. You should be either tapping with two fingers at once, or holding a finger on the touchpad and clicking the button if you are trying to access other "clicks".

It shouldn't do anything. It should just sit there and wait for me to tell it what to do.

It shouldn't start scrolling just because I put 2 fingers on the pad, it should start scrolling because I put 2 fingers on the pad and dragged them somewhere. I shouldn't be able to leave 1 finger on the mousepad while tapping on the other end of the mousepad to scroll the page or make the cursor dance across the screen.

Let me give you an example of where this is a problem...

Say I was to save a link, I have to right-click it. So I move my cursor over the link with 1 finger, put my second finger down and click to make a r-click. Except now the page has scrolled down and the cursor has jumped out of place and I missed the right-click. This happens every time I try to click it because the trackpad is expecting me to put both fingers down at precisely the same moment, or else it registers a mouse movement and a scroll, until I leave both fingers on the trackpad after vertically aligning my cursor and then scrolling back up to the link with the arrow keys to right-click as it passes.

It works and does everything, it's just impossible to get it to do exactly what you want, when you want it because the cursor is always bouncing or scrolling around because the trackpad can't differentiate between 2 fingers moving to scroll, and a second finger being placed on the trackpad.

I'm HOPING that explained it properly... I know that there's definitely something not working perfectly with this trackpad still. If I had Mac installed I could show you instantly how differently the cursors responded, and how much better Mac handles the variable of finger timing and location to prevent mis-scrolls and missed clicks.

Here, let's pretend I need to right click a file on my desktop, my settings are set for 2 fingers scrolling, and so that when both fingers are on the pad at the same time and the button is clicked, it performs a right-click... So I move the cursor over the file with 1 finger. Take that finger off the trackpad. Place both fingers on the trackpad and push the button.

The trackpad registers me as moving my cursor back and forth between fingers points (as if 1 fingers was sliding on the trackpad back and forth, rather than 2 the 2-finger contact being registered immediately.

But then it realizes that I have 2 fingers on the pad, and not just 1, so after my cursor jumps around, it scrolls, because for some reason it thinks there's fingers moving around on the pad, when really I have 2 fingers resting stationary on the pad.

If I click, I do get the right-click because both my fingers are down, but in order to get both fingers down, I have to bounce my cursor back and forth and trigger a scroll.

So obviously I can't put both fingers down at once... Let's try putting the second finger down while the first fingers is still on the trackpad.

Well, we can again see that the cursor jumps on the screen between the points of where your fingers are. Try leaving 1 finger in the middle of the trackpad and start tapping circles around it with your other hand and watch the cursor bounce around in a circle returning back to its original position.

For some reason it interprets that placement of the second finger as a sliding finger, and also interprets it as 2 fingers sliding, because it performs both a 1 fingered function of moving the cursor back and forth between finger-points, but also scrolls as if two fingers were being dragged between the finger points.

I'll make a video of my fingers on the trackpad and my cursor to show you EXACTLY what's going on.

---

### Post by SaiHayashi on 2009-01-03
hi there i setup my macbook4,1 basically according to this site
[http://lijamez.wordpress.com/2008/10/31/ubuntu-810-intrepid-ibex-experience-on-a-macbook-21/](http://lijamez.wordpress.com/2008/10/31/ubuntu-810-intrepid-ibex-experience-on-a-macbook-21/)
for my macbook the the 2 finger tap right click doesnt always work, works about 90% of the time tho.

---

### Post by cyberdork33 on 2009-01-05
Oplix, You can configure the touchpad to operate how you want it to if you don't like the default configuration. That is what I asked, what are you "expecting" it do... If you don't want two-finger scrolling, turn it off. The same goes for the other functions you speak of.

---

