---
title: "Synaptics Multitouch Touchpad Driver on other Laptops"
date: 2009-01-30
forum: Apple Hardware Users
---

### Post by undoIT on 2009-01-30
One of my favorite things about my MacBook is the multi-touch touchpad with two-finger scroll and two-finger tap to right click. Is it possible to install this driver on other laptops? For example, the new Dell Studio XPS 16 has a Synaptics touchpad that supports some multi-touch features like pinch zoom. Would it be possible to install the driver on the XPS 16 or perhaps port it?

---

### Post by cyberdork33 on 2009-01-30
It is likely that, if the hardware is similar, it would be pretty easy to port, if not just use the same driver... Unfortunately, I will not be the one to help with this (though I wish I could).

The 'lsusb' command will be able get you the hardware information.

---

### Post by undoIT on 2009-01-30
I may be purchasing an XPS 16 in the next few months. If I do, I'll try out the driver and post lsusb info if it is not working. It would be great to have this, I'm always trying to do the two-finger multi-touch gestures when switching back and forth from my MacBook to my current XPS laptop :rolleyes:

And, it would be a unique functionality available on Ubuntu, that Windows does not provide

---

### Post by kosumi68 on 2009-01-30
> **undoIT said:**
> One of my favorite things about my MacBook is the multi-touch touchpad with two-finger scroll and two-finger tap to right click. Is it possible to install this driver on other laptops? For example, the new Dell Studio XPS 16 has a Synaptics touchpad that supports some multi-touch features like pinch zoom. Would it be possible to install the driver on the XPS 16 or perhaps port it?

The kernel hardware modules for trackpads are very much dependent on the actual hardware. The appletouch, synaptics and bcm5974 are all very different. Common to all is that they use the Xorg synaptics driver to generate X events, which is what makes things such as the two-finger scroll to work.

So, the answer to your question is that for hardware drivers, you are stuck with the capabilities of the one working for your hardware.

---

### Post by undoIT on 2009-01-30
> **kosumi68 said:**
> The kernel hardware modules for trackpads are very much dependent on the actual hardware. The appletouch, synaptics and bcm5974 are all very different. Common to all is that they use the Xorg synaptics driver to generate X events, which is what makes things such as the two-finger scroll to work.

So, the answer to your question is that for hardware drivers, you are stuck with the capabilities of the one working for your hardware.

Thanks Kosumi. So then, it is pretty much guaranteed that the current appletouch driver won't work with the XPS 16. Do you think it would be very difficult to take what has been done in that driver and create a new driver for the XPS 16? Pardon my terminology.

---

### Post by kosumi68 on 2009-01-30
> **undoIT said:**
> Thanks Kosumi. So then, it is pretty much guaranteed that the current appletouch driver won't work with the XPS 16. Do you think it would be very difficult to take what has been done in that driver and create a new driver for the XPS 16? Pardon my terminology.

It sounds like the synaptics *kernel* driver, which I believe is baked into psmouse, might do the job. That driver also has two-finger capabilities. This is not really an apply question, is it :-)

---

### Post by undoIT on 2009-01-30
> **kosumi68 said:**
> This is not really an apply question, is it :-)

Was my terminology a give away? :???:

---

### Post by andrew.mckevitt on 2009-01-30
I'm on an eeepc running eeebuntu, I have two finger scroll, two finger tap(open in new tab) and 3 finger tap(right click) working out of the box. If you have the hardware, *buntu may just be able to use it.

---

### Post by undoIT on 2009-01-30
Hot Diggity! I've got two finger scrolling and two finger right click tapping working on my Dell XPS M1330.

Here's what I did to get it working:

Copy settings and open copied file to edit:

```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```

Then I added this to the file that is open:

```
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
```

You need to add those settings after the closing </match> for whatever input device you have i.e. Alps / Synaptic. My edited file looks like this:
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
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">80</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
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
        <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
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
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

Save and reboot. You have to reboot, a logout and login won't show the changes.

There is still some fine tuning to do. The two finger scrolling is a little quirky. In Firefox, sometimes after releasing the two fingers to scroll, the window scrolls backwards. This isn't an issue on my MacBook. Not sure what to adjust to prevent this from happening.

---

### Post by cyberdork33 on 2009-01-31
ah, i see... the actions you are talking about are actually not multitouch actions... they have been supported on most synaptics touchpads for a very long time...

---

### Post by undoIT on 2009-01-31
> **cyberdork33 said:**
> ah, i see... the actions you are talking about are actually not multitouch actions... they have been supported on most synaptics touchpads for a very long time...

And I thought my MacBook was so special ;)

Really, all I use is the two finger scroll and two finger right click. The other ones are kind of gimmicky imo.

The sensitivity seems off when I have those two features enabled on the M1330 synaptics touchpad. If I do a tap right click in a long web document, it often scrolls down. Sometimes if I get it just right it works. Also, the two finger scrolling can be jumpy after release. Both issues seem to be related to having the sensitivity to high for detecting two fingers. Perhaps if the timing interval could be adjusted so that it is more forgiving. Is it possible to adjust this?

Would these values have any effect:

```
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>

```

It is kind of hard to test things because you have to reboot each time.

---

### Post by cyberdork33 on 2009-01-31
> **undoIT said:**
> And I thought my MacBook was so special ;)

Really, all I use is the two finger scroll and two finger right click. The other ones are kind of gimmicky imo.

The sensitivity seems off when I have those two features enabled on the M1330 synaptics touchpad. If I do a tap right click in a long web document, it often scrolls down. Sometimes if I get it just right it works. Also, the two finger scrolling can be jumpy after release. Both issues seem to be related to having the sensitivity to high for detecting two fingers. Perhaps if the timing interval could be adjusted so that it is more forgiving. Is it possible to adjust this?

Would these values have any effect:

```
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>

```It is kind of hard to test things because you have to reboot each time.
You should just have to restart hal

---

### Post by undoIT on 2009-01-31
> **cyberdork33 said:**
> You should just have to restart hal

"I'm sorry Dave, I'm afraid I can't do that." ;)

Here's the command to restart HAL:
```
sudo /etc/init.d/hal restart
```

Doesn't seem to be working. I changed the configuration file to disable scrolling, restarted HAL, but scrolling is still working.

---

### Post by cyberdork33 on 2009-01-31
> **undoIT said:**
> "I'm sorry Dave, I'm afraid I can't do that." ;)

Here's the command to restart HAL:
```
sudo /etc/init.d/hal restart
```Doesn't seem to be working. I changed the configuration file to disable scrolling, restarted HAL, but scrolling is still working.
hmm. ok maybe xorg too. :)

---

### Post by boomshop on 2009-02-02
Hi, perhaps this one will make your experience less choppy:

```

<merge key="input.x11_options.VertScrollDelta" type="string">40</merge>

```

VerticalScrollDelta sets the minimum movement required to start scrolling. Same goes for HorizScrollDelta.

---

### Post by undoIT on 2009-02-02
@ cyberdork: restarting HAL and then logout out login does work for testing adjustments.

@ boomshop: thanks for the suggestion. tried adding that line and it doesn't seem to make a difference. i wouldn't really say that the motion is choppy. it just seems that the touchpad is too sensitive for detecting when two fingers are pressed and when one of the fingers leaves the touchpad after scrolling. i have found that touching my fingers together while scrolling makes it work better (less margin of error for when two fingers are no longer touching the pad).

it is nearly impossible to get a right click in a long document. if I try and right-click with two fingers in Firefox, the window almost always scrolls to the bottom of the document and then opens the contextual menu.

---

### Post by Bobber76 on 2009-05-19
deleted: missed topic

---

### Post by bonfire89 on 2009-09-08
It seems like the fingers have to be set wider... it tries to scroll when using a single finger.

---

### Post by Tompalaz on 2009-09-09
Two finger scroll and two-finger tap rightclick works like a charm with my MacBook (5,1).

I used a program from Add/remove called Touchpad.

I'm using Karmic.

> tomas@MacintoshLinux:~/Desktop$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu karmic (development branch)
Release:	9.10
Codename:	karmic
2.6.31-9-generic

---

### Post by gwydionwaters on 2009-09-16
8.10 ppc g4
i tried this method and it didn't work for me, i then tried editing the original location, /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi but that has not seemed to make a difference either. this is one thing i would love to get working, or even a vertical edge scroll. i do not have xorg conf, i tried to use it and it hugely messed up my system lol

---

