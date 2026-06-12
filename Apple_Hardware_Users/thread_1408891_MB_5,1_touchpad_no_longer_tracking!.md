---
title: "MB 5,1 touchpad no longer tracking!"
date: 2010-02-16
forum: Apple Hardware Users
---

### Post by Jheric on 2010-02-16
I searched around on Google and the Ubuntu forums a good bit before posting... but I couldn't seem to find a post that had the same problem as me.

I'm on a newer Macbook (5,1) dual-booting OSX and Ubuntu 9.10

Despite some sensitivity frustrations that I was tweaking to be bearable, my touchpad was working fine.

Yesterday (day 2 since installation) I booted into Ubuntu and my touchpad was no longer working properly. It still clicks and right-clicks... but it doesn't track anymore and I cannot move the mouse with it. I've been using a usb mouse in the meantime, but this becomes a big problem when I need to be mobile.

Any recommendations on how I can "reset" the touchpad or something? I don't care if it's back to the default settings, I just need it back.

---

### Post by linuxopjemac on 2010-02-17
you could try this:

>    1.

      Create the file appletouch.fdi in the folder /etc/hal/fdi/policy:

      ```
sudo gedit /etc/hal/fdi/policy/appletouch.fdi
```

   2. Paste the following contents into the file:

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
          <merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>

          <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>

          <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
          <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
          <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
          <merge key="input.x11_options.LTCornerButton" type="string">false</merge>

          <merge key="input.x11_options.TopEdge" type="string">0</merge>
          <merge key="input.x11_options.LeftEdge" type="string">0</merge>
          <merge key="input.x11_options.RightEdge" type="string">1100</merge>
          <merge key="input.x11_options.BottomEdge" type="string">800</merge>

          <merge key="input.x11_options.FingerLow" type="string">5</merge>
          <merge key="input.x11_options.FingerHigh" type="string">15</merge>

          <merge key="input.x11_options.TapButton1" type="string">1</merge>
          <merge key="input.x11_options.TapButton2" type="string">3</merge>
          <merge key="input.x11_options.TapButton3" type="string">2</merge>

          <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
          <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
          <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

          <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
          <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
          <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

          <merge key="input.x11_options.PalmDetect" type="string">true</merge>
         </match>
        </match>
       </device>
      </deviceinfo>

```
   3. Restart the touchpad's kernel driver with the command:

    ```
  sudo modprobe -r appletouch && sudo modprobe appletouch

```
The following behavior should result:

    *

      Left click: one-finger tap or button press
    *

      Right click: two-finger tap or button press with two fingers on the pad
    *

      Middle click: three-finger tap or button press with three fingers on the pad
    *

      Vertical scrolling: move two fingers vertically 

---

### Post by Jheric on 2010-02-17
Thank you for the reply! Unfortunately, it didn't alter the behavior... I still get click function only and no tracking.

To confirm, it still works in Mac OSx, but not in Ubuntu =/.

I'll keep fiddling with it.

Any other recommendations are appreciated!

---

### Post by Jheric on 2010-02-17
Alright, thread solved!

I didn't pay attention to the instructions here because my touchpad was working fine.

Don't skip these steps! If you're have touchpad issues with your 5,1 install the drivers and make all of the changes in this help section:

[https://help.ubuntu.com/community/MacBook5-1/Jaunty#Trackpad](https://help.ubuntu.com/community/MacBook5-1/Jaunty#Trackpad)

Installing bcm5974-dkms and blacklisting usbhid was what the doctor ordered and it worked!

Thank you for you assistance.

---

### Post by teChM33 on 2010-02-17
Yea lucky you found that, I was reviewing it befor, I have not yet installed my Linux but was going to referee you there.

---

### Post by _mario_ on 2010-02-18
> **Jheric said:**
> Alright, thread solved!

I didn't pay attention to the instructions here because my touchpad was working fine.

Don't skip these steps! If you're have touchpad issues with your 5,1 install the drivers and make all of the changes in this help section:

[https://help.ubuntu.com/community/MacBook5-1/Jaunty#Trackpad](https://help.ubuntu.com/community/MacBook5-1/Jaunty#Trackpad)

Installing bcm5974-dkms and blacklisting usbhid was what the doctor ordered and it worked!

Thank you for you assistance.

did you observe the effect after rebooting or after resuming from suspend (to RAM or to disk)? this is important, because one of the features, the mactel version of bcm5974 adds, is to reset the device after resuming, effectively rendering this usbhid loading stuff useless. that solved the problem for me.

ciao,
Mario

---

### Post by Jheric on 2010-02-18
> **_mario_ said:**
> did you observe the effect after rebooting or after resuming from suspend (to RAM or to disk)? this is important, because one of the features, the mactel version of bcm5974 adds, is to reset the device after resuming, effectively rendering this usbhid loading stuff useless. that solved the problem for me.

ciao,
Mario

Actually, my suspend has been flawless. I experience no differences in my os or hardware behavior after a suspend (ram or disk). So yeah, I'm quite happy, at the moment.

---

