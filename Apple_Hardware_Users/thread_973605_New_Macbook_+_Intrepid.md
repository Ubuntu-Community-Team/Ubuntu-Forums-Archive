---
title: "New Macbook + Intrepid"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by undoIT on 2008-11-06
Has anyone installed Intrepid 8.10 on the new Macbook? Is there any way to get mouse gestures working, or at least assign a region of the touchpad for right-click? How is the compatibility with hardware?

---

### Post by m.musashi on 2008-11-06
See this thread:

[http://ubuntuforums.org/showthread.php?t=964291](http://ubuntuforums.org/showthread.php?t=964291)

I have it working now thanks to the mactel ppa.

---

### Post by undoIT on 2008-11-06
Wow! Thanks for the link. This is the first time I've been seriously considering buying another Mac in some time. If it is possible to get everything operational in Ubuntu for the dual-boot I may just have to get one.

btw, Kurosawa is awesome. I need to dig out my collection and watch some.

---

### Post by m.musashi on 2008-11-06
to be clear, not all gestures work. I have 1, 2 and 3 finger tapping (1 click, right and middle) but not the other zoom, etc. 2 finger scrolling also works out of the box. However, I'm finding the tapping to be annoying. While typing my cursor moves all over with incidental taps. I just opened a new thread on that. If I can find a way to turn it off and on that would be cool.

---

### Post by undoIT on 2008-11-06
with a touchpad that big, i'd imagine accidental taps would be a concern. perhaps it requires some training of the wrists. i don't really care about zoom, as long as i can get an efficient, non-carpal tunnel inducing right-click working, that is just fine.

how about page up, page down? is there any way to simulate those keys? i use them all the time on my current computers. or is the two finger scrolling a sufficient replacement?

---

### Post by m.musashi on 2008-11-06
I don't use page up / down. What way do you use these? Or do you mean the actual keys on a 104 key keyboard? Two finger scrolling is quite simple and fast. Arrow keys work too.

Oh, and fn up or down arrow jumps (not sure a full page) up and down.

---

### Post by undoIT on 2008-11-06
page up and page down keys are very useful when dealing with a large spread sheet or a website with a big scroll bar. it is an efficient way to scroll to the next page of info. there is also "end" and "home" which are useful for jumping to the top and bottom of pages / documents with large scroll bars. i use those quite a bit too and i missed having those keys on my old macbook.

how about the hard drive? is it easy to replace like the previous generation of macbooks?

---

### Post by m.musashi on 2008-11-06
Okay, yeah, those keys don't exist. There are some similar shortcuts like fn up arrow.

I've not tried to remove the drive yet but from what I've read/seen it's brain dead easy. It's all accessible under the bottom batter cover which also covers the drive. There are some nice descriptions on the apple site about the various features. I downloaded a nice overview video from there too.

---

### Post by undoIT on 2008-11-06
very cool :D

As long as there are short-cut keys that substitute page up and page down in Ubuntu, all of my usability issues with macs are no longer an issue.

---

### Post by cyberdork33 on 2008-11-07
> **undoIT said:**
> there is also "end" and "home" which are useful for jumping to the top and bottom of pages / documents with large scroll bars. i use those quite a bit too and i missed having those keys on my old macbook.
You will find that "Home" and "End" function differently on pretty much every platform BUT OS X. Home and End generally go to the beginning or end of a single line, not a page.

I think that Fn+Right = End and Fn+Left = Home in OSX, but I do not know if they operate the same in Ubuntu.

---

### Post by undoIT on 2008-11-07
> **cyberdork33 said:**
> You will find that "Home" and "End" function differently on pretty much every platform BUT OS X. Home and End generally go to the beginning or end of a single line, not a page.

I think that Fn+Right = End and Fn+Left = Home in OSX, but I do not know if they operate the same in Ubuntu.

Yes. I need to press Ctrl End to go to the bottom of a spreadsheet, whereas in a web browser only pressing End goes to the bottom of the page.

I probably should go to a local store and try out the new Macbook to get a feel for it. I wonder if they would let me load up my Ubuntu Live CD?

:D

---

### Post by cyberdork33 on 2008-11-07
> **undoIT said:**
> Yes. I need to press Ctrl End to go to the bottom of a spreadsheet, whereas in a web browser only pressing End goes to the bottom of the page.

I probably should go to a local store and try out the new Macbook to get a feel for it. I wonder if they would let me load up my Ubuntu Live CD?

:D
Worth a shot. Note that there are a few items that will not work on the CD, but can be fixed with packages from the mactel-support PPA:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by undoIT on 2008-11-24
Okay, I got my new MacBook. Popped in the Kubuntu 8.10 liveCD and booting it up :)

---

### Post by undoIT on 2008-11-24
> **m.musashi said:**
> to be clear, not all gestures work. I have 1, 2 and 3 finger tapping (1 click, right and middle) but not the other zoom, etc. 2 finger scrolling also works out of the box. However, I'm finding the tapping to be annoying. While typing my cursor moves all over with incidental taps. I just opened a new thread on that. If I can find a way to turn it off and on that would be cool.

How did you get 2 and 3 finger tapping to work? I've been messing with the config file and can't get those functioning. Here is the synaptics config I have:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">1</merge>
        <merge key="input.x11_options.TapButton3" type="string">1</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by cyberdork33 on 2008-11-25
> **undoIT said:**
> ```
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">1</merge>
        <merge key="input.x11_options.TapButton3" type="string">1</merge>
```

You have tapping with 1, 2, or 3 fingers set to left click (button 1)

---

### Post by undoIT on 2008-11-26
aha. i had used these settings earlier and was expecting a 2 finger right click:

```
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
```

needs to be:

```
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
```

getting closer :D

---

### Post by joka. on 2008-11-26
Hi, I'm planning on getting the new macbook pro soon and installing Intrepid  8.10 on there, but I want to figure out what needs to be fixed first before doing so. Can anyone tell me what else needs to be fixed for the touchpad? And is there a thread that's for fixing the function buttons? Thanks.

---

### Post by cyberdork33 on 2008-11-26
> **joka. said:**
> Hi, I'm planning on getting the new macbook pro soon and installing Intrepid  8.10 on there, but I want to figure out what needs to be fixed first before doing so. Can anyone tell me what else needs to be fixed for the touchpad? And is there a thread that's for fixing the function buttons? Thanks.
This is the best info we have right now.
[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

---

