---
title: "Apple Unibody Trackpad Driver"
date: 2010-04-05
forum: Apple Hardware Users
---

### Post by cph05a on 2010-04-05
Is there already a perfect unibody trackpad driver out there? I started working on some improvements on the driver listed in the *[MacBookPro5-5/Karmic]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Touchpad")* page and I'm wondering if I should see this through to completion and put it online, or if I'm just reinventing the wheel.

---

### Post by lvleph on 2010-04-05
I don't know of one. I have not put Linux on my work machine for this exact reason. If at all possible I would like to make a request. Could you have it simulate a middle click using three finger clicks? This would make your driver better than OSX drivers.

---

### Post by cph05a on 2010-04-05
> Could you have it simulate a middle click using three finger clicks?

I can do that. It'd be great if you can help me test it once I add one or two more features.

---

### Post by lvleph on 2010-04-05
Sure, I will go ahead and install Ubuntu on it this weekend. Do you want me to test on Lucid or Karmic?

---

### Post by linuxopjemac on 2010-04-05
have a look [here]("http://ubuntuforums.org/showthread.php?t=1334696")

---

### Post by buntuLo on 2010-04-05
> **linuxopjemac said:**
> have a look [here]("http://ubuntuforums.org/showthread.php?t=1334696")
indeed.

and, by the way, two- and three-fingers tapping or clicking can be configured even with the driver installed by default:

```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/
sudo nano /etc/hal/fdi/policy/11-x11-synaptics.fdi
```
here you can experiment different settings. my modifications to the file are:
```
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
<merge key="input.x11_options.HorizScrollDelta" type="string">40</merge>
<merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
<merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
<merge key="input.x11_options.FingerLow" type="string">16</merge>
<merge key="input.x11_options.FingerHigh" type="string">80</merge>
<merge key="input.x11_options.FingerPress" type="string">256</merge>
<merge key="input.x11_options.PalmDetect" type="string">1</merge>
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
```
you can check the new settings with:
```
/usr/src/bcm5974-1.1.1/scripts/bcm5974-diagnostics
```
save the file and reboot the machine to enable the changes, or enable them on-the-fly (without rebooting) with:
```
sudo /etc/init.d/hal restart
```
and logging out and in again (to restart X11).

---

### Post by cph05a on 2010-04-05
> Sure, I will go ahead and install Ubuntu on it this weekend. Do you want me to test on Lucid or Karmic?

It doesn't matter me which one you try. You might want to try buntuLo's solution first and if you don't like it, I'll post my driver. Everything is finished except for one extra palm detection feature I plan to add.


Edit: it's finished. my driver doesn't use any fdi files or anything like that. Palm / thumb detection is always on. It was a fun little exercise I guess.

---

