---
title: "[SOLVED] New kernel driver for the BCM5974 touchpad (Macbook Air, Penryn)"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by kosumi68 on 2008-06-25
UPDATED 25OCT2008

Apple USB BCM5974 (Macbook Air and Penryn Macbook Pro) multitouch driver

This driver adds support for the multitouch trackpad on the new
Apple Macbook Air and Macbook Pro Penryn laptops. It replaces the
appletouch driver on those computers, and integrates well with the
synaptics driver of the Xorg system. 

Known to work on Macbook Air, Macbook Pro Penryn and the new Unibody
Macbook 5 and Macbook Pro 5.

Support for the latest Macbooks is not upstream yet, but available in the mactel PPA.
Make sure you have these lines in /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main

```

When changing /etc/apt/sources.list, one needs to update:
```

sudo apt-get update

```

With the mactel PPA in place, install the bcm5974-dkms package
```

sudo apt-get install bcm5974-dkms

```

Enjoy!

For more information or troubleshooting, see [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/)

Credit for finding out how to initialize the trackpad goes to Scott Shawcroft and the touchd user-space driver.

---

### Post by kosumi68 on 2008-06-25
A new version of the bcm5974 driver is out, yielding a somewhat more stable trackpad motion. Some of the secondary motions like hand resting on the trackpad and accidental swiping of the trackpad are mostly ignored, even though it could be improved further.

I am curious to hear if anyone managed to make it work on the Macbook Pro Penryn?

---

### Post by kosumi68 on 2008-06-26
Edge scrolling does not mix very well with two-finger scrolling, I think. In either case, here are the exact trackpad dimensions of the bcm5974 driver:

```

        Option          "LeftEdge"              "0"
        Option          "RightEdge"             "1280"
        Option          "TopEdge"               "0"
        Option          "BottomEdge"            "800"

```

Setting the above lines in the /etc/X11/xorg.conf will in it self turn edge scrolling off, by leaving zero room around the edges. With my old settings, I experienced oddities like occasional corner taps; the new settings made that problem go away.

---

### Post by eddielgarcia on 2008-06-26
Not to sound ignorant but i am kinda new.  Once this module has been appended to the kernel how does one go about and configure the touchpad device?  Is there a .conf file somewhere or does a GUI app take care of that for you.  I just appended it and I don't know how to determine its inner working.  Thanks for any new info on this module.


Ed


MB Air 1.6 Ghz 2GB RAM and the works!!!!

---

### Post by kosumi68 on 2008-06-26
There is a nice introduction to synaptics configuration in the sticky thread on top of the page: [http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

Did you get the driver working? What is the output of this command:

```

synclient -l

```

---

### Post by eddielgarcia on 2008-06-26
Hmmm maybe i did something wrong during the setup when i run the command given this is my output:


xxxx@xxxx-air:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?


When I followed the above link I did not compile I went with the first option.  Any ideas?

Ed

---

### Post by kosumi68 on 2008-06-27
It might be several different things:

1. The mouseemu module interfers with the touchpad motion, please stop it.

2. The bcm5974 might not be loaded properly (most likely case).

3. The usbhid and bcm5974 seems to compete to claim the device (hence the module ordering in the download instructions).

4. Something else, there are tips in this thread: [http://ubuntuforums.org/showthread.php?t=795830](http://ubuntuforums.org/showthread.php?t=795830)

To test 2), unload the bcm5974 driver, load it again, and check the dmesg output. You should see these lines:

```

 usbcore: deregistering interface driver bcm5974
 input: bcm5974 disconnected
 bcm5974: Wellspring mode initialized.
 input: bcm5974 as /devices/[somepath]
 usbcore: registered new interface driver bcm5974

```

If the input: line does not appear, the device could not be claimed, suggesting some other module got to it first. If the wellspring mode is not initialized, the device could not be found, meaning the device detection failed. It would be very helpful if you can provide the usb details of your machine:

```

sudo lsusb -v | grep -B1 idProduct

```

---

### Post by eddielgarcia on 2008-06-27
Here is the output of **sudo lsusb -v | grep -B1 idProduct**

  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x8505 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x0223 
--
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x8242 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x820b 
--
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x820a 
--
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x8210 
--
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4500 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x0000 
  idProduct          0x0000 
--
  idVendor           0x0000 
  idProduct          0x0000 


Here you go I will attempt to unload and redo steps let me know if you see anything.  

More Info:
     I places this entry in my blacklist:
[B]    # put in place to support touchpad driver macbook air
    usbhid[/B]

    This in my entry in modules:

    # /etc/modules: kernel modules to load at boot time.
    #
    # This file contains the names of kernel modules that should be loaded
    # at boot time, one per line. Lines beginning with "#" are ignored.

    fuse
    lp
    ndiswrapper
    usbnet
    patasix
    bcm5974
    usbhid

---

### Post by kosumi68 on 2008-06-27
From the looks of it, you have a macbook air, and the same module loading order as in my setup. I am very curious as to what your dmesg says as you unload and reload the bcm5974 driver.

UPDATE: the post above should read "blacklist usbhid", as explained in succeeding posts.

---

### Post by eddielgarcia on 2008-06-27
To "unload the module" do I just remove the file that I added into the kernel directory and depmod again?  What exactly is the procedure for "removal".  I will try both and output the dmesg when I do that.

---

### Post by _alex_ on 2008-06-27
> **eddielgarcia said:**
> 
     I places this entry in my blacklist:
[B]    # put in place to support touchpad driver macbook air
    usbhid[/B]


Shouldn't that read "blacklist usbhid" instead of just "usbhid", or does that make no difference?

Alex

---

### Post by kosumi68 on 2008-06-27
__alex__ is absolutely right -- it should say "blacklist usbhid" in the /etc/modprobe.d/blacklist file, and "usbhid" in the /etc/modules file. I was being too implicit. As to the unloading and loading, these are the commands to use:

```

sudo rmmod bcm5974
sudo modprobe bcm5974

```

---

### Post by _alex_ on 2008-06-27
> **kosumi68 said:**
> I am curious to hear if anyone managed to make it work on the Macbook Pro Penryn?

Hello Henrik,

I'm currently using BCM5974 version 0.3 on a Macbook Pro 4,1 (penryn, touchpad device id is 0x230). It seems to work quite well now. I can scroll with two fingers, and right click with two-finger+mouse click. Tap to click doesn't seem to work; also unless I use the tip of my finger to move the mouse, it begins to scroll instead (probably need to adjust the sensitivity...)

It also stops working after a while, and I'm not sure why... The last thing I see in dmesg is:
```

[ 1404.650701] hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[ 1404.656488] bcm5974: Wellspring mode initialized.
[ 1404.656596] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.2/input/input19

```

Great work though, I think once the kinks are ironed out it's probably going to be the best short term solution (at least until touchd becomes more mature, or the synaptics driver is extended with more advanced multitouch stuff).

Alex

---

### Post by kosumi68 on 2008-06-27
Great, thanks for trying it out! The finger-starts-to-scroll is the FingerPress option of synaptics; the 0.3 version reported a bit too sensitive pressure information. Version 0.31 remedies that. These are my pressure settings in synaptics:

```

        Option          "FingerLow"             "16"
        Option          "FingerHigh"            "23"
        Option          "FingerPress"           "256"

```

The tap click works: I normally run without it, but these are my settings for tapping:

```

        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "223"
        Option          "MaxDoubleTapTime"      "200"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        #Option          "TapButton1"            "0"

        # not using corner buttons
        Option          "RTCornerButton"         "0"
        Option          "RBCornerButton"         "0"
        Option          "LTCornerButton"         "0"
        Option          "LBCornerButton"         "0"  

```

Also, it is important to set the dimensions of the device as in a previous post in this thread.

In what way does it stop working?

---

### Post by _alex_ on 2008-06-27
I can confirm that 0.31 fixes single finger scrolling. Tap click also works with the changes you described (I use your xorg settings on [http://web.comhem.se/rydberg/Bits/xorg-settings.html](http://web.comhem.se/rydberg/Bits/xorg-settings.html), save for the midifications for tap clicking).

The mouse stops moving. The mouse button still works, and bcm5974 is still listed in "lsmod". Restarting X fixes the issue. Let me know if there's any other info I should get for you to help you debug this.

---

### Post by eddielgarcia on 2008-06-28
I think the issue with my touchpad device has been fixed.  Once I blacklisted that one driver correctly my touchpad began to work, but when I also used the xorg.conf setting as seen online my touchpad: lost all secondary functionality, and it seemed as if the standard mouse driver was running.  Going to dry disabling some options to see if that remedies my situation!  Thanks for your help this is what helps the ubuntu family grow!

Ed

---

### Post by lloeki on 2008-06-28
excellent work.

still, I have a macbook pro 4,1 penryn and encounter an issue. while two finger scrolling does work, two finger right clicking does not. pretty annoying... especially when I'm so close to make it work.

I am using the xorg.conf excerpt yet it seems to ignore the 'Option          "MultiFingerButton"     "2"'... weird:
```

(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) TouchPad auto-dev sets device to /dev/input/event12
(**) Option "Device" "/dev/input/event12"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "0"
(**) Option "RightEdge" "1280"
(**) Option "TopEdge" "0"
(**) Option "BottomEdge" "800"
(**) Option "VertScrollDelta" "40"
(**) Option "HorizScrollDelta" "0"
(**) Option "FingerLow" "16"
(**) Option "FingerHigh" "23"
(**) Option "FingerPress" "256"
(**) Option "MaxTapTime" "223"
(**) Option "MaxTapMove" "100"
(**) Option "MaxDoubleTapTime" "200"
(**) Option "VertEdgeScroll" "0"
(**) Option "HorizEdgeScroll" "0"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "RTCornerButton" "0"
(**) Option "RBCornerButton" "0"
(**) Option "LTCornerButton" "0"
(**) Option "LBCornerButton" "0"
(**) Option "TapButton1" "0"
(**) Option "TapButton2" "0"
(**) Option "TapButton3" "0"
(**) Option "PressureMotionMinZ" "10"
(--) TouchPad touchpad found
(**) Option "SendCoreEvents"
(**) Option "CorePointer"
(**) TouchPad: always reports core events

```

fwiw it seems to initialize fine:
```

Jun 28 20:56:37 metal usbcore: registered new interface driver bcm5974
Jun 28 20:56:37 metal bcm5974: Wellspring mode initialized.
Jun 28 20:56:37 metal input: bcm5974 as /class/input/input12

```

to be fair, I don't use ubuntu but arch linux. I feel like I'm missing something obvious.

---

### Post by kosumi68 on 2008-06-28
Looking for the obvious then... I take it you are using the mactel version of the synaptics X11 driver? What kernel version are you using? What is your output of "synclient -l"? :-)

---

### Post by lloeki on 2008-06-28
```
$ synclient -l
Parameter settings:
    LeftEdge                = 0
    RightEdge               = 1280
    TopEdge                 = 0
    BottomEdge              = 800
    FingerLow               = 16
    FingerHigh              = 23
    FingerPress             = 256
    MaxTapTime              = 223
    MaxTapMove              = 100
    MaxDoubleTapTime        = 200
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 257
    VertScrollDelta         = 40
    HorizScrollDelta        = 0
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 0.8
    MaxSpeed                = 1.2
    AccelFactor             = 0.1
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 80
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 0
    PressureMotionMinZ      = 10
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1

```

```
$ pacman -Q synaptics
synaptics 0.14.6.99-2

```


```
$ pacman -Q kernel26
kernel26 2.6.25.6-1

```

---

### Post by lloeki on 2008-06-28
> I take it you are using the mactel version of the synaptics X11 driver?
ahem? is there a special version for mactels? this would explain a lot.

---

### Post by lloeki on 2008-06-28
nevermind, I found it there: [http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/x/xfree86-driver-synaptics/](http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/x/xfree86-driver-synaptics/)

a quick grep on the diff revealed me that it effectively adds the relevant option. built it and it works like a charm. thanks for the assistance!

---

### Post by kosumi68 on 2008-06-28
Yes, the MultiFingerButton option has not made it all the way yet. That makes you the second documented penryn user. Great! Are you experiencing any flavor of the problem __alex__ is describing?

---

### Post by lloeki on 2008-06-29
up till now, nothing like that.

all in all, it works like a charm. this module is really a much better solution than touchd, as I don't think this should belong to userspace, and it has no funky dependencies (openusb comes to mind). I like this KISS spirit, the ArchLinux way :)

---

### Post by kosumi68 on 2008-06-29
Lovely, lovely. :) Then this is for alex: are you by any chance running touchd in the background? It would interfere with the device, in particular any device reset would confuse synaptics.

I looked into the device initialization a bit, trying to get rid of the need to blacklist usbhid. The current kernel seems to miss out on the mouse-ignore quirk for the MBA and Penryn (aka wellspring devices). These should be the right quirks to use in /etc/modprobe.d/options:

```

# for MBA
options usbhid quirks=0x05ac:0x0223:0x00020800,0x05ac:0x0224:0x00024800,0x05ac:0x0225:0x00020800
# for Penryn
options usbhid quirks=0x05ac:0x0230:0x00020800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00020800

```

UPDATE: the quirk table above has been corrected according to succeeding posts.

For those who compile their own kernel, here are the correct lines to use in drivers/hid/usbhid/hid-quirks.c:

```

	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING_ANSI, HID_QUIRK_APPLE_HAS_FN | HID_QUIRK_IGNORE_MOUSE },
	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING_ISO, HID_QUIRK_APPLE_HAS_FN | HID_QUIRK_APPLE_ISO_KEYBOARD | HID_QUIRK_IGNORE_MOUSE},
	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING_JIS, HID_QUIRK_APPLE_HAS_FN | HID_QUIRK_IGNORE_MOUSE},
	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING2_ANSI, HID_QUIRK_APPLE_HAS_FN | HID_QUIRK_IGNORE_MOUSE},
	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING2_ISO, HID_QUIRK_APPLE_HAS_FN | HID_QUIRK_APPLE_ISO_KEYBOARD | HID_QUIRK_IGNORE_MOUSE },
	{ USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_WELLSPRING2_JIS, HID_QUIRK_APPLE_HAS_FN  | HID_QUIRK_IGNORE_MOUSE },

```

With one of the two options above in effect, one can drop the usbhid from the /etc/modprobe.d/blacklist, and just add bcm5974 to /etc/modules.

---

### Post by kosumi68 on 2008-06-29
Version 0.4 of the driver is out, adding the finger width reading to the synaptics interface: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/).

The idea here is that given the finger size, one can determine if its a clean index finger, a bulky thumb, or the whole palm touching the trackpad. Based on this, one can determine what action should be taken. We all know how annoying it is to accidentally touch the trackpad while writing a mail, for instance. :)

Unfortunately, the palm detection feature of synaptics seems to be completely broken, so the palm feature will have to be turned off awaiting a fix to synaptics. These are the relevant settings in /etc/X11/xorg.conf:

```

        Option          "PalmDetect"             "0"
        Option          "PalmMinWidth"           "180"
        Option          "PalmMinZ"               "10"  

```

Anyone feel like giving synaptics a treat, please go ahead :)

PS: one can see the finger size reading running "sudo synclient -m 100". Pretty cool. DS.

---

### Post by _alex_ on 2008-06-29
Hello Henrik,

I messed around with xorg.conf, and the touchpad has not frozen on me in a couple of days. I think it had to do with an external mouse that I always had attached. I mapped the external mouse to "/dev/input/mice", and the touchpad to "/dev/psaux/" in xorg.conf, and that seems to have done it...

As for the dynamic quirks, it will work with the following modification:
*Edit: see kosumi68's post above.*
(HID_QUIRK_IGNORE_MOUSE is defined as 0x00020000 in hid.h)

Good work!

Edit: And it just locked up again :(  This is running v0.41, but this time dmesg did capture something useful. The lockup happened right after I tried a two-finger right click, and the following messages appeared in dmesg:
```

[  885.095826] usb 5-2: USB disconnect, address 5
[  885.152487] input: bcm5974 disconnected
[  885.218634] usb 5-2: new full speed USB device using uhci_hcd and address 6
[  885.269833] usb 5-2: configuration #1 chosen from 1 choice
[  885.278812] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.0/input/input16
[  885.333494] input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  885.615309] hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  885.621106] bcm5974: Wellspring mode initialized.
[  885.621217] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.2/input/input17

```
After this, the touchpad button works, but the trackpad does not.

---

### Post by _alex_ on 2008-06-29
Okay, I'm pretty sure I know what it is now. My macbook pro seems to suffer from this problem: [http://discussions.apple.com/thread.jspa?threadID=1365569&tstart=75](http://discussions.apple.com/thread.jspa?threadID=1365569&tstart=75)

The flaky keyboard/trackpad connection causes the device to disconnect shortly (this explains the correlated keyboard and trackpad messages in dmesg), which causes the bcm5974 driver issues . I guess I'll have to bring my macbook in for repairs.

---

### Post by kosumi68 on 2008-06-29
Ooops - your quirk table is exactly what I thought I tested, thanks for finding the problem :)

So your device reinitiates spontaneously? After the initialization, the synaptics driver most likely loses track of what device to read from - do you have the output of /var/log/Xorg* from the same time?

---

### Post by lloeki on 2008-06-29
currently I'm using these quirks to make fn key work:
```
options usbhid quirks=0x05ac:0x0230:0x00000800,0x05ac:0x0231:0x00004800,0x05ac:0x0232:0x00000800
```

is the last part wrong? do you suggest I add 0x0225:0x00020800 at the end? do you suggest I add +0x00020000 to each value? could you give a short explanation of what it all means?

---

### Post by kosumi68 on 2008-06-29
Sometimes the simplest things are the hardest - apparently alex' correction needs a correction, too :-) Check my edited post for the (hopefully!) correct lines.

The quirks look very mysterious and woodoo-like, until one reads the kernel code. It is all about performing special tasks for particular devices, things that have not yet made it to the driver code. For instance "0x05ac:0x0232:0x00020800" means: "apple device penryn has the FN key and the mouse device should be ignored" (to be initialized by bcm5974). The difference between 0x0230, 0x0231 and 0x0232 is where the computer is manufactured (dont know much about the details). In principle, you should only need to use the code for your own device (found with the lsusb command).

---

### Post by _alex_ on 2008-06-29
> **kosumi68 said:**
> Sometimes the simplest things are the hardest - apparently alex' correction needs a correction, too :-) Check my edited post for the (hopefully!) correct lines.

Whoops, sorry. I jsut cut and pasted your lines of code and added the 2's without checking the product/device ids :)  I'll edit my post above so as not to confuse readers any further ;)

As for the Xorg log. I can't make much sense of it. The last couple of lines right after a touchpad freeze read:
```
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(--) Synaptics Touchpad touchpad found
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

```

In any case, I'm now very certain that it's due to the faulty connection. I'll let Apple repair/replace my laptop, and we'll see if the problem persists then. Thanks for your help!

---

### Post by kosumi68 on 2008-06-30
Ok, let us recapitulate the current status of the bcm5974 driver:

* Two confirmed users on Macbook Air (productId: 0x0223)

* Two confirmed users on Macbook Pro Penryn (productIds: 0x0230, 0x0231)

* Versions 0.41 and 0.31 both seem stable.

Download page: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/)

Version 0.31 was submitted to kernel.org (pending).

That about wraps it up. If you have ideas on how to incorporate this into the next ubuntu kernel release, please advice. Frankly I do not know where to turn. :-)

Cheers!

---

### Post by lloeki on 2008-06-30
> * Two confirmed users on Macbook Pro Penryn (productIds: 0x0230, 0x0232)
here's my lsusb. isn't that 0x231 instead?
```
$ lsusb
Bus 003 Device 003: ID 05ac:8502 Apple Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0002  
Bus 007 Device 005: ID 05ac:0231 Apple Computer, Inc. 
Bus 007 Device 004: ID 05ac:8242 Apple Computer, Inc. 
Bus 007 Device 001: ID 1d6b:0001  
Bus 006 Device 001: ID 1d6b:0001  
Bus 005 Device 004: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0002  
Bus 004 Device 001: ID 1d6b:0001  
Bus 001 Device 008: ID 05ac:820b Apple Computer, Inc. 
Bus 001 Device 007: ID 05ac:820a Apple Computer, Inc. 
Bus 001 Device 006: ID 05ac:820f Apple Computer, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001  

```

again, excellent work. will try 0.41 as soon as I get some time on my hands.

---

### Post by lloeki on 2008-06-30
Ah just right now I got no touchpad working:

> TouchPad no synaptics event device found (checked 25 nodes)
Query no Synaptics: 000000
(EE) TouchPad no synaptics touchpad detected and no repeater device
Query no Synaptics: 000000
Query no Synaptics: 000000
Synaptics driver lost sync... got gigantic packet!
Query no Synaptics: 000000
Query no Synaptics: 000000
Query no Synaptics: 000000
Synaptics driver lost sync... got gigantic packet!

but then it suddently started working... barely. it moves, it scrolls?? but no right click... I can understand it moving because of /dev/input/mice, but the scrolling... how could this be when synaptics X driver failed to load?

---

### Post by kosumi68 on 2008-06-30
Absolutely, 0x0231 it is then. Please note the different quirk for that machine, as it is using a different keyboard layout.

So what did you do? Install 0.41? Try out the quirk settings? Or something else? I need something to go on :)

---

### Post by kosumi68 on 2008-06-30
Checking the synaptics source code, it seems the device fell back to the psaux protocol, and something non-mouse-like was received on some device. In /etc/X11/xorg.conf, I can think of two protocol settings that work: either auto-dev or event. If you just tried out the quirk settings, it could explain the behavior, assuming something went wrong when initializing bcm5974 and your error turned up as you restarted the machine.

---

### Post by lloeki on 2008-06-30
I happened to have the error at some point after a resume from s2ram, dunno exactly when, as I was using a mouse until I noticed it.

this was before I made any modification to my quirks (which were there solely to make fn key work), and using rmmod usbhid && modprobe bcm5974 && modprobe usbhid.
since then I began using the latest quirks line, which indeed works without the rmmod trick.

currently xorg.conf reads like this:
```
Section "InputDevice"
        Identifier      "TouchPad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        Option          "CorePointer"
        blahblahblah

```

btw two finger+click gives button 2, but I was happily surprised that three fingers+click gives button 3! excellent for copy-pasting!
now I wish it worked also on the vt consoles...

---

### Post by lloeki on 2008-06-30
it happened again. touchpad can't move, click works, keyboard works.

this seems tied to entering suspend mode and/or external usb mouse (un)plugging.

when this happens, restarting X (and thus reinitializing synaptics driver) makes it behave correctly.

---

### Post by _alex_ on 2008-06-30
> **kosumi68 said:**
> If you have ideas on how to incorporate this into the next ubuntu kernel release, please advice. Frankly I do not know where to turn. :-)

You could try one of the mailing lists, I've had success there before: [https://lists.ubuntu.com/](https://lists.ubuntu.com/)
Perhaps kernel-team is the one to contact.

lloeki, if you're running bcm5974 v0.41 make sure to include the palm lines in the synaptics section of xorg.conf, otherwise you might get some weirdness like what you describe.

---

### Post by lloeki on 2008-06-30
also, could you please separate binary and source in two different release files?

this is somehow important for external packagers (like me) who fetch and build automatically (think gentoo ebouild, archlinux pkgbuild): it is cumbersome to have the ubuntu kernel verison in the zip filename, and useless to have the binaries...

I'd sggest: 
- bcm5974-0.41-2.6.24-19-generic.zip for binary
- bcm5974-0.41-src.zip for source

---

### Post by magaio on 2008-06-30
Hey guys, I'm having trouble getting this to work properly. I've followed the directions for a binary install of the current driver and I'm not getting right-click or scrolling.

Right now, I'm 2.6.24-19-generic

xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
        # updated 2007-12-07
        # use command "synclient -m 1" to see raw output
        # common stuff
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        
        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        
        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" # set to 0 if you don't want horizontal scrolling
        
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "10"
        Option          "VertScrollDelta"       "10"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers if you like to push hard
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20" # change to 30 or 40 if you like

        # borders based on output from synclient
        Option          "LeftEdge"              "20"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "20"
        Option          "BottomEdge"            "370"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8" # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2" # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "100"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"

        # must be commented out or normal tapping wont work
        #Option         "TapButton1"            "0"

        # needed for disabled while typing fix  
        Option          "SHMConfig"             "on"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```


/etc/modules includes:
bcm5974
usbhid

/etc/modprobe.d/blacklist includes:
blacklist usbhid

Xorg.0.log snippet:

```
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
```

kernel messages:
```

Jun 30 12:42:18 mbpu kernel: [  272.176926] usbcore: deregistering interface driver bcm5974
Jun 30 12:42:30 mbpu kernel: [  275.535817] usbcore: registered new interface driver bcm5974
Jun 30 12:42:40 mbpu kernel: [  278.759654] usbcore: deregistering interface driver bcm5974
Jun 30 12:46:42 mbpu kernel: [  330.507230] usbcore: registered new interface driver appletouch
Jun 30 12:47:01 mbpu kernel: [  334.941114] usbcore: registered new interface driver bcm5974
```

Installed synaptic driver:
0.14.7~git20070706-mactel1

Kernel messages after rmmod and modprobe of bcm5974:
```
Jun 30 13:20:51 mbpu kernel: [  943.608044] usbcore: deregistering interface driver bcm5974
Jun 30 13:21:00 mbpu kernel: [  945.555609] usbcore: registered new interface driver bcm5974
```


I hope someone can help me out...this one last thing is all I need to complete this installation! :D

---

### Post by kosumi68 on 2008-06-30
I see... So both the penryn computers displays this reinitialization problem, related to suspend (to ram or disk?) and/or usb connect/disconnect. I tried reproducing this problem on my MBA by plugging and unplugging a usb mouse, but it is stable. Thus, my current conjecture is that this problem only occurs on the penryn computers. Now the question is: where is the source of this problem? It does not seem like anything one can fix in the bcm5974 driver.

---

### Post by firewing1 on 2008-06-30
I wanted to say thank you for the great driver, I was working on a kernel-module myself but yours is much better :)

I can confirm this works perfectly on a MacBook Pro 4,1 running Fedora 9 (kernel 2.6.25.6-57.fc9). In Fedora, usbhid isn't compiled as a module so I can't unbind the trackpad by blacklisting it. However, somebody showed me this trick:
```
echo -n '7-2:1.2' > /sys/bus/usb/drivers/usbhid/unbind
```
('7-2:1.2' is the USB ID of your trackpad. You can check the output of "dmesg" to find it out, but that should be the same for all MacBook Pro 4,1s sold in North America.)

The code above will keep usbhid loaded, but simply prevent it from grabbing the trackpad before bcm5974 can. You can use this trick if you need to keep usbhid loaded for other devices (ie, external keyboard) but still want to use bcm5974 for the trackpad.

Will double-finger-click=right-click and triple-finger-swipe be supported in a future versions? Also, do you have any plans to support gestures with Multi-Pointer X?

Firewing1

---

### Post by kosumi68 on 2008-06-30
Hi magaio, there are several problems with your setup, it seems:

* Try the quirk settings of a previous post in this thread, it is a better solution than blacklisting the usbhid. Your output shows the bcm5974 is not claiming the device, suggesting something else grabbed it first.

* Please provide the output of lsusb for further checking and productID reference.

* The xorg.conf has bad trackpad dimensions and is missing the VertTwoFingerScroll option. Please check a previous post in this thread for links to good settings.

Something to start with :)

---

### Post by kosumi68 on 2008-06-30
Hi firewing, thanks for reporting! Neat trick also :) Using the quirks in a previous post in this thread is another way to go, it seems quite stable.

Double-finger-click = right-click *is* supported, check the xorg.conf settings in this thread.

Swiping... how is that one supposed to work? :)

I never used MPX, so have not given it (that) much thought. I did get inspired by Jeff Han's demos, though :)

---

### Post by kosumi68 on 2008-06-30
Alex, thanks, I will give the mailing list a try.

Lloeki, the next release will have source and binaries separated :)

---

### Post by magaio on 2008-06-30
Hi everyone. I got it to work. I think I just fudged up the process at some point.

Here's what I did:

[LIST=1]
[*]Uninstalled linux-image and modules packages
[*]Reinstalled linux-image and modules (current highest version)
[*]reinstalled xserver-xorg and xserver-xorg-core packages
[*]removed all files related to BCM5974 and the KO module
[*]blacklisted appletouch and usbhid
[*]added bcm5974 and usbhid to /etc/modules
[*]rebuilt bcm5974 from source and copied to the module folder from bits' instructions
[*]pasted the inputdevice section from the website over into my xorg.conf file
[*]rebooted
[*]yay
[/LIST]

Right click also works. SCORE. Perhaps we need a clearer install doc?

---

### Post by firewing1 on 2008-06-30
> **kosumi68 said:**
> Hi firewing, thanks for reporting! Neat trick also :) Using the quirks in a previous post in this thread is another way to go, it seems quite stable.

Double-finger-click = right-click *is* supported, check the xorg.conf settings in this thread.

Swiping... how is that one supposed to work? :)

I never used MPX, so have not given it (that) much thought. I did get inspired by Jeff Han's demos, though :)
What version of synaptics are you using? I have 0.14.6 and it says "MultiFingerButton" isn't recognized :confused:
Edit: Hm, I enabled tapping in xorg.conf by uncommenting the TapButton2/3 lines and it works now, but only with tapping enabled. Double-finger + button click doesn't produce a right-click but I believe this is a bug in synaptics, not your driver ;)

For the swiping, a triple finger "swipe" (really just a left/right movement) moves back/forward in Firefox or the file browser. Apple also has a rotate gesture for pictures which is pretty neat.

I have a technical question - is the finger detection done in synaptics or the actual kernel module? One thing I've noticed is two-finger taps don't always scroll (the mouse just jumps across the screen like on older laptops when you have one finger down and put another on the trackpad). 

It's tricky reproducing it, but one way I found that works most of the time is to put one finger on the trackpad, start moving it and then try to scroll up/down by adding a second finger. synclient shows that two fingers are detected which is odd...

Firewing1

---

### Post by kosumi68 on 2008-06-30
Magaio, great! There are good wiki pages for both MBA and Penryn, but perhaps we could update them now as the procedure seems to stabilize somewhat. If you want to give it a go, please do - I dont mind a little help :)

What is the output of lsusb on your computer, please?

---

### Post by magaio on 2008-06-30
lsusb output:

```
Bus 007 Device 003: ID 05ac:8502 Apple Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 05ac:0230 Apple Computer, Inc. 
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c044 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 05ac:820b Apple Computer, Inc. 
Bus 001 Device 005: ID 05ac:820a Apple Computer, Inc. 
Bus 001 Device 004: ID 05ac:820f Apple Computer, Inc. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by kosumi68 on 2008-06-30
> **firewing1 said:**
> What version of synaptics are you using? I have 0.14.6 and it says "MultiFingerButton" isn't recognized :confused:
Edit: Hm, I enabled tapping in xorg.conf by uncommenting the TapButton2/3 lines and it works now, but only with tapping enabled. Double-finger + button click doesn't produce a right-click but I believe this is a bug in synaptics, not your driver ;)


The synaptics version is 0.14.7~git20070706-mactel1, you need to add the mactel repositories to get it via the package manager.

> **firewing1 said:**
> 
For the swiping, a triple finger "swipe" (really just a left/right movement) moves back/forward in Firefox or the file browser. Apple also has a rotate gesture for pictures which is pretty neat.


Ok - then you only need to enable horizontal scroll in xorg.conf and in your trackpad configuration (System/Preferences/Touchpad) :)

I believe there is (at least experimental) support for rotation in the synaptics driver, something to think about...

> **firewing1 said:**
> 
I have a technical question - is the finger detection done in synaptics or the actual kernel module? One thing I've noticed is two-finger taps don't always scroll (the mouse just jumps across the screen like on older laptops when you have one finger down and put another on the trackpad). 

It's tricky reproducing it, but one way I found that works most of the time is to put one finger on the trackpad, start moving it and then try to scroll up/down by adding a second finger. synclient shows that two fingers are detected which is odd...


The finger detection is done in the driver.
Indeed, I have noticed one or two other things like this. It is my intention to see what can be done about it. :)

---

### Post by firewing1 on 2008-06-30
Excellent, let me know if need any help... I'm still learning my way around programming kernel modules, but I'll offer any help I can.

Hm, your driver seems to have the same problem as mine as well - the mouse moves across the screen just by touching various parts of the touchpad. Try for example starting on the top-left side of the touchpad, make 5 taps downwards to reach the bottom-left corner then make 10 taps to get to the bottom right corner. In my case the tapping still works, but the mouse jumped across 1/2 the screen. Maybe this is what's causing the double-finger scroll to fail? I've noticed that typically when it the scroll doesn't happen the mouse jumps.

Edit: In the code from touchd that mapped out x/y coordinates, I printed out the value of the two separate numbers that were added and I found that one seems to be the value of a large sensor - its value is in multiple of 256. The other one seems to be a more precise sensor with a limit of roughly 100. So touching either side of an area which was the limit of the large sensor would result in a jump of 156x156 (0+100 vs 256+0)... /me thinks there might be a third sensor that's not being taken accounted for.

Firewing1.

---

### Post by kosumi68 on 2008-06-30
firewing, could you please check that you are running precisely the synaptics settings found here [http://web.comhem.se/rydberg/Bits/xorg-settings.html](http://web.comhem.se/rydberg/Bits/xorg-settings.html) and see if the problem you describe persists? I tried it and it was very smooth.

You can check the bcm5974.c source to see my current observations regarding the device sensors.

---

### Post by firewing1 on 2008-06-30
> **kosumi68 said:**
> firewing, could you please check that you are running precisely the synaptics settings found here [http://web.comhem.se/rydberg/Bits/xorg-settings.html](http://web.comhem.se/rydberg/Bits/xorg-settings.html) and see if the problem you describe persists? I tried it and it was very smooth.

You can check the bcm5974.c source to see my current observations regarding the device sensors.
I redid my Xorg settings and it still happens :(

I'm going to try to get myself a git build of synaptics to see if it helps...
Edit: Hm, how many inputs does your Xorg log show? My logs show 4 "mouse" inputs, maybe this is the cause of the problem?```

(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) XINPUT: Adding extended input device "HID 05ac:820b" (type: MOUSE)

```
firewing1

---

### Post by kosumi68 on 2008-06-30
> 
(II) XINPUT: Adding extended input device "HID 05ac:820b" (type: MOUSE)


Wow, this is the first time is see this one attached to anything... I have noticed that usbhid detects it, but thought of it as some not-used interface.

You could try disabling it altogether, try adding this quirk in /etc/modprobe.d/options (or append to your existing ones):

```

options usbhid quirks=05ac:820b:0x00000004

```

This will ignore the device altogether.

UPDATE: a simpler way might be to comment out all devices but the synaptics driver in the ServerLayout section of xorg.conf. :)

---

### Post by firewing1 on 2008-06-30
> **kosumi68 said:**
> Wow, this is the first time is see this one attached to anything... I have noticed that usbhid detects it, but thought of it as some not-used interface.

You could try disabling it altogether, try adding this quirk in /etc/modprobe.d/options (or append to your existing ones):

```

options usbhid quirks=05ac:820b:0x00000004

```

This will ignore the device altogether.

UPDATE: a simpler way might be to comment out all devices but the synaptics driver in the ServerLayout section of xorg.conf. :)
Thanks, I'll give that a try. I thing this might have something to do with Fedora 9's very recent Xorg version - It uses a 1.5 pre-release which would explain why you've never seen this happen before. I'll post back with the results ^_^

BTW - Since the problem seems to be fedora-specific now, I can create a thread on fedoraforum if you'd like. I posted here because that was the link from the touchd mailing list ;)

---

### Post by firewing1 on 2008-06-30
> **kosumi68 said:**
> Wow, this is the first time is see this one attached to anything... I have noticed that usbhid detects it, but thought of it as some not-used interface.

You could try disabling it altogether, try adding this quirk in /etc/modprobe.d/options (or append to your existing ones):

```

options usbhid quirks=05ac:820b:0x00000004

```

This will ignore the device altogether.

UPDATE: a simpler way might be to comment out all devices but the synaptics driver in the ServerLayout section of xorg.conf. :)
Interesting, it seems synaptics was ignoring the settings in xorg.conf - I used a shell script to read them and parse them using synclient, now the jumpyness is gone. :D Not sure if it was the settings or the extra input.

Either way, heads up for when ubuntu updates to Xorg server v1.5 - Synaptics settings in xorg.conf might break  :(

Thanks for your help.

---

### Post by kosumi68 on 2008-06-30
Firewing, great! That makes it 2 MBAs and 4 Penryns reported so far. Thanks to all of you for reporting details and tips, what a wonderfully parallel testing environment this is! :)

---

### Post by magaio on 2008-06-30
Hey Kosumi,

So I got the touchpad to work exactly as I wanted. One thing though ... now my usb mouse doesn't respond when plugged in. It's sending data to /dev/input/mice but something about the conf isn't recognizing it. Right now I'm just commenting out between "Configured Mouse" and "Synaptics Touchpad" in ServerLayout. Am I missing something?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto-dev"
	Option		"CorePointer"

        # exclusive grabbing of device
        Option		"GrabEventDevice"	"1"

        # simulate right button
        Option		"MultiFingerButton"	"2"

        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"

        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" 

        # set to 0 if you don't want horizontal scrolling
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "40"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers
        # if you like to push hard, change to 30 or 40
        Option          "FingerLow"             "16"
        Option          "FingerHigh"            "23"
        Option          "FingerPress"           "256"

        # palm detect
        Option          "PalmDetect"             "0"
        Option          "PalmMinWidth"           "180"
        Option          "PalmMinZ"               "10"  

        # borders based on output from synclient
        # controls the edge scrolling
        # turned off by specifing the exact size /henrik
        Option          "LeftEdge"              "0"
        Option          "RightEdge"             "1280"
        Option          "TopEdge"               "0"
        Option          "BottomEdge"            "800"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8"
        # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2"
        # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "223"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        #Option          "TapButton2"            "3"
        #Option          "TapButton3"            "2"
        Option          "TapButton2"             "0"
        Option          "TapButton3"             "0"

        # must be commented out or normal tapping wont work
        Option          "TapButton1"             "0"

        # not using corner buttons
        Option          "RTCornerButton"         "0"
        Option          "RBCornerButton"         "0"
        Option          "LTCornerButton"         "0"
        Option          "LBCornerButton"         "0"  

        # needed for disabled while typing fix  
        Option          "SHMConfig"              "true"

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	#InputDevice	"Synaptics Touchpad"
	InputDevice	"Configured Mouse"
EndSection
```

---

### Post by kosumi68 on 2008-06-30
Yeah, I realized this myself earlier today - you need to comment out the CorePointer line of the synaptics configuration, then you should get both the mouse and trackpad events.

PS. The option is there for "historical reasons" - I will comment it out in the file on the webpage. Thanks for pointing it out! DS.

---

### Post by _alex_ on 2008-06-30
> **kosumi68 said:**
> I see... So both the penryn computers displays this reinitialization problem, related to suspend (to ram or disk?) and/or usb connect/disconnect. I tried reproducing this problem on my MBA by plugging and unplugging a usb mouse, but it is stable. Thus, my current conjecture is that this problem only occurs on the penryn computers. Now the question is: where is the source of this problem? It does not seem like anything one can fix in the bcm5974 driver.

Doing the following also kills the mouse for me:
```

sudo rmmod bcm5974
sudo modprobe bcm5974

```
So it does in fact seem to be a reinit problem. Edit: Just to provide some more info, here's what's printed in dmesg:
```

[ 5060.442260] usbcore: deregistering interface driver bcm5974
[ 5060.470987] bcm5974: disconnected
[ 5061.907285] bcm5974: Wellspring mode initialized.
[ 5061.907419] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.2/input/input31
[ 5061.959638] usbcore: registered new interface driver bcm5974

```

---

### Post by kosumi68 on 2008-06-30
Hey alex, running the same commands stops the trackpad for me, but the external usb mouse is still going. I get the same output in my dmesg, and there is nothing written to /var/log/Xorg.0.log.

Is the non-working trackpad after reloading the device what you would consider the problem? I did not even think of it as a problem, not expecting it to reinitiate in the first place... I should think more of ubuntu, shouldn't I :-P

Awaiting your confirmation that this is a problem, I will start digging for a solution. Thanks!

---

### Post by _alex_ on 2008-06-30
I believe that my faulty usb connection, lloeki's suspend---which case the touchpad to stop moving (while the touchpad button still works)---as well as the 2 commands are all the same problem (i.e., dmesg shows essentially the same messages in those cases -- that is, bcm disconnects, then it's registered again but this time the mouse no longer moves -- the external mouse is unaffected as you mention).

I suspect if reloading the device is fixed, all of those issues will go away. Edit: In fact, you can try the following yourself:
```

# run the following command:
sudo rmmod bcm5974
# now the touchpad and touchpad button will not work
# run the following command:
sudo modprobe bcm5974
# now the touchpad button comes back, but the touchpad doesn't move the mouse.
# This is *exactly* what happens when the device briefly disconnects due to my faulty macbook's connection.

```

---

### Post by kosumi68 on 2008-06-30
It seems switching to a text console (ctrl-alt-F1) and back again (alt-F7) is enough to reinitiate the trackpad. At least one other program - pommed with some hacks for testing - continues reading the trackpad events even after bcm5974 is reloaded. Thus, at this stage, it seems like a synaptics "bug".

---

### Post by _alex_ on 2008-07-01
Yeah switching to a text console and back brings back the touchpad. The closest related bug report I could find is this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68370](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68370)

---

### Post by kosumi68 on 2008-07-01
Version 0.42 is out: the very first button click after starting X is now registered properly.

Enjoy!

---

### Post by lloeki on 2008-07-01
for me, last working version is 0.31.

previously I tried 0.41 has the pointer jumping frantically, then stuck. in this case two finger click, and two finger scrolling works perfectly. then I reverted to 0.31 and it was affected too.
I then fiddled a bit and 0.31 is back to life. this involved many shots in the dark.
now 0.41 and 0.42 don't work. pointer just stays there, no clicks or whatever. logs seem fine though. reverting to 0.31 (package reinstall+rmmod/modprobe+kill X) makes things work instantly.

I'll take a deeper, proper look later.

I made a PKGBUILD for ArchLinux, I will share it as soon as I think it's good enough.

Also, I fell like an a** asking that, but could you make separate src packages for the older versions too?

---

### Post by mass_ga on 2008-07-01
> **lloeki said:**
> 0.41 has the pointer jumping frantically, then stuck. in this case two finger click, and two finger scrolling works perfectly.


Hi everybody!! I successfully installed BCM5974 driver, set up xorg.conf following previous suggestions in the thread and the touchpad of my MBA seems to work! Just two more things ... the pointer somethimes jumps or suddenly disappear; then right click doesn't work. Do you suggest to reinstalll 0.31 driver version?

---

### Post by kosumi68 on 2008-07-01
I believe lloekis problem is related to not getting the xorg config to "bite" - we discussed this earlier, and it is consistent with the palm problem (lloeki, please check your palm settings)

The difference between 0.31 and 0.41 is almost only the finger width, which requires the palm setting to be turned off in synaptics, because it is broken. Reverting to 0.31 seems pointless to me - 0.42 is the best version so far on my MBA, why should it be different for you :)

Lloeki, perhaps you can package those yourself - the next version of bcm5974 will use the dkms package system, and then it should be easy to build and maintain lots of version-kernel variants.

mass_ga, the xorg settings are very important in getting the right behavior. The button tapping works provided you use the right version of synaptics, you will find it in earlier posts in this thread.

---

### Post by lloeki on 2008-07-01
> (lloeki, please check your palm settings)
exactly! thanks, I missed that one, pointer now moves correctly.

as for packaging, I was just worried about recent versions not working. now it's fine. thanks.

---

### Post by magaio on 2008-07-01
Do we have middle-click with this module?

---

### Post by kosumi68 on 2008-07-02
Yes, both middle-click with button and with tapping. Or rather, synaptics has that. Please refer to the thread posts for details.

Reading through all the posts, one finds that most issues are either related  to synaptics settings in xorg.conf, or problems with the pathological case where the bcm5974 driver is removed from under the feet of the synaptics driver. Unfortunately, neither of those problems can really be remedied in the bcm5974 driver. Perhaps one should work a little bit on the synaptics driver?

For newcomers, my advice is to copy one of the synaptics settings from [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) into your xorg.conf. If experiencing problems, please provide the diff to the file synclient-output.txt.

EDIT: or run the script bcm5974-diagnostics, it checks the usual suspects.

---

### Post by mass_ga on 2008-07-02
> **kosumi68 said:**
> 
mass_ga, the xorg settings are very important in getting the right behavior. The button tapping works provided you use the right version of synaptics, you will find it in earlier posts in this thread.

Here is my xorg.conf file:


> Section "InputDevice"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto-dev"
#	Option		"CorePointer"
#	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"True"

# exclusive grabbing of device
        Option		"GrabEventDevice"	"1"

        # simulate right button
        Option		"MultiFingerButton"	"2"

        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"

        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" 

        # set to 0 if you don't want horizontal scrolling
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "40"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers
        # if you like to push hard, change to 30 or 40
        Option          "FingerLow"             "16"
        Option          "FingerHigh"            "23"
        Option          "FingerPress"           "256"

        # palm detect
        Option          "PalmDetect"             "0"
        Option          "PalmMinWidth"           "180"
        Option          "PalmMinZ"               "10"  

        # borders based on output from synclient
        # controls the edge scrolling
        # turned off by specifing the exact size /henrik
        Option          "LeftEdge"              "0"
        Option          "RightEdge"             "1280"
        Option          "TopEdge"               "0"
        Option          "BottomEdge"            "800"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8"
        # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2"
        # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "223"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        #Option          "TapButton2"            "3"
        #Option          "TapButton3"            "2"
        Option          "TapButton2"             "0"
        Option          "TapButton3"             "0"

        # must be commented out or normal tapping wont work
        #Option          "TapButton1"             "0"

        # not using corner buttons
        Option          "RTCornerButton"         "0"
        Option          "RBCornerButton"         "0"
        Option          "LTCornerButton"         "0"
        Option          "LBCornerButton"         "0"  

EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


I can't find out anything wrong. Right click continues not working.

---

### Post by kosumi68 on 2008-07-02
I cant see any problem either, looks normal. Could you try out this command, please:

```

 synclient -l | diff - synclient-output.txt

```

You find the synclient-output.txt on the webpage. This way, we get to see precisely what synaptics thinks about its settings, not only what we instruct it to think :)

---

### Post by firewing1 on 2008-07-02
I just updated synaptics to today's git and everything is working perfectly (double-finger scroll detection has improved a lot!) except the middle button - Using the synaptics configuration from the webpage, tapping middle click works but not with the button.
firewing1

---

### Post by kosumi68 on 2008-07-02
The MultiFingerButton is a mactel patch, apparently it has not made it to the git source... :(

However, the mactel patch to the actual code seems fairly small... perhaps one can apply it to the git version :)

---

### Post by firewing1 on 2008-07-02
> **kosumi68 said:**
> The MultiFingerButton is a mactel patch, apparently it has not made it to the git source... :(

However, the mactel patch to the actual code seems fairly small... perhaps one can apply it to the git version :)
Ah, OK - Recompiled and it works now. Thanks again!
Firewing1

---

### Post by matty_x on 2008-07-03
Here's another Penryn user! Thanks for the driver!

---

### Post by letic on 2008-07-03
+1 Penryn :)

Cheers for that Henryk it's working perfectly now.

---

### Post by firewing1 on 2008-07-04
Any ideas on when this will be upstream?
firewing1

---

### Post by kosumi68 on 2008-07-04
For me, it is hard to say. The review process is ongoing, I am working on a new release, and packaging takes a bit of time. A guess would be that it first appears as a dkms package on my website, then as a backport in hardy, and then in the 2.6.27 kernel.

---

### Post by Botto on 2008-07-05
I get a problem with loading the bcm5974 module.
This is a printout from my terminal:
```

FATAL: Error inserting bcm5974 (/lib/modules/2.6.24-19-generic/kernel/drivers/input/mouse/bcm5974.ko): Invalid module format

```

---

### Post by kosumi68 on 2008-07-05
Could you please provide some more information about your system:

```

uname -r

```

What version of bcm5974 are you running? What is the output of of this command:

```

lsusb

```

---

### Post by Rekoil on 2008-07-05
Just another grateful MacBook Pro 4,1 user popping in to say thanks :)

+1 virtual beer for kosumi68

---

### Post by kosumi68 on 2008-07-06
Current status of the bcm5974 driver:

* 2 confirmed users on Macbook Air (productId: 0x0223)

* 9 confirmed users on Macbook Pro Penryn (productIds: 0x0230, 0x0231)

* Version 0.42 is the latest stable version.

Download page: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/)

---

### Post by kosumi68 on 2008-07-06
Version 0.5 is out!

The bcm5974 is now packaged using the dkms utility (available in package manager). Installing should be completely automatic.

The bcm5974-0.5 now works well with synaptics' palm detection.

I would love some feedback on this release, in particular in these areas:

* Installation - does it work well for everyone?

* Stability - can you make it fail in anyway? If you can, please report back to this thread :)

* Tuning - the Penryn touchpad has slightly different dimensions from the MBA. In order to set the right parameters in the driver, if someone could please turn on the debugging in /etc/modprobe.d/bcm5974, then use the output of /var/log/debug to find out the actual sensor limits, it would be most helpful.

Enjoy!

---

### Post by kosumi68 on 2008-07-07
Version 0.51 just released, with really smooth mouse motion (there was a slight regression in 0.5).

---

### Post by RonakG on 2008-07-07
Hi,

I am a very newbi to Ubuntu/Linux. I just installed the deb package provided on the link. V0.51. Then I modified the xorg.conf file.

I logged out and logged in again. But nothing seems to work. Is there anything I am missing here?

Pls help.

---

### Post by kosumi68 on 2008-07-07
Hello RonakG, I will need some more information in order to disentangle the problem.

1. Did the installer complain?

2. Is your mouse pointer not moving?

3. Please run the script /usr/src/bcm5974-0.51/scripts/bcm5974-diagnostics, and post the output here.

---

### Post by Botto on 2008-07-07
The fatal load issue has gone now, but I have the same problem as RonakG. The mouse pointer moves, but when I look in the Xorg log it says it cant find a synaptic device.

Here is the output from the diagnostic:
```
-----------------------------------------------------------------------
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-1ubuntu4
* USB device: Bus 005 Device 003: ID 05ac:0231 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
No help on this one...

```

---

### Post by kosumi68 on 2008-07-07
Thanks for reporting! Of course the diagnostics failed at the single point where I dont know how to proceed... :) The output of this command would be helpful:

```

cat /proc/bus/input/devices

```

Also, please try this command, and then rerun the diagnostics tool:

```

sudo rmmod bcm5974; sudo modprobe bcm5974

```

Note: your trackpad will freeze after issuing the above command. To reinitialize, do "Ctrl-Alt-F1" to go to a text window, then "Alt-F7" to go back to the X session.

---

### Post by Botto on 2008-07-07
> **kosumi68 said:**
> Thanks for reporting! Of course the diagnostics failed at the single point where I dont know how to proceed... :) The output of this command would be helpful:

```

cat /proc/bus/input/devices

```

Also, please try this command, and then rerun the diagnostics tool:

```

sudo rmmod bcm5974; sudo modprobe bcm5974

```

Note: your trackpad will freeze after issuing the above command. To reinitialize, do "Ctrl-Alt-F1" to go to a text window, then "Alt-F7" to go back to the X session.


The output from "cat /proc/bus/input/devices" is:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=05ac Product=820a Version=0111
N: Name="HID 05ac:820a"
P: Phys=usb-0000:00:1a.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05ac Product=820b Version=0111
N: Name="HID 05ac:820b"
P: Phys=usb-0000:00:1a.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=3
B: MSC=10

I: Bus=0003 Vendor=05ac Product=0231 Version=0111
N: Name="Apple, Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=120013
B: KEY=e10000 0 0 0 1007b00010007 ff9f217ac54057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05ac Product=0231 Version=0111
N: Name="Apple, Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.2/input/input11
U: Uniq=
H: Handlers=mouse3 event11 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=3
B: MSC=10

```

I didnt include the power button, lid switch ect...

After unloading the module and reloading it, the trackpad still worked fine, but the output from the diagnostic is:
```
-----------------------------------------------------------------------
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-1ubuntu4
* USB device: Bus 005 Device 003: ID 05ac:0231 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
No help on this one...

```

---

### Post by kosumi68 on 2008-07-07
> 
N: Name="Macintosh mouse button emulation"


Are you by any chance running mouseemu? In case you do, please stop it/remove it. :)

UPDATE: I was comparing the device output to a customized kernel without the kernel-built-in mouse emulation option. When checking against the 2.6.24-19-generic kernel, I also see the above line. My bad.

---

### Post by Botto on 2008-07-07
The only thing I can think of is that my computers has a Norwegian layout on the keyboard.

---

### Post by kosumi68 on 2008-07-07
Heja Norge :)

What is the output of dmesg, please?

```

dmesg | grep bcm5974

```

---

### Post by Botto on 2008-07-07
```
[   34.491258] usbcore: registered new interface driver bcm5974
[  231.109730] usbcore: deregistering interface driver bcm5974
[  232.195319] usbcore: registered new interface driver bcm5974

```

---

### Post by kosumi68 on 2008-07-07
Lovely. It means the bcm5974 device was NOT initialized as it should. The currently most likely cause is that usbhid claimed the device before the bcm5974 driver, although the quirks in /etc/modprobe.d/bcm5974 are there to prevent it. Possibly something is wrong with the quirks. Could you please provide this info:

```

lsusb | grep 05ac
cat /etc/modprobe.d/bcm5974

```

---

### Post by Botto on 2008-07-07
> **kosumi68 said:**
> Lovely. It means the bcm5974 device was NOT initialized as it should. The currently most likely cause is that usbhid claimed the device before the bcm5974 driver, although the quirks in /etc/modprobe.d/bcm5974 are there to prevent it. Possibly something is wrong with the quirks. Could you please provide this info:

```

lsusb | grep 05ac
cat /etc/modprobe.d/bcm5974

```

YES! The quirks in the /etc/modprobe.d/bcm5974 had the penryn model commented out.
I commented the air model and removed the comment for the penryn model.
It now works and I can use the synaptics client, excellent.
Thank you very much for all the help

---

### Post by kosumi68 on 2008-07-07
Great! This means there is a problem with the post-installation script in the dkms package. I will check it at once, and get back with a new debian package.

Cheers!

---

### Post by Botto on 2008-07-07
> **kosumi68 said:**
> Great! This means there is a problem with the post-installation script in the dkms package. I will check it at once, and get back with a new debian package.

Cheers!

Perhaps ask the user if he has a macbook pro or macbook air.

---

### Post by kosumi68 on 2008-07-07
Botto,

the post-install script is detecting the type of computer automatically, and uncomments the correct line accordingly. There was a typo in the post-install script, which prevented this from happening.

There is a new release (0.52) available at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/). It would be greatly appreciated if you could install this one and verify that it works (you can move/remove the file /etc/modprobe.d/bcm5974 first to feel extra confident).

---

### Post by eindgebruiker on 2008-07-07
Hi Henrik,

I just installed 0.52 on a MacBook Pro Penryn. I still encountered the same problem Botto had: penryn was commented out instead of macbook air.

Besides that: excellent work!

---

### Post by kosumi68 on 2008-07-07
Great! Yes, there was yet another typo in the post-install script... a new version will be out shortly.

A few pages back I expressed a hope that someone with a penryn could possibly perform a little experiment to determine the correct dimensions of the penryn trackpad. Are you up for it? :)

---

### Post by kosumi68 on 2008-07-07
Ok, bcm5974-0.53 is out! Any test on the MBP is greatly appreciated. :)

---

### Post by eindgebruiker on 2008-07-07
> **kosumi68 said:**
> A few pages back I expressed a hope that someone with a penryn could possibly perform a little experiment to determine the correct dimensions of the penryn trackpad. Are you up for it? :)

Sure. Tell me what to do.

---

### Post by eindgebruiker on 2008-07-07
> **firewing1]
For the swiping, a triple finger "swipe" (really just a left/right movement) moves back/forward in Firefox or the file browser. Apple also has a rotate gesture for pictures which is pretty neat.[/QUOTE]

[QUOTE=kosumi68 said:**
> Ok - then you only need to enable horizontal scroll in xorg.conf and in your trackpad configuration (System/Preferences/Touchpad) :)

Triple finger swipe equates to the back/forward button in Safari. Which is awesome. Any chance getting that to work (in Firefox)?

---

### Post by gu3st on 2008-07-07
Hi :)

I have a problem with this kernel driver.  I've just installed the kernel module, and I have 2 finger scrolling and such (so I imagine that it's working) however 2 finger clicking does not work.  Contents of my xorg.conf here:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        #Option         "CorePointer"

        # exclusive grabbing of device
        Option          "GrabEventDevice"       "1"

        # simulate right button
        Option          "MultiFingerButton"     "2"

        # not using edge scrolling
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"

        # use two finger scrolling
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1" 

        # set to 0 if you don't want horizontal scrolling
        # scroll speed, lower is faster
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "40"

        # minimum pressure motion factor
        Option          "PressureMotionMinZ"    "10"

        # touch and untouch thresholds, higher numbers
        # if you like to push hard, change to 30 or 40
        Option          "FingerLow"             "16"
        Option          "FingerHigh"            "80"
        Option          "FingerPress"           "256"

        # palm detect
        Option          "PalmDetect"             "0"
        Option          "PalmMinWidth"           "10"
        Option          "PalmMinZ"               "200"  

        # borders based on output from synclient
        # controls the edge scrolling
        # turned off by specifing the exact size /henrik
        Option          "LeftEdge"              "0"
        Option          "RightEdge"             "1280"
        Option          "TopEdge"               "0"
        Option          "BottomEdge"            "800"

        # speeds, smaller number for a slower mouse
        Option          "MinSpeed"              "0.8"
        # 0.5 is very slow, 1.5 is very fast
        Option          "MaxSpeed"              "1.2"
        # up to 1.5 works ok
        Option          "AccelFactor"           "0.10"

        # tap times, change to suit your tapping habits
        Option          "MaxTapMove"            "100"
        Option          "MaxTapTime"            "223"
        Option          "MaxDoubleTapTime"      "200"
        
        # don't change these or two finger tap stops working
        #Option          "TapButton2"            "3"
        #Option          "TapButton3"            "2"
        Option          "TapButton2"             "0"
        Option          "TapButton3"             "0"

        # must be commented out or normal tapping wont work
        Option          "TapButton1"             "0"

        # not using corner buttons
        Option          "RTCornerButton"         "0"
        Option          "RBCornerButton"         "0"
        Option          "LTCornerButton"         "0"
        Option          "LBCornerButton"         "0"  

        # needed for disabled while typing fix  
        Option          "SHMConfig"              "true"

EndSection


```

Help with this will be greatly appreciated :)

Thank you very much for this lovely kernel driver.  Makes my triple boot of OSX/XP/Kubuntu work nicely :)

Dustin

---

### Post by kosumi68 on 2008-07-08
Thank you eindgebruiker, here is the thing:

* Tuning - the Penryn touchpad has slightly different dimensions from the MBA. Please turn on debugging in /etc/modprobe.d/bcm5974 by uncommenting the appropriate line, then restart the driver:

```

sudo rmmod bcm5974; sudo modprobe bcm5974

```

Note: your trackpad will freeze after issuing the above command. To reinitialize, do "Ctrl-Alt-F1" to go to a text window, then "Alt-F7" to go back to the X session.

Now start the following command in a terminal:

```

tail -f /var/log/debug

```

You will see lines showing the current pressure (p), finger width (w), absolute x position (x), absolute y position (y), and number of fingers (n). Now move a finger along the left edge of the trackpad and record the minimal value of x. Repeat along all four edges, and report these values: minimum_x, minimum_y, maximum_x, maximum_y.

Dont forget to comment out the debug line again, and restart the driver, or your disk will eventually fill up with debug output :)

Cheers!

---

### Post by kosumi68 on 2008-07-08
> **eindgebruiker said:**
> Triple finger swipe equates to the back/forward button in Safari. Which is awesome. Any chance getting that to work (in Firefox)?

In System->Preferences->Touchpad, one can turn horizontal scroll on, and two- and three-finger scrolling will act as swiping in firefox. Personally I find horizontal scrolling with two fingers annoying, often getting accidental page-flipping when scrolling up or down on a page, so if one could turn off this feature for two fingers, that would be perfect. The problem seems to be that synaptics does not distinguish between two-finger horizontal scroll and three-finger swipe. A small patch in synaptics, possibly?

---

### Post by kosumi68 on 2008-07-08
gu3st,

in order to get two-finger click working, you need the mactel version of synaptics. I believe you will find information in earlier posts in this thread. Have you tried running the command:

```

/usr/src/bcm5974-0.53/scripts/bcm5974-diagnostics

```

It should tell two things: a) what version of synaptics you have installed, and b) your synaptics settings as a diff to a set of sensible defaults.

---

### Post by eindgebruiker on 2008-07-08
OK, this is the Penryn:

x: +4825
x: -4825
y: +4290
y: -0171

---

### Post by Botto on 2008-07-08
I can confirm these values.
I took 10 samples and calculated the mean value:


x: +4820
x: -4781
y: +4245
y: -0141


Looking at the debug output, I can see that it can feel 4 fingers. Can we use this in xorg config?

---

### Post by letic on 2008-07-08
Hey Henrik,

I'm experiencing some random issues with a MBP, when booting/rebooting the driver is working alternatively.

I guess this is due to usbhid loading before bcm5974. When checking the logs I can see the usbhid loading first most of the time.

I checked the quirks but they are correct. I put some info below, let me know what you would need to debug.

```
cat /etc/modprobe.d/bcm5974 
### Options for the bcm5974 driver

## quirks for the Macbook Air
#options usbhid quirks=0x05ac:0x0223:0x00020800,0x05ac:0x0224:0x00024800,0x05ac:0x0225:0x00020800

## quirks for the Macbook Pro Penryn
options usbhid quirks=0x05ac:0x0230:0x00020800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00020800

## Debug level - uncomment this to get raw packets in /var/log/debug
#options bcm5974 debug=99

```

```

lsusb | grep 05ac
Bus 007 Device 003: ID 05ac:0230 Apple Computer, Inc. 
Bus 007 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 003 Device 005: ID 05ac:820b Apple Computer, Inc. 
Bus 003 Device 004: ID 05ac:820a Apple Computer, Inc. 
Bus 003 Device 003: ID 05ac:820f Apple Computer, Inc. 
Bus 002 Device 002: ID 05ac:8502 Apple Computer, Inc.

```

Cheers
LeTic

---

### Post by kosumi68 on 2008-07-08
eindgebruiker, Botto, much obliged!

Apparently the penryn trackpad is slightly shorter than the MBA. The values have been saved and will appear in the next release.

---

### Post by Botto on 2008-07-08
One bug I have found is when forcfully shutting down and booting up again, the trackpad doesnt have any of the advanced features, just moving the mouse, no tapping or anything.

---

### Post by kosumi68 on 2008-07-08
Greetings Letic,

> **letic said:**
> 
I'm experiencing some random issues with a MBP, when booting/rebooting the driver is working alternatively.
[..]
I checked the quirks but they are correct. I put some info below, let me know what you would need to debug.


Have you tried out the bcm5974-diagnostics at a point where you are experiencing problem? It could reveal something.

Otherwise, the thing that comes to mind is to check that no other files contains quirks in /etc/modprobe.d/. Also if your are running mouseemu, that could be a problem. A printout of dmesg when the problem appears is also helpful.

---

### Post by kosumi68 on 2008-07-08
> **Botto said:**
> One bug I have found is when forcfully shutting down and booting up again, the trackpad doesnt have any of the advanced features, just moving the mouse, no tapping or anything.

This sounds profoundly odd. Could you please provide the output of dmesg when this happens? Maybe it is related to letics problem, maybe the quirk settings are ignored for some reason.

---

### Post by kimtiede on 2008-07-08
Heres one more Macbook Pro Penryn working.

I installed the 0.53 deb package and the quirks in /etc/modprobe.d/bcm5974 had the penryn commented out, so I had to change that. Afterwards it worked :-)

Cheers and thanks a lot for the work!!

Kim

Macbook Pro Penryn
Ubuntu 8.04
Danish keyboard

---

### Post by cyberdork33 on 2008-07-08
kosumi,

This will likely not be available in the Ubuntu kernel anytime soon. Would you like to put it in the mactel-support PPA? This should make it much easier for users to get the driver and update it.

[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)

Request to join, and I will gladly approve.

---

### Post by _alex_ on 2008-07-08
Hi Henrik,

I just got my MacbookPro back from the repair shop. As expected everything works perfectly now. I'm using the latest (v0.53) driver. I too had the penryn line commented out in /etc/modprobe.d/bcm5974.
An easier way would be to just use one quirks line for both Air and Penryn as follows:
```

options usbhid quirks=0x05ac:0x0223:0x00020800,0x05ac:0x0224:0x00024800,0x05ac:0x0225:0x00020800,0x05ac:0x0230:0x00020800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00020800

```

Since there is no clash for the device ids, the hid module will use the corresponding quirk for the given hardware. That way you won't have to do any sort of hardware detection during installation.

---

### Post by kosumi68 on 2008-07-08
Hi kimtiede,

I am glad it worked out, but it troubles me that your setup was not automatically detected. It would be most helpful if you could provide the output of these commands:

```

which lsusb
lsusb

```

It would make it possible for me to test the installation further. Cheers!

---

### Post by kosumi68 on 2008-07-08
Hi Cyberdork,

thanks - it will indeed be a lot easier!

:)

---

### Post by kosumi68 on 2008-07-08
Welcome back alex,

> **_alex_ said:**
> Hi Henrik,
An easier way would be to just use one quirks line for both Air and Penryn [..]
Since there is no clash for the device ids, the hid module will use the corresponding quirk for the given hardware. That way you won't have to do any sort of hardware detection during installation.

*blushes* Here is one that thought there was a limit of four set in the kernel... I guess it applies to a single id, not the total?

---

### Post by sbayless on 2008-07-08
First, I want to echo everyone else here in saying: thank you.

I just tried to install version 0.53 from the .deb on my MBP, on Ubuntu 8.04 (fully updated, kernel 2.6.24-19-generic). Installation appeared to fail on the post install script. Unfortunately, the trackpad works exactly as it did before installing the driver.

The installer runs fine until the post installer script where it complains that it cant find kernel -17, or -18, and then appears to give up without trying -19.

I've been looking over the forum, and I've tried to provide for you the information you've asked for in the past for debugging purposes. If there is any other information I can provide for you, or testing I can do, I'm more than happy to help.

First off, ```
/etc/modprobe/d/bcm5974
``` quirks had the penryn commented out, instead of the Macbook Air (assumedly because the post install scrip failed). However, changing the comments and reloading the driver using```
sudo rmmod bcm5974; sudo modprobe bcm5974
``` a) did not freeze my trackpad and b) did not solve the problem.

Here is the output from diagnostics:
```
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-1ubuntu4
* USB device: Bus 007 Device 003: ID 05ac:0230 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974

```

This is (some) of the output from cat /proc/bus/input/devices
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=0458 Product=0007 Version=0110
N: Name="Genius Optical Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input1
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=05ac Product=0230 Version=0111
N: Name="Apple, Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120013
B: KEY=e10000 0 0 0 0 0 0 1007b 10007 ff9f217a c54057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05ac Product=0230 Version=0111
N: Name="Apple, Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.2-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input3
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
B: MSC=10

I: Bus=0003 Vendor=05ac Product=820a Version=0111
N: Name="HID 05ac:820a"
P: Phys=usb-0000:00:1a.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05ac Product=820b Version=0111
N: Name="HID 05ac:820b"
P: Phys=usb-0000:00:1a.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5
U: Uniq=
H: Handlers=mouse3 event5 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
B: MSC=10

```

---

### Post by _alex_ on 2008-07-08
> **kosumi68 said:**
> *blushes* Here is one that thought there was a limit of four set in the kernel... I guess it applies to a single id, not the total?

Actually I did not realize that MAX_USBHID_BOOT_QUIRKS was set to 4. I think you're right the maximum is four quirks. Bummer, I guess I can't think of an easier way than what you're already doing.

Detection of the hardware failed on my macbook pro running hardy 64bit. Here's the output of "which lsusb":
```
/usr/sbin/lsusb
```
and "lsusb":
```

Bus 007 Device 003: ID 05ac:0230 Apple Computer, Inc. 
Bus 007 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 05ac:0304 Apple Computer, Inc. Apple Optical USB Mouse [Mitsumi]
Bus 003 Device 005: ID 05ac:820b Apple Computer, Inc. 
Bus 003 Device 004: ID 05ac:820a Apple Computer, Inc. 
Bus 003 Device 003: ID 05ac:820f Apple Computer, Inc. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05ac:8502 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by kosumi68 on 2008-07-08
Good news: the post-install script was so full of bugs i must have been asleep when writing it.

bcm5974-0.54 released:

* Penryn trackpad dimensions fine-tuned

* x86_64 for 2.6.24-19-generic

* post-install fixed

Enjoy!

---

### Post by kosumi68 on 2008-07-08
sbayless, thanks for the extensive report!

Yes, the post-install problem is consistent, should work in 0.54.

Did you reboot your machine after installing? At least it is consistent with the problem.

---

### Post by sbayless on 2008-07-08
> Did you reboot your machine after installing?

Yes, I did reboot the machine after installing.

---

### Post by _alex_ on 2008-07-08
I can confirm that 0.54 fixes the hardware misdetection issue :D

---

### Post by kosumi68 on 2008-07-08
> **_alex_ said:**
> I can confirm that 0.54 fixes the hardware misdetection issue :D

I am relieved! :)

---

### Post by kosumi68 on 2008-07-08
sbayless, could you try the following:

```

sudo rmmod bcm5974;sudo rmmod usbhid;sudo modprobe bcm5974;sudo modprobe usbhid

```

and provide the output of dmesg?

---

### Post by sbayless on 2008-07-08
> sbayless, could you try the following:

Actually, I just installed 0.54, and everything seems to be working!

---

### Post by kosumi68 on 2008-07-08
That is very good news! Thanks to all of you for helping out, the ubuntu community rocks :cool:

---

### Post by kosumi68 on 2008-07-08
Current standings:

* 2 confirmed users on Macbook Air.

* 14 confirmed users on Macbook Pro Penryn.

The bcm5974-0.54 release is potentially stable.

Download: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/), although this might soon move to mactel, meaning downloading via the package manager.

Anything else? :)

---

### Post by Botto on 2008-07-08
I just tried killing my MBP and the issue with the driver not working after seems to have gone....quite odd considering there havent been that many changes since 0.5

---

### Post by kimtiede on 2008-07-09
> **kosumi68 said:**
> Hi kimtiede,

I am glad it worked out, but it troubles me that your setup was not automatically detected. It would be most helpful if you could provide the output of these commands:

```

which lsusb
lsusb

```

It would make it possible for me to test the installation further. Cheers!

Hi,

```

kim@kim-ubuntu:~$ which lsusb
/usr/sbin/lsusb
kim@kim-ubuntu:~$ lsusb
Bus 007 Device 002: ID 05ac:8502 Apple Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 05ac:820b Apple Computer, Inc. 
Bus 001 Device 005: ID 05ac:820a Apple Computer, Inc. 
Bus 001 Device 004: ID 05ac:820f Apple Computer, Inc. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 05ac:0231 Apple Computer, Inc. 
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

I do not know if you still need it as it seems by reading the replies that you have fixed the problem.

If I want to install the new version of the package do I just run the package installer or should I somehow uninstall the old one?

Thanks

Cheers

Kim

---

### Post by kosumi68 on 2008-07-09
> **Botto said:**
> I just tried killing my MBP and the issue with the driver not working after seems to have gone....quite odd considering there havent been that many changes since 0.5

The dkms might be doing some magic at bootup. The bcm5974 package does not use it, but dkms can for instance be configured to automatically rebuild modules for new kernels. If something went wrong during the installation... it is a thought.

---

### Post by kosumi68 on 2008-07-09
Thanks kimtiede, I added it to my productId collection.

> **kimtiede said:**
> 
If I want to install the new version of the package do I just run the package installer or should I somehow uninstall the old one?


By all means go ahead and install it; it will simply be considered an upgrade. No need to perform any extra steps.

Cheers

---

### Post by phico on 2008-07-09
Hello,

Thank you for your great work.
It works nearly perfect on MBP 4.

I installed driver on a MBP 4 from source code because deb packet install was failing (maybe because I modified my kernel for 4Gb support?)

The only thing I am missing is the right click.  Two fingers click does not work.  Tap is ok.  Two finger scroll is ok also.

Here is my diagnostic :
```
-----------------------------------------------------------------------
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-1ubuntu4
* USB device: Bus 006 Device 003: ID 05ac:0231 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/kernel/drivers/input/mouse/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
* bcm5974: Wellspring was initialized
* synaptics: configuration readable
=======================================================================
The bcm5974 seems properly configured

Your synaptics settings differ from the bcm5974 default:
-----------------------------------------------------------------------
     EmulateTwoFingerMinZ    = 257
     FastTaps                = 0
     FingerHigh              = 80
-    FingerLow               = 16
+    FingerLow               = 30
     FingerPress             = 256
     GrabEventDevice         = 1
     GuestMouseOff           = 0
@@ -35,8 +35,7 @@
     MaxTapMove              = 100
     MaxTapTime              = 223
     MinSpeed                = 0.8
-    MultiFingerButton       = 2
-    PalmDetect              = 0
+    PalmDetect              = 1
     PalmMinWidth            = 10
     PalmMinZ                = 200
     PressureMotionMaxFactor = 1
@@ -48,14 +47,14 @@
     RTCornerButton          = 0
     ScrollButtonRepeat      = 100
     SingleTapTimeout        = 180
-    TapButton1              = 0
-    TapButton2              = 0
-    TapButton3              = 0
+    TapButton1              = 1
+    TapButton2              = 3
+    TapButton3              = 2
     TopEdge                 = 0
     TouchpadOff             = 0
     TrackstickSpeed         = 40
     UpDownScrolling         = 1
     UpDownScrollRepeat      = 1
-    VertEdgeScroll          = 0
+    VertEdgeScroll          = 1
     VertScrollDelta         = 40
     VertTwoFingerScroll     = 1
-----------------------------------------------------------------------
If in doubt, please check your /etc/X11/xorg.conf settings


```

---

### Post by kosumi68 on 2008-07-09
Hello phico, from your excellent log it actually shows that the MultiFingerButton option is missing, which can also be explained from the log by the fact that you are running the ubuntu version of synaptics - not the mactel version. :)

Try adding the mactel repositories to /etc/apt/sources.list:

```

deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

```

Now you should be able to find the mactel version of synaptics in the package manager.

Cheers!

---

### Post by cyberdork33 on 2008-07-09
> **kosumi68 said:**
> Now you should be able to find the mactel version of synaptics in the package manager.The thread for that driver is here:
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---

### Post by _alex_ on 2008-07-09
> **kosumi68 said:**
> 
Try adding the mactel repositories to /etc/apt/sources.list:


Henrik, since this issue has been brought up several times now in this thread, you might want to add it to [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) in order to avoid any more questions regarding this.

---

### Post by phico on 2008-07-09
Thanks a lot kosumi68 and cyberdock33  That was missing indeed.

two fingers + click = right click
three finger + click = middle click

Great great work ...  =D>

A little summary of what I did on MBP 4 :

```
wget http://web.comhem.se/rydberg/Bits/bcm5974-0.54-src.zip
unzip bcm5974-0.54-src.zip 
cd bcm5974/
make -C /lib/modules/`uname -r`/build M=$PWD modules
sudo cp bcm5974.ko /lib/modules/`uname -r`/kernel/drivers/input/mouse/
sudo ./scripts/bcm5974-post-install
sudo modprobe bcm5974
```

add these lines to source repositories /etc/apt/sources.list

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

install or upgrade xserver-xorg-input-synaptics:
```
apt-get install xserver-xorg-input-synaptics
```

restart Xserver

---

### Post by kosumi68 on 2008-07-09
I note +1 penryn user :)

Alex, good idea - I will go over the information again when switching to the mactel PPA.

---

### Post by cyberdork33 on 2008-07-09
> **kosumi68 said:**
> Alex, good idea - I will go over the information again when switching to the mactel PPA.
I know that you linked to this thread, but you also might add directions in the penryn / Macbook Air wiki pages as well.

---

### Post by The_Doctor on 2008-07-09
+1 Penryn User.

Thanks very much for putting time into this... the frequency of your updates is impressive.


One note, though: sometimes the driver failed to work (diagnostics indicated it hadn't been registered in /proc/input/....). After a couple of reboots, it would start working again, which makes me suspect it might be a timing issue, but I can't be sure. I just installed the latest version (.54) and it did load. I'll let you know if it stops working.

Again, thanks!

---

### Post by kosumi68 on 2008-07-09
Speaking of which: bcm5974-0.55 is out. :)

This version contains only minor changes to the packaging, and a long-standing two-line revert for the kernel code. I do not expect any updates in the near future.

The recommendation is now to always reboot after an install (I was mistaken about some things regarding the dkms package).

---

### Post by kimtiede on 2008-07-10
Hi again,

There seems to be an issue around timing as someone previously wrote. Sometimes when I boot the machine the touchpad does not work (the basic stuff works but the 2 finger scroll etc does not).

I then have to issue the command:

```

sudo rmmod bcm5974;sudo rmmod usbhid;sudo modprobe bcm5974;sudo modprobe usbhid

```

Then the mouse stops working at all and I restart X. Then after new login it works again with scroll etc.

It seems to me that the order of which bcm5974 and usbhid are loaded is not consistent.

Cheers

Kim

---

### Post by kosumi68 on 2008-07-10
The fact that the mouse works initially, in both cases, suggests it is the quirks that sometimes get ignored. Otherwise the trackpad would not work at all, since the quirks tell usbhid to ignore it.

The output of this command should be useful:

```

modprobe -c | grep usbhid

```

Otherwise, here are some long-shots to try:

1. Turn off (use sysv-rc-conf or the like, or simply move it somewhere else) the file /etc/init.d/dkms_autoinstaller. This should not do anything in the given configuration, but just to be sure.

2. Check for any other reference to usbhid, using "grep usbhid /etc/modprobe.d/*"

3. Is there a /etc/modules.conf? There shouldnt be...

---

### Post by _alex_ on 2008-07-10
> **kosumi68 said:**
> The fact that the mouse works initially, in both cases, suggests it is the quirks that sometimes get ignored. Otherwise the trackpad would not work at all, since the quirks tell usbhid to ignore it.

I can confirm that this is in fact the case, as the exact same behaviour was observed for the dynamic function key quirk, until the hid_blacklist table was patched. Henrik, when you submit your module to kernel.org, also submit a patch for hid-quirks.c with the HID_QUIRK_IGNORE_MOUSE flag set.

This will solve the issue that is experienced with dynamic quirks once the patch and driver are in the kernel.

---

### Post by kosumi68 on 2008-07-10
Great, that explains it. Although making sure the quirks make their way into the kernel (also the fn-key quirks are missing, are those reported?) removes the symptom, I suspect there should also be a report regarding the unreliable dynamic quirks. Anyone know if this has been reported?

Speaking of patches, here is one to the following nuisance:

When the multi-finger tapping is on, and when two-finger scrolling quickly in a window, the right-click menu often appears. Apparently the two-finger scroll and two-finger tap gets entangled. Here is a small patch to the mactel version of synaptics that seems to take care of the problem:

```

--- synaptics.c 2008-07-11 01:39:34.000000000 +0200
+++ synaptics-new.c     2008-07-11 01:39:54.000000000 +0200
@@ -1138,8 +1138,7 @@ HandleTapProcessing(SynapticsPrivate *pr
 
     touch = finger && !priv->finger_state;
     release = !finger && priv->finger_state;
-    move = ((priv->tap_max_fingers <= 1) &&
-           ((abs(hw->x - priv->touch_on.x) >= para->tap_move) ||
+    move = (((abs(hw->x - priv->touch_on.x) >= para->tap_move) ||
             (abs(hw->y - priv->touch_on.y) >= para->tap_move)));
 
     if (touch) {

```

---

### Post by _alex_ on 2008-07-10
> **kosumi68 said:**
> the fn-key quirks are missing, are those reported?

They are reported and patched in the latest kernel (make sure you have the latest source). However the HID_QUIRK_IGNORE_MOUSE flag was not not set because, unless bcm5974 driver is already in the kernel, the touchpad would stop working.

---

### Post by kosumi68 on 2008-07-10
Yes, they are there in the hardy kernel, but not upstream. I guess there is a process that makes them appear there too, eventually.

---

### Post by _alex_ on 2008-07-10
> **kosumi68 said:**
> Yes, they are there in the hardy kernel, but not upstream. I guess there is a process that makes them appear there too, eventually.

I've submitted a patch upstream but wasn't the first to do so, so I let it slide; not sure what the status is as I've not followed development upstream too closely. In any case, your patch should take precedence when the driver gets accepted upstream.

---

### Post by cyberdork33 on 2008-07-11
> **kosumi68 said:**
> When the multi-finger tapping is on, and when two-finger scrolling quickly in a window, the right-click menu often appears. Apparently the two-finger scroll and two-finger tap gets entangled. Here is a small patch to the mactel version of synaptics that seems to take care of the problem...
I assigned your bug to the maintainer of the synaptics module in the PPA. Hopefully he will update it.

---

### Post by kosumi68 on 2008-07-11
Thank you, cyberdork. Andrew Morton signed off the driver to the mm tree today, so things are moving forward. :)

Cheers!

---

### Post by lucianosilva on 2008-07-12
Hi all,

My touchpad stops working sometimes and I need to restart my X session or to suspend/resume to get it back. I've found this in /var/log/syslog:   

 Jul 12 11:59:30 macbookpro kernel: [ 1075.195829] hub 5-0:1.0: port 2
 disabled by hub (EMI?), re-enabling...
 Jul 12 11:59:30 macbookpro kernel: [ 1075.195845] usb 5-2: USB 
 disconnect, address 22
 Jul 12 11:59:30 macbookpro kernel: [ 1075.197057] /var/lib/dkms/bcm5974
 /0.55/build/bcm5974.c: bcm5974: button urb failed: -19

Is there a way to solve this issue? I think it is related to the usb disconnection.

---

### Post by kosumi68 on 2008-07-13
The error message is ENODEV, no such device, which is consistent with the device being disabled as your log states. Have you considered the possibility that this is a hardware problem? You will find information in alex's posts in this thread.

---

### Post by frisi on 2008-07-13
+1 penryn user

i had some problems getting my touchpad working. this might help somebody else too:
when running the diagnostics (/usr/src/bcm5974-0.55/scripts/bcm5974-diagnostics)

i got the same problem as sbayless described in his comment on [page 13]("http://ubuntuforums.org/showthread.php?t=840040&page=13")

```
* /proc/bus/input/devices: module is NOT registered
Please double-check the quirks settings in /etc/modprobe.d/bcm5974
```

i could fix this by running the installer again *after* commenting out the 
quirks for the function key in /etc/modprobe.d/option

---

### Post by kosumi68 on 2008-07-13
Presuming it is not a spelling mistake, having quirks in 'option' is the problem; the default name for the file is /etc/modprobe.d/options, which the diagnostics script is checking for old quirks. Perhaps it should check *all* files except bcm5974. :)

---

### Post by lucianosilva on 2008-07-13
Thank you kosumi68. I'm not sure that it is a hardware failure, but I followed Alex's posts and the problem seems to be the same. 

Alex, could you please send me more information about this problem 
and what kind of repair it was necessary to fix your macbook?

And I'd like to know if it is possible to restart bcm5974 and 
keep touchpad working in the previous device so that synaptics
be able to track it again.

---

### Post by kosumi68 on 2008-07-13
Issuing this command

```

sudo rmmod bcm5974;sudo modprobe bcm5974

```

followed by a Ctrl-Alt-F1 and a Alt-F7 will have you up and running again.

---

### Post by _alex_ on 2008-07-13
Hello Luciano, I replied to your PM, but maybe it didn't go through. Here it is again:
> 
Hi Luciano,

I've posted the dmesg log for my problem in this message: [http://ubuntuforums.org/showpost.php...5&postcount=26](http://ubuntuforums.org/showpost.php...5&postcount=26)

For me whenever I firmly tapped the touchpad, the device would disconnect briefly (resulting in those log messages). If you notice a similar pattern in your case, then it's likely that you have the same defect as I did (see [http://discussions.apple.com/thread....5569&tstart=75](http://discussions.apple.com/thread....5569&tstart=75)). My top case (keyboard and touchpad) were replaced and the problem went away.

Another way to solve this is to custom compile a kernel with the quirks applied. I believe the dynamic quirks are ignored when the usb device reconnects, and so the usbhid module claims the device before bcm5974.

Alex


---

### Post by _mario_ on 2008-07-16
Hi kosumi68 and all MacBook * users,

i'd like to thank you for your work. so +1 MacBook Pro user. :)
and here comes the drawback:

after booting the machine the touchpad doesn't work, due to:
bcm5974: bad trackpad package, length: 8
After suspending and resuming the machine, its works.

some more details:
machine: MacBook Pro, Touchpad ID 0x0231
system:  Ubuntu Hardy, stack kernel 2.6.24
driver:  version 0.55 installed via dkms (precompiled module)

the full log looks like that:
usbcore: registered new interface driver bcm5974
bcm5974: Wellspring mode initialized.
input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input1
bcm5974: bad trackpad package, length: 8
bcm5974: bad trackpad package, length: 8
bcm5974: bad trackpad package, length: 8
... more of the above lines ...

after resuming:
bcm5974: disconnected
bcm5974: Wellspring mode initialized.
input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input10

do you have any idea how to solve this issue?
thanks in advance

---

### Post by kosumi68 on 2008-07-16
Hello mario, thanks for reporting! :-)

This problem is unheard of so far. Is it the 2.6.24-19-generic kernel you are running? It would be great if you could provide the output of the diagnostics program here:
```

/usr/src/bcm5974-0.55/scripts/bcm5974-diagnostics

```

it will document the result of most of the known problems, and give us something to go on.

Cheers!

---

### Post by cyberdork33 on 2008-07-16
looks like another module order problem as suspending / resuming likely just reloads the module and it starts working.

---

### Post by _mario_ on 2008-07-16
@kosumi68: yes, ubuntu's stock 2.6.24-19-generic kernel.
the diagnostics script shows nothing unusual:

```

* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-mactel1
* USB device: Bus 005 Device 003: ID 05ac:0231 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
* bcm5974: Wellspring was initialized
* synaptics: configuration readable
The bcm5974 seems properly configured

```

i omitted the synaptics driver config dump.

after thinking about that, another possibility came to my mind.
looks like cyberdork33 is right.

in contrast to your description, i additionally added this module
to /etc/initramfs-tools/modules to get it loaded early in the boot
process.

observing the logs again, i found the module being loaded before
the HID driver was initialized.

after removing the module from my initrd and rebooting, it must
have been loaded after the HID layer. and, hence, this time it
worked right after booting the machine.

not really a serious problem, but thanks and sorry for causing
confusion.

---

### Post by kosumi68 on 2008-07-16
Mario, great that you sorted it out. :)

The macbooks manage both the keyboard and the trackpad with the same usb device, which is why the load order is so important. Although not claimed, the hid module probably resets also the trackpad interface, resulting in the wrong kind of packages being sent to bcm5974 after hid is initialized. This is consistent with the error messages you get.

---

### Post by blunt.dualboot on 2008-07-17
Hi All,

I am using Macbook Pro, 4.1 Penryn. Running 8.04 Hardy Heron.

I followed the instruction from link kosumi68 posted. 

It work like a charm.
 
Thanks kosumi68. It's a magic. I can now fully enjoy my mac with mulitouch, tapping and scrolling. :)

Lovely!

---

### Post by kosumi68 on 2008-07-17
bcm5974-0.56 is out!

I stumbled across the mouse-freeze problem myself, and could finally reproduce it. In retrospect, it was easy :)

1. suspend
2. plug or unplug a usb device
3. resume

With version < 0.56, this will make your mouse freeze. With version 0.56, it should be business as usual.

This might affect the result of many of the reports regarding mouse freeze; please check :)

Cheers!

PS to avoid confusion: yes, the "Wellspring was initialized" message is now removed from the dmesg log; the driver became a bit too loud DS

---

### Post by berlandb on 2008-07-18
Hi,

it works on my Macbook Pro, too.

However, I also have the problem of the quirks apparently being ignored at boot.

The error the diagnostics scripts finds is one that was reported before.
```
* /proc/bus/input/devices: module is NOT registered
```

So after boot the trackpad works normally (no extra functions). I have to run the command that was posted earlier and restart X. I do have the right quirks commented out by the way.

```
sudo rmmod bcm5974;sudo rmmod usbhid;sudo modprobe bcm5974;sudo modprobe usbhid
```

I´m attaching the output of commands that were asked for before:

1) The, I think, relevant output of lsusb:
```
Bus 005 Device 003: ID 05ac:0231 Apple Computer, Inc.
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc.
```

2) modprobe -c |grep usbhid
```
#options usbhid quirks=0x05ac:0x0223:0x00020800,0x05ac:0x0224:0x00024800,0x05ac:0x0225:0x00020800
options usbhid quirks=0x05ac:0x0230:0x00020800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00020800
#blacklist usbhid
alias usb:v*p*d*dc*dsc*dp*ic03isc*ip* usbhid
alias symbol:hiddev_hid_event usbhid
```

3) grep usbhid /etc/modprobe.d/*
```
/etc/modprobe.d/bcm5974:#options usbhid quirks=0x05ac:0x0223:0x00020800,0x05ac:0x0224:0x00024800,0x05ac:0x0225:0x00020800
/etc/modprobe.d/bcm5974:options usbhid quirks=0x05ac:0x0230:0x00020800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00020800
/etc/modprobe.d/blacklist:#blacklist usbhid
```


But how often do you reboot anyway, right?

Thank you so much for this driver.

---

### Post by kosumi68 on 2008-07-18
berlandb, Im glad :)

One thing worth trying is to change the quirk line in /etc/modprobe.d/bcm5974 to

```

options usbhid quirks=0x05ac:0x0231:0x00024800

```

If this is really a problem with the usbhid parameter loading, it could make sense trying to set it to your specific model.

Otherwise there is also the possibility of using module alias to redefine the loading of usbhid to take explicit arguments, although I never tried this myself.

Or one could compile ones own kernel, as suggested in other posts in this thread.

Or be content and wait for intrepid :)

Cheers!

---

### Post by kosumi68 on 2008-07-19
bcm5974-0.57 is out, with minor changes. Current driver standings:

 * 2 documented Macbook Air users

 * 21 documented Macbook Pro Penryn users

Version bcm5974-0.55 is in Andrew Morton's mm tree.

Version bcm5974-0.57 was submitted to kernel.org.

The driver is on it's way into the linux-backports-modules-hardy package, I will announce when it gets there. Meanwhile, download as usual from

[http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/)

Enjoy!

---

### Post by kosumi68 on 2008-07-22
bcm5974-0.58 is out, with mostly administrative changes, and a theoretical concurrency problem fix.

This is most likely the last release as a dkms package.

Enjoy!

---

### Post by calizu15 on 2008-07-22
+ 1 for Penryn. I'm a newbie, so thank you very much for this driver and the instructions.  So far, working great. merciiiii

---

### Post by Lightgod86 on 2008-07-23
Just upgraded to 8.04 so i could utilize this, and it seems to be working however the 2 finger scrolling is not working, and 2 finger to right click is actually 3 finger...  I also noticed some long lag when i go to move the track pad if it thinks it was a click rather than a movement... Not sure exactly what it is doing.

Here is my current diagnostics report:

```

* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-1ubuntu4
* USB device: Bus 005 Device 003: ID 05ac:0230 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
Can't access shared memory area. SHMConfig disabled?
* synaptics: configuration NOT readable

```

side scrolling works fine but it is tough when it randomly clicks while trying to move it or sometimes just wont move at all...  

Might i also ask where the configuration file is located?

Either way, thanks for your constant support, couldn't have done it without dedicated people like you!

---

### Post by kosumi68 on 2008-07-23
Hello lightgod86,

thank you for providing the diagnostics output. Most likely you are missing or have a misconfigured synaptics driver. Here is what is needed:

* Open [http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html](http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html) with your web browser, and copy the InputDevice section into the file /etc/X11/xorg.conf on your computer. You need a command like
```

sudo gedit /etc/X11/xorg.conf

```
to be able to edit the file. Make sure you only have one section in there regarding the synaptics driver.

* Restart X, it is enough to logout and login again.

Rerun the diagnostics script. You should now get multi-touch and smooth mouse motion, but the two-finger-and-click will still not work. You will need a different version of the synaptics driver for that; there are instructions on the download page on how to get it.

Hope this helps! :)

---

### Post by cyberdork33 on 2008-07-23
> **kosumi68 said:**
> Rerun the diagnostics script. You should now get multi-touch and smooth mouse motion, but the two-finger-and-click will still not work. You will need a different version of the synaptics driver for that; there are instructions on the download page on how to get it.
I think he was talking about 2-finger vs 3-finger tapping for right-click which is part of the default synaptics. 

To change it to your desired functionality, you have to add the correct option in the synaptics section your xorg.conf:

From the man page([http://linux.die.net/man/5/synaptics):](http://linux.die.net/man/5/synaptics):)
> 
**TapButton1** (Integer) Which mouse button is reported on a non-corner one-finger tap. Set to 0 to disable. 
**TapButton2** (Integer) Which mouse button is reported on a non-corner two-finger tap. Set to 0 to disable. [B]
TapButton3[/B] (Integer) Which mouse button is reported on a non-corner three-finger tap. Set to 0 to disable.Left Button = 1
Middle Button = 2
Right Button = 3

---

### Post by Lightgod86 on 2008-07-23
It should have been obvious!  It worked as always, thanks a bunch, I am inlove with ubuntu on my mac now! haha

---

### Post by cutl4ss on 2008-07-31
Hello

first, this driver is great...you made a good work ;)
but my touchpad stops working after 1-2min..
i have installed it on a fresh ubuntu 8.04 installation
(only pommed&wlan-drivers are installed)

the diagnostics program shows no errors

what to do?


ps: yeees, my english is bad (i am a german)

---

### Post by cutl4ss on 2008-07-31
Ok i have tested a little bit..

first some infos:

diagnostics output
-----------------------------------------------------------------------
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-mactel1
* USB device: Bus 005 Device 065: ID 05ac:0231 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
* synaptics: configuration readable
=======================================================================
The bcm5974 seems properly configured

Your synaptics settings differ from the bcm5974 default:
-----------------------------------------------------------------------
     RTCornerButton          = 0
     ScrollButtonRepeat      = 100
     SingleTapTimeout        = 180
-    TapButton1              = 0
-    TapButton2              = 0
-    TapButton3              = 0
+    TapButton1              = 1
+    TapButton2              = 3
+    TapButton3              = 2
     TopEdge                 = 0
     TouchpadOff             = 0
     TrackstickSpeed         = 40
     UpDownScrolling         = 1
     UpDownScrollRepeat      = 1
-    VertEdgeScroll          = 0
+    VertEdgeScroll          = 1
     VertScrollDelta         = 40
     VertTwoFingerScroll     = 1
-----------------------------------------------------------------------
If in doubt, please check your /etc/X11/xorg.conf settings

I have the config "http://web.comhem.se/rydberg/Bits/xorg-settings-with-tapping.html" installed

also installed (for mac) is
pommed
ndiswrapper (wlan card)
and the module 
applesmc
loads on startup

the problem is
the touchpad works after initial start..but after 1min it stops
- with using strg+alt+f1 and strg+alt+f7 it works again for about 1min
- my bluetooth mighty mouse works normal
also my keyboard often stops working...
(no i dont touch the touchpad...)

please help me :)

(everything works under mac os/vista => so no hardware defect i guess)

---

### Post by cutl4ss on 2008-08-01
no solution?

---

### Post by cyberdork33 on 2008-08-01
> **cutl4ss said:**
> no solution?
try using it without pommed, and maybe without applesmc and see if you have the same problem.

---

### Post by cutl4ss on 2008-08-01
The same problem...

i also noticed that (without bcm5974 installed) i cant press a key and use my mouse (touchpad/mighty mouse) - is it normal?
edit: ok that was because of mouseemu, removing solves the problem..

but the other problem still exists...

---

### Post by kosumi68 on 2008-08-01
The fact that it works for an hour, then returns to normal after switching to a text console, suggests that this is indeed a hardware problem, although macos might be equipped to deal with it.

---

### Post by cutl4ss on 2008-08-02
is it possible to test for hardware defects?
=> in mac and windows it works normal....


because how should i explain it to apple? that they repair it..

---

### Post by kosumi68 on 2008-08-02
There is a hardware problem that has been reported twice for the macbook pro 4,1 laptop, with symptoms very similar to what you describe. Alex got parts of his computer replaced, no questions asked, as far as I can tell. I would try to check with him if the problem was also visible in macos.

---

### Post by cutl4ss on 2008-08-02
> **kosumi68 said:**
>  if the problem was also visible in macos.
as posted before: the problem is only visible in linux with the driver bcm5974...without everything works (except two-fingerscrolling,etc)
and in macos/windows it works also...
so i think its no hardware defect

---

### Post by kosumi68 on 2008-08-02
Sorry for being unclear. Question to alex: did your problem manifest itself also under macos?

---

### Post by kazounet on 2008-08-11
Pheew !! I've finally read all the pages of this topic. 

Thanks for your driver ! It almost always works. Yeah almost lol.

It works randomly on my Macbook Pro with ubuntu hardy 8.04. I don't know if it's a Penrynn or not. I bought it in march 2008 so I suppose it is. It says MBP 4,1 under MacOSX, and Intel Core 2 Duo under Linux with <command-name-I-forgot>


The driver works perfectly let's say .. 9 boots on 10. When it doesn't work (which means I can only left click with the button and move the mouse), I use your checkup script and of course it says the module is not loaded (but it is according to the lsmod output).

I double-checked the quirks in the modprobe file and it's ok. 

Oh and by the way, I can't ALT+F2 or ALT+anything, so I can't reload the driver. Maybe because of pommed.

Any idea?

PS: hope my english is not too bad, I'm french :)

---

### Post by cyberdork33 on 2008-08-11
> **kazounet said:**
> It works randomly on my Macbook Pro with ubuntu hardy 8.04. I don't know if it's a Penrynn or not. I bought it in march 2008 so I suppose it is. It says MBP 4,1 under MacOSX, and Intel Core 2 Duo under Linux with <command-name-I-forgot>
MacBookPro4,1 = Penryn = 4th gen = only macbook pro with this touchpad :)

> **kazounet said:**
> Oh and by the way, I can't ALT+F2 or ALT+anything, so I can't reload the driver. Maybe because of pommed.
By default, the keyboard functions the same as in OS X (for some reason) so to use F2, you actually have to hold the Fn key as well... so ALT+F2 is actually ALT+Fn+F2.

---

### Post by kosumi68 on 2008-08-11
> **kazounet said:**
> 
The driver works perfectly let's say .. 9 boots on 10. When it doesn't work (which means I can only left click with the button and move the mouse), I use your checkup script and of course it says the module is not loaded (but it is according to the lsmod output).

I double-checked the quirks in the modprobe file and it's ok. 


Yes, this is a known problem with the quirk loading in hardy 2.6.24-19. It should work better in 2.6.24-20, as the driver is included in the linux-backports-modules packages, with simplified steps to enable the multitouch features.

Cheers!

---

### Post by kazounet on 2008-08-11
Ok then +1 Penryn :)
Many thanks to you 2 for answering so quickly !

---

### Post by dkulp on 2008-08-15
This is great.   However, it's missing one feature that we have in OSX: if you put two fingers on the pad and click the button, that's the right button.  Three fingers and click and thats the middle button.

Here's a patch that adds that:

```


251,252d250
<       set_bit(BTN_RIGHT, input_dev->keybit);
<       set_bit(BTN_MIDDLE, input_dev->keybit);
255,256d252
< static int num_fingers = 0;
<
263,269c259
<       if (num_fingers == 2) {
<           input_report_key(dev->input, BTN_RIGHT, dev->bt_data->button);
<       } else if (num_fingers == 3) {
<           input_report_key(dev->input, BTN_MIDDLE, dev->bt_data->button);
<       } else {
<           input_report_key(dev->input, BTN_LEFT, dev->bt_data->button);
<       }
---
>       input_report_key(dev->input, BTN_LEFT, dev->bt_data->button);
304d293
<       num_fingers = n;


```

---

### Post by cyberdork33 on 2008-08-15
> **dkulp said:**
> This is great.   However, it's missing one feature that we have in OSX: if you put two fingers on the pad and click the button, that's the right button.  Three fingers and click and thats the middle button.
This functionality should be added to the synaptics driver not this kernel driver... a user (volanin) has published a deb for just such a driver:
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---

### Post by kosumi68 on 2008-08-16
Indeed. Since it was sort of brought up; the bcm5974 emulates a synaptics trackpad, with absolute coordinates. However, there might be times when one would like to emulate a multi-button mouse instead. I got reports that some games do not work very well with trackpads. Is there an interest to have the option of a mouse emulator as well?

---

### Post by dkulp on 2008-08-16
> **kosumi68 said:**
> Indeed. Since it was sort of brought up; the bcm5974 emulates a synaptics trackpad, with absolute coordinates. However, there might be times when one would like to emulate a multi-button mouse instead. I got reports that some games do not work very well with trackpads. Is there an interest to have the option of a mouse emulator as well?


Yes.   It would be great to be able to use gpm for console sessions.

---

### Post by kosumi68 on 2008-08-25
The BCM5974 driver is now part of 2.6.27 upstream, and has been incorporated into Intrepid, meaning the driver will work out-of-the-box. As for Hardy, the kernel image 2.6.24-21 is not out yet, but as soon as it is (the -20 has been skipped it seems), these are the steps to enable the driver:

* Use the package manager to install this package:
```

linux-backports-modules-hardy

```

* add the following line to /etc/initramfs-tools/modules:
```

lbm_bcm5974

```

* update the ramdisk using the following command:
```

sudo update-initramfs -u -v -k 2.6.24-21-generic

```

* reboot

Enjoy!

---

### Post by Red/Grey on 2008-08-27
Strangest thing, i think, i'm very new at this...

I can't get the two finger scroll to work properly. If i drag two/three fingers along the touchpad the pointer stops moving, but other than that nothing happens.

I have a MBA and I've tried to follow this guide to the very limit my brain lets me. One thing puzzles me a bit tough. I've added the size of the MBA's touchpad which, if i understood it correctly, should disable the "right-edge-of-touchpad-scroll". But it has not...?

I have tried to load/unload the driver, uninstall/install it, but no results...

Any help would be most appreciated!

---

### Post by cyberdork33 on 2008-08-27
I think you still have to set those options in your synaptic config (in xorg.conf) namely, set VertEdgeScroll to 0 and VertTwoFingerScroll to 1

To see all the possible options run 'man synaptics' int the terminal or see here:
[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

---

### Post by kosumi68 on 2008-08-27
> **Red/Grey said:**
> 

I have a MBA and I've tried to follow this guide to the very limit my brain lets me. One thing puzzles me a bit tough. I've added the size of the MBA's touchpad which, if i understood it correctly, should disable the "right-edge-of-touchpad-scroll". But it has not...?



Just to make sure what your setup is, could you perhaps provide the output of this command:

```

/usr/src/bcm5974-0.58/scripts/bcm5974-diagnostics

```

---

### Post by Red/Grey on 2008-08-29
Before i had the chance to try the answers i got., I somehow managed to make my keyboard stop working... Since I'm very new to this i took the easy way out and reinstalled Ubuntu from scratch.

After following this thread a second time, the driver works just fine! :)

Thanks for the effort!

---

### Post by e-gandalf on 2008-08-29
I installed daily Ubuntu 8.10 on MBP Penryn and the new drive doesn't work :(

If I try to do rmmod bcm5974;rmmod usbhci;modprobe bcm5974;modpobe usbhci the keyboard/mouse (usb) stop responding after rmmod usbhci, but it doesn't help at all...

Trying the diagnostic script tells me:

"Can't access shared memory area. SHMConfig disabled?" even when usbhci is unloaded.

after reloading bcm5974 dmesg says:

[12920.447443] usbcore: deregistering interface driver bcm5974
[12924.742711] input: bcm5974 as /class/input/input35
[12924.812366] usbcore: registered new interface driver bcm5974


Any help?

---

### Post by kosumi68 on 2008-08-29
I believe you are first out to test this on the complete Intrepid distro - I only tested the 2.6.27 kernel so far myself. :-)

First of all - make sure all references to the DKMS version are viped out - this includes checking with modprobe -l that only the 2.6.27 version of bcm5974 is available, and that no reference to bcm5974 is present in /etc/modprobe.d/ (uninstalling the driver with dkms should do the trick).

This is the experience you should expect from the 2.6.27 kernel: When booting, the bcm5974 driver should pick the trackpad up, and according to

[12924.742711] input: bcm5974 as /class/input/input35

it does, registering an input device for it. What puzzles me is the /class part. If you check /proc/bus/input/devices, you should find a bcm5974 device in there. If not, that would explain why synaptics does not pick it up. Another possibility is that the problem is related to the new xorg server version - see [http://ubuntuforums.org/showthread.php?p=5293527&highlight=heads#post5293527](http://ubuntuforums.org/showthread.php?p=5293527&highlight=heads#post5293527).

---

### Post by e-gandalf on 2008-08-30
is it possible that there's a conflict with nvidia glx driver? It installs some DKMS (at least that's what was in the log from nvidia driver installation)

regarding /proc:

root@gbook:~# cd /proc/bus/input/devices
bash: cd: /proc/bus/input/devices: Not a directory

---

### Post by kosumi68 on 2008-08-30
I dont think this is related to any other driver. I will be back with some further testing - thanks for the reports!

---

### Post by kosumi68 on 2008-08-31
I tested Interpid daily today, 31AUG2008. The kernel is now 2.6.27-2, and the bcm5974 driver is loaded and installed properly; it is represented in the file /proc/bus/input/devices. As reported by e-gandalf, the mouse does not move. This has to do with the bcm5974 acting as a trackpad only - not as an ordinary mouse. After configuring the /etc/X11/xorg.conf, in my case by copying the one from my hardy installation, the mouse is working fine.

In summary, the trackpad driver works fine given a proper configuration of the synaptics driver.

It would make a lot of sense if the bcm5974 driver could also act as an ordinary mouse, as suggested earlier in this thread. I will look into it.

---

### Post by cyberdork33 on 2008-08-31
follow the bug report here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/263451](https://bugs.edge.launchpad.net/mactel-support/+bug/263451)

---

### Post by kosumi68 on 2008-09-01
The bcm5974-0.60 is out!

This version includes a mouse compatibility mode, and works even without configuring the Xorg synaptics driver. The features of the mouse mode are in short:

* The default Xorg configuration will pick up the mouse input interface, resulting in a functional mouse pointer out-of-the-box.

* Two-finger scroll works without the need to configure the synaptics driver.

* Multi-finger button emulation, which currently only exists in the mactel version of the synaptics driver, works out-of-the-box.

* The mouse driver also works with gpm in text consoles, providing cut-and-paste functionality via the multi-button emulation.

The version is available for hardy at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/).

Enjoy!

---

### Post by cyberdork33 on 2008-09-01
> **kosumi68 said:**
> The bcm5974-0.60 is out!

This version includes a mouse compatibility mode, and works even without configuring the Xorg synaptics driver. The features of the mouse mode are in short:

* The default Xorg configuration will pick up the mouse input interface, resulting in a functional mouse pointer out-of-the-box.

* Two-finger scroll works without the need to configure the synaptics driver.

* Multi-finger button emulation, which currently only exists in the mactel version of the synaptics driver, works out-of-the-box.

* The mouse driver also works with gpm in text consoles, providing cut-and-paste functionality via the multi-button emulation.

The version is available for hardy at [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/).

Enjoy!
Interesting that you decided to put all that in the actual kernel driver. I guess that makes it easier for the one-button touchpads though.

---

### Post by kosumi68 on 2008-09-01
Yes, it sure does - and given that not all linux systems use auxiliary drivers like synaptics to produce input, it seemed worthwhile. Actually, every mouse driver does about the same thing - it is not a lot of code. The drawback as I see it is a somewhat shared (or blurry if you wish) responsibility between the lowest level drivers and the functionality level, like Xorg. On the other hand, this distinction is hard to make: what part is responsible for input configuration in a text console?

---

### Post by kosumi68 on 2008-09-01
The bcm5974-0.61 is out, with smoother pointer motion in the compatibility mouse interface.

Enjoy!

---

### Post by kosumi68 on 2008-09-02
Ok, bcm5974-0.62 is out. The mouse compatibility mode was a bit on the extravagant side, in particular for upstream to swallow. Besides, it turned out there was an interface mismatch between bcm5974 and mousedev, which is already capable of emulating a simple mouse from a touchpad. Once corrected, the pointer works out-of-the-box. We don't get the right-click emulation this way, but who knows - maybe it will turn up in mousedev one day :-)

Enjoy!

---

### Post by letic on 2008-09-03
Hey Henryk,

As you might remember I've been using the driver for a long time and if it's working great there is one thing that bugs me.

It seems the driver doesn't work correctly when pressing a key at the same time. For example when trying to open a link in a new tab in Firefox when pressing Ctrl and tap on the touchpad.

Same when trying to zoom with compiz fusion : super + 2 fingers scroll will only works randomly.

So I was wondering if the behavior was the same for everybody ot if it was an issue on my MacBook Pro, and if it is how can I troubleshoot it ?

Let me know what info you would need
Cheers
LeTic

---

### Post by kosumi68 on 2008-09-03
Welcome back, letic :-)

Actually, Ctrl+Tap to open link in new tab, Ctrl+Click to open link in new tab, Meta+DoubleTap to move a window, and Meta+TwoFingerScoll to resize text works fine in my setup. Perhaps you could provide the output of this command (assuming you run the latest version, 0.64):

```

/usr/src/bcm5974-0.64/scripts/bcm5974-diagnostics

```

---

### Post by letic on 2008-09-03
> **kosumi68 said:**
> Welcome back, letic :-)

He he not my fault if it worked the first time but I was still lurking :)

> Actually, Ctrl+Tap to open link in new tab, Ctrl+Click to open link in new tab, Meta+DoubleTap to move a window, and Meta+TwoFingerScoll to resize text works fine in my setup.

Hum I was afraid of that...

>  Perhaps you could provide the output of this command (assuming you run the latest version, 0.64):

```

/usr/src/bcm5974-0.64/scripts/bcm5974-diagnostics

```

Jeez you are quick to release :) I just upgraded to the 0.62 a couple of hours ago.

Here you go :
```
/usr/src/bcm5974-0.64/scripts/bcm5974-diagnostics
-----------------------------------------------------------------------
* Kernel version: 2.6.24-19-generic
* Synaptics version: 0.14.7~git20070706-mactel1
* USB device: Bus 005 Device 003: ID 05ac:0230 Apple Computer, Inc.
* /lib/modules/2.6.24-19-generic/updates/dkms/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.24-19-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
* synaptics: configuration readable
=======================================================================
The bcm5974 seems properly configured

Your synaptics settings differ from the bcm5974 default:
-----------------------------------------------------------------------
     EmulateTwoFingerMinZ    = 257
     FastTaps                = 0
     FingerHigh              = 80
-    FingerLow               = 16
+    FingerLow               = 30
     FingerPress             = 256
     GrabEventDevice         = 1
     GuestMouseOff           = 0
@@ -36,7 +36,7 @@
     MaxTapTime              = 223
     MinSpeed                = 0.8
     MultiFingerButton       = 2
-    PalmDetect              = 0
+    PalmDetect              = 1
     PalmMinWidth            = 10
     PalmMinZ                = 200
     PressureMotionMaxFactor = 1
@@ -48,14 +48,14 @@
     RTCornerButton          = 0
     ScrollButtonRepeat      = 100
     SingleTapTimeout        = 180
-    TapButton1              = 0
-    TapButton2              = 0
-    TapButton3              = 0
+    TapButton1              = 1
+    TapButton2              = 3
+    TapButton3              = 2
     TopEdge                 = 0
-    TouchpadOff             = 0
+    TouchpadOff             = 2
     TrackstickSpeed         = 40
     UpDownScrolling         = 1
     UpDownScrollRepeat      = 1
-    VertEdgeScroll          = 0
+    VertEdgeScroll          = 1
     VertScrollDelta         = 40
     VertTwoFingerScroll     = 1

```

As you can see I'm using the Xorg settings with tapping and palm detection.

Is there a way to turn the logging on ?

Cheers
LeTic

---

### Post by kosumi68 on 2008-09-03
> **letic said:**
> 
Jeez you are quick to release :) I just upgraded to the 0.62 a couple of hours ago.

Rather somewhat trigger happy :-) communication upstream creates some additional work, I guess thats why there are sometimes bursts of releases.

Your system seems perfectly in order... you can turn on bcm5974 logging for instance by issuing
```

sudo rmmod bcm5974; sudo insmod /lib/modules/`uname -r`/updates/dkms/bcm5974.ko debug=99

```

beware that the synaptics driver switches to the backup mouse driver when restarting the driver (no multitouch features enabled); you need to do a Ctrl-Alt-F1 followed by Alt-F7 to force synaptics to get back bcm5974.

Dont forget to change the debug level back to zero after youre done :-)

Cheers!

---

### Post by kosumi68 on 2008-09-03
However, since you are stating a problem with the keyboard and tapping, perhaps you want to have a look at the xev output instead. Does it work to do Ctrl+MouseClick?

---

### Post by cyberdork33 on 2008-09-03
> **letic said:**
> It seems the driver doesn't work correctly when pressing a key at the same time. For example when trying to open a link in a new tab in Firefox when pressing Ctrl and tap on the touchpad.
Before you get too much further on debugging this, make sure that mouseemu is  disabled. This has been a issue since I can remember:
[http://ubuntuforums.org/showthread.php?t=545244](http://ubuntuforums.org/showthread.php?t=545244)

(Or you can just uninstall it as I don't think it is even needed on Intel Macs).

---

### Post by letic on 2008-09-04
> **kosumi68 said:**
> 
Your system seems perfectly in order... you can turn on bcm5974 logging for instance by issuing
```

sudo rmmod bcm5974; sudo insmod /lib/modules/`uname -r`/updates/dkms/bcm5974.ko debug=99

```


Thanks for that I'll try it tonight.

> **kosumi68 said:**
> However, since you are stating a problem with the keyboard and tapping, perhaps you want to have a look at the xev output instead. Does it work to do Ctrl+MouseClick?

Yes the Ctrl+Click works and I don't have the consistency issue that I have with the Ctrl+Tap. To clarify :
  - Ctrl + Click : works all the time
  - Ctrl + Tap works intermittently. Once it worked, it's usually working until I release the Ctrl key. 

> **cyberdork33 said:**
> Before you get too much further on debugging this, make sure that mouseemu is  disabled. This has been a issue since I can remember:
[http://ubuntuforums.org/showthread.php?t=545244](http://ubuntuforums.org/showthread.php?t=545244)

(Or you can just uninstall it as I don't think it is even needed on Intel Macs).

Cheers for that Cyberdork I'll check it as well :)

I'll let you know tonight how it went
Thanks for the tips

Cheers
LeTic

---

### Post by wisedrunkard on 2008-09-04
I'm a total newb how do i start my own thread... i have a problem i need help with, thx for the help

---

### Post by letic on 2008-09-04
Ok I checked and the mouseemu package is not even installed.

The debug output didn't show any differences in ouput when taping while pressing or not a key.

Then I remember that I used touchd before bcm5974 and that I enabled syndaemon to disable the touchpad while typing...

Removing syndaemon from the boot services solved my issue...

Sorry about the noise lads, thanks for pointing me in the right direction :)

Cheers
LeTic

---

### Post by kosumi68 on 2008-09-17
Status report
-------------

Latest release: bcm5974-0.65.

Native support in kernel since 2.6.27-rc5.

Native support in Xorg since synaptics-0.15.2.

Intrepid: Works out-of-the box since alpha-5.

Hardy: Use the DKMS package for latest version.

---

### Post by metajack on 2008-09-18
I have a Macbook Air and had the driver working perfectly using the mactel synaptics driver.  I have just upgraded to intrepid, and now the mouse still works, but two finger right click no longer works.  Two finger swipe still seems to change desktops.

My config is the no-tapping config from [http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html](http://web.comhem.se/rydberg/Bits/xorg-settings-without-tapping.html)

Below is the output from the diagnostics script.

Any ideas how I can get right click back?

-----------------------------------------------------------------------
* Kernel version: 2.6.27-3-generic
* Synaptics version: 0.15.2-0ubuntu1
* USB device: Bus 006 Device 003: ID 05ac:0223 Apple, Inc.
* /lib/modules/2.6.27-3-generic/kernel/drivers/input/mouse/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: no obsolete quirks, good
* /etc/modprobe.d/bcm5974: has quirks, good
* /lib/modules/2.6.27-3-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
* synaptics: configuration readable
=======================================================================
The bcm5974 seems properly configured

Your synaptics settings differ from the bcm5974 default:
-----------------------------------------------------------------------
     CircScrollTrigger       = 0
     CircularPad             = 0
     CircularScrolling       = 0
+    ClickFinger1            = 1
+    ClickFinger2            = 3
+    ClickFinger3            = 2
     ClickTime               = 100
     CoastingSpeed           = 0
     CornerCoasting          = 0
-    EdgeMotionMaxSpeed      = 80
+    EdgeMotionMaxSpeed      = 128
     EdgeMotionMaxZ          = 160
     EdgeMotionMinSpeed      = 1
     EdgeMotionMinZ          = 30
@@ -32,10 +35,9 @@
     LTCornerButton          = 0
     MaxDoubleTapTime        = 200
     MaxSpeed                = 1.2
-    MaxTapMove              = 100
-    MaxTapTime              = 223
+    MaxTapMove              = 25
+    MaxTapTime              = 180
     MinSpeed                = 0.8
-    MultiFingerButton       = 2
     PalmDetect              = 0
     PalmMinWidth            = 10
     PalmMinZ                = 200
@@ -56,6 +58,6 @@
     TrackstickSpeed         = 40
     UpDownScrolling         = 1
     UpDownScrollRepeat      = 1
-    VertEdgeScroll          = 0
+    VertEdgeScroll          = 1
     VertScrollDelta         = 40
     VertTwoFingerScroll     = 1

---

### Post by kosumi68 on 2008-09-18
Intrepid uses synaptics-0.15.2, which has multi-finger clicks, but it was implemented in a different way (more people than ubuntu had this idea, it seems). To enable multi-finger clicks in intrepid, these are the settings:

```

        Option          "ClickFinger1"  "1"
        Option          "ClickFinger2"  "3"
        Option          "ClickFinger3"  "2"

```

---

### Post by cyberdork33 on 2008-09-18
> **kosumi68 said:**
> Intrepid uses synaptics-0.15.2, which has multi-finger clicks, but it was implemented in a different way (more people than ubuntu had this idea, it seems). To enable multi-finger clicks in intrepid, these are the settings:

```

        Option          "ClickFinger1"  "1"
        Option          "ClickFinger2"  "3"
        Option          "ClickFinger3"  "2"

```
It looks like he already has those enabled, or maybe I am misunderstanding his previous output...

---

### Post by kosumi68 on 2008-09-18
> **cyberdork33 said:**
> It looks like he already has those enabled, or maybe I am misunderstanding his previous output...

Hehe, I am blind :-)

With synaptics-0.15.2, there are some quite subtle problems with parameter loading, because these is a new kid on the block: hal fdi configuration. It helps out auto-loading the right drivers, but currently also creates troubles if one uses synaptics settings in /etc/X11/xorg.conf.

This is something to try: move the fdi file somewhere, and restart hal:
```

sudo mv /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi ~/somewhere
sudo /etc/init.d/hal restart

```
then restart Xorg by logging out and in again.

---

### Post by kosumi68 on 2008-09-18
I am writing this from the Intrepid Daily 17SEP2008 Live CD:

* Two-finger click works

* Three-finger click works

* Two-finger scrolling works

The name of the fdi file is
```

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

```
thus not in /etc as I said above. I will edit.

(As a side note, I run on a MBA, and all I need to do to enable wireless is 'sudo rmmod ssb;sudo modprobe wl'. Splendid!)

---

### Post by cyberdork33 on 2008-09-18
> **kosumi68 said:**
> (As a side note, I run on a MBA, and all I need to do to enable wireless is 'sudo rmmod ssb;sudo modprobe wl'. Splendid!)

Yes, it is quite nice to have a broadcom driver available now...

---

### Post by metajack on 2008-09-18
> **kosumi68 said:**
> Hehe, I am blind :-)


Actually even though the tool says those are there, they weren't.  I added them and moved the fdi file and all is well again.

[QUOTE=kosumi68](As a side note, I run on a MBA, and all I need to do to enable wireless is 'sudo rmmod ssb;sudo modprobe wl'. Splendid!) 
[/QUOTE]

Is there some way to make it not load ssb?  Putting ssb in /etc/modprobe.d/blacklist does not seem to work.  Thanks for pointing out wl though.  I was still using ndiswrapper on intrepid.

And this is completely off topic, but have you had any trouble with emacs-snapshot-gtk or other gnome-session things crashing or refusing to load on your MBA?  The specific error i get is:

x-session-manager[6383]: DEBUG(+): GsmXsmpServer: sms_error_handler (0x9ed9260, FALSE, 3, 9, 32771, 0)

jockey-gtk also crashes on startup whenever I log in.

---

### Post by cyberdork33 on 2008-09-18
> **metajack said:**
> Is there some way to make it not load ssb?  Putting ssb in /etc/modprobe.d/blacklist does not seem to work.  Thanks for pointing out wl though.  I was still using ndiswrapper on intrepid.
We discuss it here:
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

I'd say that it is loading ssb when b43 or something tries to load.

---

### Post by metajack on 2008-09-18
> **cyberdork33 said:**
> We discuss it here:
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)


Thanks for the pointer!

---

### Post by JairunCaloth on 2008-09-21
I just want to say thanks for this driver. I ran around in circles before I ran into it. Then life got much better :)

---

### Post by JonasPetersson on 2008-09-25
Yes, I have to agree that bcm5974 really makes a huge difference in usability of my MBP.

One thing to remember if you are as teflon minded as me:

If you install a recent version (say 0.6x) and later upgrade restricted modules things may seem to break. 

The problem is then (probably) that an older module has been installed along with old config. Just reinstalling the newer version will not help.
The fix is to run the bcm5974-diagnostics script to track down the inconsistencies.

Best / Jonas

---

### Post by kosumi68 on 2008-10-09
I am turning this thread to solved. Thanks to everyone who helped out testing the driver, and enjoy!

---

### Post by i-Mac on 2008-10-09
Perhaps the wrong topic sorry





)

Greetings to you

---

### Post by cyberdork33 on 2008-10-09
> **i-Mac said:**
> Waiting for your assistance in the best
(I am sorry not good at English )

Greetings to youYou will have to post a new thread and give details about your problem.

---

### Post by i-Mac on 2008-10-09
> **cyberdork33 said:**
> You will have to post a new thread and give details about your problem.

:confused:

---

### Post by Rekoil on 2008-10-16
Has anyone on here had time to analyse the new MacBook Pro? Does it feature the BCM5974 as well?

---

### Post by kosumi68 on 2008-10-16
> **Rekoil said:**
> Has anyone on here had time to analyse the new MacBook Pro? Does it feature the BCM5974 as well?

It is two days old... within the next two weeks is my guess. Then we should have a pretty good picture of the new machines.

---

### Post by Rekoil on 2008-10-16
> **kosumi68 said:**
> It is two days old... within the next two weeks is my guess. Then we should have a pretty good picture of the new machines.

Haha, very true. Was just hoping someone had had time to check already, I'm looking for hope that they will add 4-finger swipe support to the Penryn MBP.

Sorry for posting in an old thread.

---

### Post by cyberdork33 on 2008-10-16
> **Rekoil said:**
> Haha, very true. Was just hoping someone had had time to check already, I'm looking for hope that they will add 4-finger swipe support to the Penryn MBP.

Sorry for posting in an old thread.

as far as I know, the Penryn MacBook Pro touchpad can track up to something like 11 fingers. (I know the guy that demoed it had to get a friend to help him to max it out.) You can see him get at least 8 in this video:
[http://www.youtube.com/watch?v=Hek22LtL5XY](http://www.youtube.com/watch?v=Hek22LtL5XY)

His old site is gone, so I can't find the older video that showed more.

---

### Post by Rekoil on 2008-10-18
> **cyberdork33 said:**
> as far as I know, the Penryn MacBook Pro touchpad can track up to something like 11 fingers. (I know the guy that demoed it had to get a friend to help him to max it out.) You can see him get at least 8 in this video:
[http://www.youtube.com/watch?v=Hek22LtL5XY](http://www.youtube.com/watch?v=Hek22LtL5XY)

His old site is gone, so I can't find the older video that showed more.

I know the hardware supports it, but that doesn't mean Apple will enable it in OS X for the old laptops. Hopefully they do :) (I'm talking about the 4-finger swipes).

---

### Post by cyberdork33 on 2008-10-18
> **Rekoil said:**
> I know the hardware supports it, but that doesn't mean Apple will enable it in OS X for the old laptops. Hopefully they do :) (I'm talking about the 4-finger swipes).

OK, I didn't realize they did it different.

---

### Post by MaddMatt on 2008-10-20
Has anyone had any luck getting right-left scrolling (two finger) ability out of this driver? I can't seem to get that to work right in Hardy- or is this just a matter of upgrading Synaptics as described earlier?

Thanks, 
M

---

### Post by kosumi68 on 2008-10-25
The latest version of bcm5974 is from now on available as a package in the mactel PPA; see the updated first post in this thread.

Cheers!

---

### Post by tannewt on 2008-11-01
Hey Kosumi great work on the kernel module.  I'm glad touchd was a precursor to this.  I just moved to intrepid and your module.  Its working well.  The config was a bit wierd but got it.  Thanks also for the acknowledgement.  For those of you who wanted to see all the videos I made they should all be accessible from my YouTube page.

---

### Post by cyberdork33 on 2008-11-01
> **tannewt said:**
> Hey Kosumi great work on the kernel module.  I'm glad touchd was a precursor to this.  I just moved to intrepid and your module.  Its working well.  The config was a bit wierd but got it.  Thanks also for the acknowledgement.  For those of you who wanted to see all the videos I made they should all be accessible from my YouTube page.
hey! Long time, no see!

---

### Post by ichekryg on 2008-11-07
Hello, I am running MBP 8.10 64bit and have continuous issue with bcm5974.
I was wondering if anyone else has experienced the same problem and has or can point me to a solution.
dmesg:
[  481.521841] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  481.521860] usb 6-2: USB disconnect, address 16
[  481.523642] bcm5974: bcm5974: button urb failed: -19
[  481.644148] bcm5974: bcm5974: could not read from device
[  481.904118] usb 6-2: new full speed USB device using uhci_hcd and address 17
[  482.093905] usb 6-2: configuration #1 chosen from 1 choice
[  482.104922] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input38
[  482.141155] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  482.610236] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  482.620755] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input39

---

### Post by kosumi68 on 2008-11-08
> bcm5974: bcm5974: button urb failed: -19

ENODEV - no such device.

Are you using the 2.6.27 kernel from Intrepid?

Just to make sure the problem is not connected to the recent kernel upgrade, please reinstall the bcm5974 package.

What machine model do you have?
```

sudo dmidecode | grep Product

```

What is your usb device id?
```

lsusb | grep 05ac

```

> hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...

So the trackpad works initially, then this happens, and it stops working? There were similar issues back in May, and it was discovered to be a hardware problem on some machines: [http://ubuntuforums.org/showpost.php?p=5286529&postcount=27](http://ubuntuforums.org/showpost.php?p=5286529&postcount=27)

---

### Post by ichekryg on 2008-11-09
Yes, I am using Intrepid.

After upgrading to new kernel (2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux), i did reinstall bcm5974-dkms.

~$ sudo dmidecode | grep Product
	Product Name: MacBookPro4,1
	Product Name: Mac-F42C89C8

~$ lsusb | grep 05a
Bus 007 Device 002: ID 05ac:8502 Apple, Inc. 
Bus 003 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 006 Device 005: ID 05ac:0230 Apple, Inc. 
Bus 006 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 001 Device 005: ID 05ac:820f Apple, Inc. 

I did come across this thread (defective connector for MBP - [http://ubuntuforums.org/showpost.php?p=5286529&postcount=27);](http://ubuntuforums.org/showpost.php?p=5286529&postcount=27);) however, i was not able to reproduce this problem on OsX. Maybe I wasn't using it long enough ;). The "tissue patch" solution" mentioned in that forum did not work for me either. 

bmc5974 manifests under other error messages as well, here is the tail of my dmesg:

[118860.005138] bcm5974: bcm5974: could not read from device
[118860.257060] usb 6-2: new full speed USB device using uhci_hcd and address 11
[118860.455621] usb 6-2: configuration #1 chosen from 1 choice
[118860.474700] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input278
[118860.512244] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118860.534778] usbhid: ctrl urb status -75 received
[118860.534902] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118860.540895] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input279
[118860.601897] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[118860.601905] usb 6-2: USB disconnect, address 11
[118860.648236] bcm5974: bcm5974: could not read from device
[118860.648246] bcm5974: mode switch failed
[118860.977052] usb 6-2: new full speed USB device using uhci_hcd and address 12
[118861.169717] usb 6-2: configuration #1 chosen from 1 choice
[118861.182453] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input280
[118861.238094] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118861.689761] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118861.695278] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input281
[118895.568201] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[118895.568225] usb 6-2: USB disconnect, address 12
[118895.571802] bcm5974: bcm5974: button urb failed: -19
[118895.704217] bcm5974: bcm5974: could not read from device
[118895.960257] usb 6-2: new full speed USB device using uhci_hcd and address 13
[118896.147238] usb 6-2: configuration #1 chosen from 1 choice
[118896.155914] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input282
[118896.186556] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118896.663620] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118896.668294] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input283
[118897.305151] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[118897.305174] usb 6-2: USB disconnect, address 13
[118897.308772] bcm5974: bcm5974: trackpad urb failed: -19
[118897.424257] bcm5974: bcm5974: could not read from device
[118897.696160] usb 6-2: new full speed USB device using uhci_hcd and address 14
[118897.883134] usb 6-2: configuration #1 chosen from 1 choice
[118897.894343] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input284
[118897.932363] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118898.402455] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118898.412792] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input285
[118905.736234] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[118905.736255] usb 6-2: USB disconnect, address 14
[118905.739767] bcm5974: bcm5974: button urb failed: -19
[118905.849216] bcm5974: bcm5974: could not read from device
[118906.108229] usb 6-2: new full speed USB device using uhci_hcd and address 15
[118906.299207] usb 6-2: configuration #1 chosen from 1 choice
[118906.308384] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input286
[118906.364352] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118906.457801] usbhid: ctrl urb status -75 received
[118906.457930] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118906.462997] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input287
[118906.522907] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[118906.522915] usb 6-2: USB disconnect, address 15
[118906.552224] bcm5974: bcm5974: could not read from device
[118906.552233] bcm5974: mode switch failed
[118906.872193] usb 6-2: new full speed USB device using uhci_hcd and address 16
[118907.060262] usb 6-2: configuration #1 chosen from 1 choice
[118907.069371] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input288
[118907.122385] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118907.577511] hidraw3: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[118907.584980] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input289

---

### Post by kosumi68 on 2008-11-10
The hardware problem only showed in linux.

> **ichekryg said:**
> 
Bus 003 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub


Don't recognize this one. Is it external? It would also be interesting to see the full usb listing if the 05ac:0230 device after the failure.
```

sudo lsusb -vvv -d 05ac:0230

```

---

### Post by ichekryg on 2008-11-10
[22434.976158] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[22434.976171] usb 6-2: USB disconnect, address 77
[22435.352199] usb 6-2: new full speed USB device using uhci_hcd and address 78
[22435.543522] usb 6-2: configuration #1 chosen from 1 choice
[22435.553705] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input162
[22435.601302] input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[22436.060895] hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[22436.070403] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input163
illyac@illya-laptop:~$ sudo lsusb -vvv -d 05ac:0230
[sudo] password for illyac: 

Bus 006 Device 080: ID 05ac:0230 Apple, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x0230 
  bcdDevice            0.70
  iManufacturer           1 Apple, Inc.
  iProduct                2 Apple Internal Keyboard / Trackpad
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              3 Apple Internal Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     156
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              4 Touchpad
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      27
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              4 Touchpad
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

---

### Post by ichekryg on 2008-11-10
< The hardware problem only showed in linux.
I think i am able to verify and confirm that this issue due to the faulty hardware (as described in [http://ubuntuforums.org/showpost.php?p=5286529&postcount=27](http://ubuntuforums.org/showpost.php?p=5286529&postcount=27))

Is there any fix for this on the linux side?

---

### Post by kosumi68 on 2008-11-10
> **ichekryg said:**
> < The hardware problem only showed in linux.
I think i am able to verify and confirm that this issue due to the faulty hardware (as described in [http://ubuntuforums.org/showpost.php?p=5286529&postcount=27](http://ubuntuforums.org/showpost.php?p=5286529&postcount=27))
> 

Thanks for the output. I compared it to the standard layout - I wanted to make sure nothing odd was going on with the usb interface mapping. It all looks normal. Seems you were unlucky to get one of the flaky machines :-(

[QUOTE]
Is there any fix for this on the linux side?


I will have a look at possible recovery options in the driver, but it does not look promising. Closing and reopening the device might do it as a temporery fix, but as long as X is running, this does not happen without force. You can reload the driver to get it running again
```

sudo rmmod bcm5974; sudo modprobe bcm5974 debug=3

```

---

### Post by kosumi68 on 2008-11-10
I edited the last post; running with debug=3 will give an additional bit of crucial information as to why the drive does not recover properly. If you would like to run with that option for or a while, and when the problem occurs, report a good chunk of your dmesg, it would help.

Just to make sure what the symptoms are: first you have no problems, then suddenly something stops working. Frozen mouse? No multi-touch? A detailed description of the actual symptoms will also help.

Thanks!

---

### Post by ichekryg on 2008-11-12
The issue manifests itself with intermittent interrupts in keyboard responsiveness. For example, when i type all the sudden keyboard stops working, pressing any buttons has no effect what-so-ever.  This lasts about a second or two, then it resumes back to normal. I don't use touchpad much (external mouse), so i didn't test the touchpad responsiveness. Again, the issue lasts about sec or two, so by the time i've realized i have an issue, it is gone. The issue can start (and usually does) right from the logon screan; i.e. i can detect keyboard malfunction while typing my user name/password.

Here is the dmesg before bcm reload (issue already detected):
[  537.320309] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  537.320329] usb 6-2: USB disconnect, address 6
[  537.425208] bcm5974: bcm5974: could not read from device
[  537.696202] usb 6-2: new full speed USB device using uhci_hcd and address 7
[  537.882815] usb 6-2: configuration #1 chosen from 1 choice
[  537.892955] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input22
[  537.933290] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  538.072301] usbhid: ctrl urb status -75 received
[  538.073803] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  538.075718] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input23
[  538.179387] bcm5974: bcm5974: could not read from device
[  538.179405] bcm5974: mode switch failed
[  538.312110] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  538.312131] usb 6-2: USB disconnect, address 7
[  538.660214] usb 6-2: new full speed USB device using uhci_hcd and address 8
[  538.855360] usb 6-2: configuration #1 chosen from 1 choice
[  538.866470] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input24
[  538.924537] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  539.374466] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  539.379134] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input25

this is where i reloaded bcm driver

[  634.741581] usbcore: deregistering interface driver bcm5974
[  634.827952] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input26
[  634.868159] usbcore: registered new interface driver bcm5974
[  634.930871] bcm5974: switched to wellspring mode.
[  634.965870] bcm5974: switched to normal mode.
[  634.981901] bcm5974: switched to wellspring mode.
[  635.000876] bcm5974: switched to normal mode.
[  635.031960] bcm5974: switched to wellspring mode.
[  635.049941] bcm5974: switched to normal mode.
[  635.083929] bcm5974: switched to wellspring mode.
[  635.097916] bcm5974: switched to normal mode.
[  635.122908] bcm5974: switched to wellspring mode.
[  722.824246] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  722.824271] usb 6-2: USB disconnect, address 8
[  722.827901] bcm5974: bcm5974: button urb failed: -19
[  722.940250] bcm5974: bcm5974: could not read from device
[  723.196201] usb 6-2: new full speed USB device using uhci_hcd and address 9
[  723.380065] usb 6-2: configuration #1 chosen from 1 choice
[  723.388174] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input27
[  723.437504] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  723.896531] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  723.905816] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input28
[  724.079285] bcm5974: switched to wellspring mode.
[  724.121275] bcm5974: switched to normal mode.
[  724.146273] bcm5974: switched to wellspring mode.
[  724.173253] bcm5974: switched to normal mode.
[  724.204359] bcm5974: switched to wellspring mode.
[  724.235357] bcm5974: switched to normal mode.
[  724.260258] bcm5974: switched to wellspring mode.
[  789.040248] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  789.040270] usb 6-2: USB disconnect, address 9
[  789.041784] bcm5974: bcm5974: trackpad urb failed: -19
[  789.148258] bcm5974: bcm5974: could not read from device
[  789.420180] usb 6-2: new full speed USB device using uhci_hcd and address 10
[  789.608922] usb 6-2: configuration #1 chosen from 1 choice
[  789.620088] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input29
[  789.684297] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  790.127080] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  790.134937] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input30
[  790.335172] bcm5974: switched to wellspring mode.
[  790.366151] bcm5974: switched to normal mode.
[  790.411247] bcm5974: switched to wellspring mode.
[  790.430234] bcm5974: switched to normal mode.
[  790.455228] bcm5974: switched to wellspring mode.
[  790.470210] bcm5974: switched to normal mode.
[  790.495198] bcm5974: switched to wellspring mode.
[  790.509193] bcm5974: switched to normal mode.
[  790.536168] bcm5974: switched to wellspring mode.
[  810.120273] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  810.120295] usb 6-2: USB disconnect, address 10
[  810.123277] bcm5974: bcm5974: button urb failed: -19
[  810.249303] bcm5974: bcm5974: could not read from device
[  810.523722] usb 6-2: new full speed USB device using uhci_hcd and address 11
[  810.712368] usb 6-2: configuration #1 chosen from 1 choice
[  810.721539] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input31
[  810.774794] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  811.229061] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
[  811.230962] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input32
[  811.358618] bcm5974: switched to wellspring mode.
[  811.393622] bcm5974: switched to normal mode.
[  811.434612] bcm5974: switched to wellspring mode.
[  811.449004] bcm5974: switched to normal mode.
[  811.474579] bcm5974: switched to wellspring mode.
[  811.488582] bcm5974: switched to normal mode.
[  811.522576] bcm5974: switched to wellspring mode.
[  811.536568] bcm5974: switched to normal mode.
[  811.563772] bcm5974: switched to wellspring mode.

---

### Post by kosumi68 on 2008-11-12
From the logs, and from your statements, the trackpad has not even been involved in the tests. It seems there is nothing wrong here, except for the hardware problem.

---

### Post by ichekryg on 2008-11-12
Not sure if this helps or not, but here is another observation:
Steps:
 1. boot up
 2. log on
 3. tail -f /var/log/messages
 4. don't do anything at all (no typing, scrolling, etc)
Result:
 Issue occurs on its own (ot-of-the-blue).
dmesg: 
Nov 12 14:54:28 mpb kernel: [  871.872340] usb 6-2: USB disconnect, address 24
Nov 12 14:54:28 mpb kernel: [  872.264133] usb 6-2: new full speed USB device using uhci_hcd and address 25
Nov 12 14:54:28 mpb kernel: [  872.452113] usb 6-2: configuration #1 chosen from 1 choice
Nov 12 14:54:28 mpb kernel: [  872.472953] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input56
Nov 12 14:54:28 mpb kernel: [  872.517071] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:28 mpb kernel: [  872.562230] usbhid: ctrl urb status -75 received
Nov 12 14:54:28 mpb kernel: [  872.562443] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:28 mpb kernel: [  872.564533] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input57
Nov 12 14:54:28 mpb kernel: [  872.620351] usb 6-2: USB disconnect, address 25
Nov 12 14:54:29 mpb kernel: [  873.029082] usb 6-2: new full speed USB device using uhci_hcd and address 26
Nov 12 14:54:29 mpb kernel: [  873.226966] usb 6-2: configuration #1 chosen from 1 choice
Nov 12 14:54:29 mpb kernel: [  873.241399] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input58
Nov 12 14:54:29 mpb kernel: [  873.284356] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:29 mpb kernel: [  873.370211] usbhid: ctrl urb status -75 received
Nov 12 14:54:29 mpb kernel: [  873.370354] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:29 mpb kernel: [  873.375055] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input59
Nov 12 14:54:29 mpb kernel: [  873.608203] usb 6-2: USB disconnect, address 26
Nov 12 14:54:30 mpb kernel: [  873.972422] usb 6-2: new full speed USB device using uhci_hcd and address 27
Nov 12 14:54:30 mpb kernel: [  874.160422] usb 6-2: configuration #1 chosen from 1 choice
Nov 12 14:54:30 mpb kernel: [  874.168939] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input60
Nov 12 14:54:30 mpb kernel: [  874.213203] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:31 mpb kernel: [  874.676450] hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2
Nov 12 14:54:31 mpb kernel: [  874.678631] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.2/input/input61

---

### Post by kosumi68 on 2008-11-12
Yep, that is how the hardware problem establishes itself. Getting the machine in for repairs might be your best option.

---

### Post by bristoljim on 2008-11-20
Hi, I'm trying to find the sources for bcm5974-dkms but am having no joy.

Have tried bzr branch lp:~rydberg/+junk/bcm5974-dkms  but it's saying its not a branch.

I'm running Debian Lenny (2.6.26 + mactel patches), not Ubuntu, but [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) directs me here as the forum thread for bcm5974-dkms.

# uname -a
Linux baleal 2.6.26-mactel #1 SMP PREEMPT Wed Nov 19 11:55:51 GMT 2008 x86_64 GNU/Linux

My aim is to get (at least) two finger scroll working on my MacBook Pro 4,1 Penryn. Any help much appreciated.

---

### Post by _mario_ on 2008-11-20
> **bristoljim said:**
> Hi, I'm trying to find the sources for bcm5974-dkms but am having no joy.
...
My aim is to get (at least) two finger scroll working on my MacBook Pro 4,1 Penryn. Any help much appreciated.

this package, as well as its sources, are available in the mactel repository: [http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/b/bcm5974-dkms/]("http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/b/bcm5974-dkms/").

good luck & ciao,
Mario

---

### Post by kosumi68 on 2008-11-29
> **bristoljim said:**
> Hi, I'm trying to find the sources for bcm5974-dkms but am having no joy.


The GIT repository for bcm5974-dkms has been moved to a more permanent address at [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/)

---

### Post by Botto on 2008-11-30
Hi, when trying to install the latest version of your driver I get the following error.
E: usbhid-dkms: subprocess post-installation script returned error exit status 2

I'm running x86_64 but when running in a 32 bit edition usbhid installs just fine. Seems to be some issue with 64bit ubuntu.

Any help? Thank you

---

### Post by bristoljim on 2008-12-02
> **_mario_ said:**
> this package, as well as its sources, are available in the mactel repository: [http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/b/bcm5974-dkms/]("http://ppa.launchpad.net/mactel-support/ubuntu/pool/main/b/bcm5974-dkms/").

good luck & ciao,
Mario

Thanks Mario. Luck I need :)

---

### Post by bristoljim on 2008-12-02
> **kosumi68 said:**
> The GIT repository for bcm5974-dkms has been moved to a more permanent address at [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/)

Thanks kosumi68

---

### Post by cornelius2 on 2009-04-06
I posted a patch (+ deb package) for bcm5974-dkms to make click-and-drag work with Macbook 5,1:
**EDIT (improved version):** [https://bugs.edge.launchpad.net/mactel-support/+bug/356317](https://bugs.edge.launchpad.net/mactel-support/+bug/356317)

Please test it and let me know where to submit the patch for consideration for upstream inclusion.

Thanks.

---

### Post by ichekryg on 2009-06-23
> **kosumi68 said:**
> Yep, that is how the hardware problem establishes itself. Getting the machine in for repairs might be your best option.

Just checking in if there are any changes since my last post in regards to the alternatives to bcm5974.

Thanks for the suggestion to get my machine to repair, however, since this issue does not manifest it self in OsX at all, there is nothing wrong trom the MBP-OsX perspective.

The way i see it, bcm5974 driver keeps unloading and loading, creating unresponsiveness in the keyboard. Since bcm5974 should be dedicated exclusively to the management of the trackpad, why would it cause interrupt in the keyboard functionality?

---

### Post by vanRijn on 2010-02-05
Just to reply to cornelius2's message, I'm using a MacbookPro 5,5 and I need click and drag to work. I'm currently using [http://launchpadlibrarian.net/24871974/bcm5974-dkms_1.1.4_all_test.deb](http://launchpadlibrarian.net/24871974/bcm5974-dkms_1.1.4_all_test.deb) and it works great. Anyone know what the status is on getting click+drag working on the newer touchpads?

---

### Post by kosumi68 on 2010-02-05
Check out the Multitouch X Driver project at [http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696).

---

### Post by Maletor on 2010-06-06
I love this project. I really hope we can get tap to click working. It's a tad bit buggy but much better than not being able to use the trackpad. This makes Ubuntu on Mac completely transparent.

It's worth noting that none of this works without the mactel ppa and bcm5974. That should probably be noted in the first post as I followed the instructions and my trackpad stopped working.

Thanks for this driver. Maybe it can be integrated into lucid so we don't have to install this by hand or dig through Google to find this post.

Instead of doing make install I would recommend checkinstall as that's what the ubuntu wiki recommends.

---

### Post by muryoh on 2010-06-22
Hello ):P
I'm using the new 6.2 Macbook Pro.
For some reason, my trackpad won't work on Gentoo, and I can't figure why. I tried Ubuntu 10.04, and it does work without any tweaking. I don't know why! I do know that when the usbhid module isn't loaded, the trackpad works fine.

I'm not up to date with usbhid or udev, but it does sound like a quirk issue. Could anybody provide me with the tweaks performed on previous releases of Ubuntu to get the trackpad to work fine with usbhid?

Thanks. :p

---

### Post by kosumi68 on 2010-06-24
> **muryoh said:**
> Hello ):P
I'm using the new 6.2 Macbook Pro.
For some reason, my trackpad won't work on Gentoo, and I can't figure why. I tried Ubuntu 10.04, and it does work without any tweaking. I don't know why! I do know that when the usbhid module isn't loaded, the trackpad works fine.

I'm not up to date with usbhid or udev, but it does sound like a quirk issue. Could anybody provide me with the tweaks performed on previous releases of Ubuntu to get the trackpad to work fine with usbhid?

Thanks. :p

Hi, do you use a ramdisk when booting up?

---

### Post by raumkundschafter on 2010-07-02
i'm havin problems with the trackpad and keyboard on a penryn macbook - due to my dmesg it's propably an issue with the bcm5974 driver...

dmesg output:
...
[176267.592140] apple 0003:05AC:0231.1A2F: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
[176267.594143] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input6710
[176267.660056] bcm5974: bcm5974: could not read from device
[176267.660060] bcm5974: mode switch failed
[176267.669053] bcm5974: bcm5974: could not read from device
[176267.669055] bcm5974: mode switch failed
[176267.750533] hub 7-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[176267.750538] usb 7-2: USB disconnect, address 96
[176267.998294] usb 7-2: new full speed USB device using uhci_hcd and address 97
[176268.229152] usb 7-2: configuration #1 chosen from 1 choice
[176268.242485] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6711
[176268.242554] apple 0003:05AC:0231.1A30: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[176268.259067] usb 7-2: ctrl urb status -75 received

this is on ubuntu karmic - any hints how to hunt this bug are welcome!

just filled the following bug report: 
[https://bugs.launchpad.net/ubuntu/+bug/601132](https://bugs.launchpad.net/ubuntu/+bug/601132)

---

### Post by kosumi68 on 2010-07-02
> **raumkundschafter said:**
> i'm havin problems with the trackpad and keyboard on a penryn macbook - due to my dmesg it's propably an issue with the bcm5974 driver...

dmesg output:
...
[176267.592140] apple 0003:05AC:0231.1A2F: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
[176267.594143] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input6710
[176267.660056] bcm5974: bcm5974: could not read from device
[176267.660060] bcm5974: mode switch failed
[176267.669053] bcm5974: bcm5974: could not read from device
[176267.669055] bcm5974: mode switch failed
[176267.750533] hub 7-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[176267.750538] usb 7-2: USB disconnect, address 96
[176267.998294] usb 7-2: new full speed USB device using uhci_hcd and address 97
[176268.229152] usb 7-2: configuration #1 chosen from 1 choice
[176268.242485] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6711
[176268.242554] apple 0003:05AC:0231.1A30: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[176268.259067] usb 7-2: ctrl urb status -75 received

this is on ubuntu karmic - any hints how to hunt this bug are welcome!

just filled the following bug report: 
[https://bugs.launchpad.net/ubuntu/+bug/601132](https://bugs.launchpad.net/ubuntu/+bug/601132)

Hi, thanks for the report. I am sorry, but this sounds like a known hardware (usb) problem. You will find references by searching for "ubuntu macbook disabled by hub (EMI?)".

---

### Post by muryoh on 2010-07-08
> **kosumi68 said:**
> Hi, do you use a ramdisk when booting up?

I apologize for the long delay, I'm the one asking yet I'm the one forgetting about the post... :(
No, I'm not using a ramdisk.

---

### Post by muryoh on 2010-07-19
ok, got it. Sneaky kernel options did the trick : [https://bugzilla.kernel.org/show_bug.cgi?id=14987](https://bugzilla.kernel.org/show_bug.cgi?id=14987)

Thanks :-)

---

### Post by JonasPetersson on 2011-06-06
Has anyone else started to have problems with this driver recently? Overall it has worked wonders and on the odd occasion it would stop working I'd just toggle to text console rmmod+modprobe and a few seconds after switching back everything was fine again. Yesterday this no longer helped so I tried restarting X - still broken. Note that seemingly any variant of clicking (right left depending on number of fingers - but I've intentionally disabled tapping) still worked, just moving failed. In the end I rebooted and it was fine.

This morning it was the same again (I'm currently using a USB mouse).

Any and all suggestions are welcome. This is on a MacBookPro6,1 upgraded to Natty about a month ago. I've run Ubuntu on it ever since I got it (within a month or so of its release) and the module has never misbehaved before.

Best / Jonas

[Hmm, Seems like a "Heisenbug": I tried adding some debugging to the module and suddenly it worked again! Very annoying. ]

---

### Post by JonasPetersson on 2011-06-15
For the record, it just happened again and this time it stayed broken after i modprobed with debug=8. The situation is identical in that clicking appears to work, but movement hardly ever does anything. The debug flag yields some lines like these in dmesg:
[836847.062151] bcm5974: switched to wellspring mode.
[836847.077168] bcm5974: abs: p: +0255 w: +0015 x: +0402 y: +0396 nmin: 1 nmax: 1 n: 1 ibt: 0
[836847.117028] bcm5974: abs: p: +0255 w: +0015 x: +0402 y: +0396 nmin: 1 nmax: 1 n: 1 ibt: 0
[836850.392018] bcm5974: abs: p: +0255 w: +0015 x: +0978 y: +0159 nmin: 3 nmax: 3 n: 3 ibt: 0
[836850.403021] bcm5974: abs: p: +0255 w: +0015 x: +0981 y: +0158 nmin: 3 nmax: 3 n: 3 ibt: 0

That seems to indicate that report_tp_state() is called with fingers pressed (makes sense considering what I see) and that bcm5974_wellspring_mode() is called with on==true - whether that makes sense is somewhat beyond obvious to me at the moment...

Any and all hints are welcome.

---

### Post by kcleong on 2011-06-21
The synclient command does not work on my Macbook Pro 7,1 using Ubuntu 11.04. When I'm typing on the keyboard the touchpad responds to clicks/movement. I believe I can use syndaemon to disable the touchpad while typing.

```
$ synclient -m 500
Can't access shared memory area. SHMConfig disabled?
Couldn't find synaptics properties. No synaptics driver loaded?

```

The bcm5974 diag script:
```
$ /usr/src/bcm5974-1.1.9/scripts/bcm5974-diagnostics
-----------------------------------------------------------------------
* Kernel version: 2.6.38-8-generic
* Synaptics version: 1.3.99+git20110116.0e27ce3a-0ubuntu12.1
* USB device: Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
* /lib/modules/2.6.38-8-generic/kernel/drivers/input/mouse/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: file not found
* /etc/modprobe.d/bcm5974: no such file, good
* /lib/modules/2.6.38-8-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
Couldn't find synaptics properties. No synaptics driver loaded?

```

Can anyone point me in a direction to get the synclient working?

---

### Post by philcolbourn on 2011-06-22
> **JonasPetersson said:**
> Has anyone else started to have problems with this driver recently? Overall it has worked wonders and on the odd occasion it would stop working I'd just toggle to text console rmmod+modprobe and a few seconds after switching back everything was fine again. Yesterday this no longer helped so I tried restarting X - still broken. Note that seemingly any variant of clicking (right left depending on number of fingers - but I've intentionally disabled tapping) still worked, just moving failed. In the end I rebooted and it was fine.

This morning it was the same again (I'm currently using a USB mouse).

Any and all suggestions are welcome. This is on a MacBookPro6,1 upgraded to Natty about a month ago. I've run Ubuntu on it ever since I got it (within a month or so of its release) and the module has never misbehaved before.

Best / Jonas

[Hmm, Seems like a "Heisenbug": I tried adding some debugging to the module and suddenly it worked again! Very annoying. ]

Similar story for me.

MacBook Pro 4,1 Natty 11.04

I'd say it started a month ago and just got worse over time.
I have found out this: 

Apple keyboard and touchpad share a USB port or something like that. Hence we need a mode switch - so I gather.

With touchpad bcm5974 removed, apple keyboard works fine.

With apple keyboard hid_apple removed, touchpad works fine.

With both loaded, both eventually become unusable and my USB hub seems to 
reset all the time and xorg loads and unload it's drivers making my situation unworkable.

I too am using a USB mouse.

This morning I thought it might be hardware since with a cold laptop, my machine was usable but as it warmed it got worse and eventually became unusable.

But, on OS-X all is well. So must be a driver issue - perhaps hid_apple?

How can I help?

2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

modinfo hid_apple
filename:       /lib/modules/2.6.38-8-generic/updates/dkms/hid-apple.ko

modinfo bcm5974 
filename:       /lib/modules/2.6.38-8-generic/updates/dkms/bcm5974.ko

Jun 22 09:16:41 max kernel: [ 1682.040256] usb 7-2: new full speed USB device using uhci_hcd and address 42

Jun 22 09:16:41 max kernel: [ 1682.270631] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input88

Jun 22 09:16:41 max kernel: [ 1682.270931] apple 0003:05AC:0230.0052: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0

Jun 22 09:16:41 max kernel: [ 1682.284471] usb 7-2: ctrl urb status -75 received

Jun 22 09:16:41 max kernel: [ 1682.284678] apple 0003:05AC:0230.0053: hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1

Jun 22 09:16:41 max kernel: [ 1682.286701] input: bcm5974 as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input89

Jun 22 09:16:41 max kernel: [ 1682.290311] hub 7-0:1.0: port 2 disabled by hub (EMI?), re-enabling...

Jun 22 09:16:41 max kernel: [ 1682.290323] usb 7-2: USB disconnect, address 42

Jun 22 09:16:42 max kernel: [ 1682.820394] usb 7-2: new full speed USB device using uhci_hcd and address 43

ad nausea

[ 27965.540] (EE) xf86OpenSerial: Cannot open device /dev/input/event9
        Input/output error.
[ 27965.540] (EE) Synaptics driver unable to open device
[ 27965.540] (EE) PreInit returned 11 for "bcm5974"
[ 27965.540] (II) UnloadModule: "synaptics"
[ 27965.540] (II) Unloading synaptics
[ 27965.580] (II) config/udev: removing device Apple, Inc. Apple Internal Keyboard / Tra
ckpad
[ 27965.580] (II) Apple, Inc. Apple Internal Keyboard / Trackpad: Close
[ 27965.580] (II) UnloadModule: "evdev"
[ 27965.580] (II) Unloading evdev
[ 27966.254] (II) config/udev: Adding input device Apple, Inc. Apple Internal Keyboard / Trackpad (/dev/input/event8)
[ 27966.254] (**) Apple, Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[ 27966.254] (II) Using input driver 'evdev' for 'Apple, Inc. Apple Internal Keyboard / Trackpad'
[ 27966.254] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 27966.254] (**) Apple, Inc. Apple Internal Keyboard / Trackpad: always reports core events
[ 27966.254] (**) Apple, Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event8"
[ 27966.280] (--) Apple, Inc. Apple Internal Keyboard / Trackpad: Found keys
[ 27966.280] (II) Apple, Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[ 27966.280] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input1133/event8"
[ 27966.280] (II) XINPUT: Adding extended input device "Apple, Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
[ 27966.280] (**) Option "xkb_rules" "evdev"
[ 27966.280] (**) Option "xkb_model" "macbook79"
[ 27966.280] (**) Option "xkb_layout" "us"
[ 27966.280] (**) Option "xkb_options" "lv3:ralt_switch"
[ 27966.357] (II) config/udev: Adding input device bcm5974 (/dev/input/event9)
[ 27966.357] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[ 27966.357] (**) bcm5974: Applying InputClass "touchpad catchall"
[ 27966.357] (II) Using input driver 'synaptics' for 'bcm5974'
[ 27966.357] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 27966.357] (**) bcm5974: always reports core events
[ 27966.357] (**) Option "Device" "/dev/input/event9"
[ 27966.450] (EE) xf86OpenSerial: Cannot open device /dev/input/event9
        Input/output error.

and it repeats every time.

Here is my script to test removing apple keyboard module to test my touchpad driver:

#!/bin/bash
T=60

logger "removing apple keyboard for $T seconds and installing touchpad..."
rmmod hid_apple
modprobe bcm5974
sleep $T
logger "installing apple keyboard and disabling touchpad"
modprobe hid_apple
rmmod bcm5974

---

### Post by philcolbourn on 2011-06-22
Something simple to try: remove lirc and associated libs.

Why?

My MacBook Pro 4,1 USB hub has keyboard, touchpad and IR device on it. 

Maybe lirc is messing up other devices on this bus?

It seems to have worked for me, but it is still early minutes.

---

### Post by JonasPetersson on 2011-07-15
> **philcolbourn said:**
> Something simple to try: remove lirc and associated libs.

Why?

My MacBook Pro 4,1 USB hub has keyboard, touchpad and IR device on it. 

Maybe lirc is messing up other devices on this bus?

It seems to have worked for me, but it is still early minutes.

Hi Phil, (/me just back from holidays)

Good plan as such and I'm happy that it seems to work for you, but I don't even have lirc installed so it can hardly be the issue in my case. So far it has not showed up again (that is, it has only manifested twice) which makes identifying the cause tricky...

---

### Post by philcolbourn on 2011-07-15
> **JonasPetersson said:**
> Hi Phil, (/me just back from holidays)

Good plan as such and I'm happy that it seems to work for you, but I don't even have lirc installed so it can hardly be the issue in my case. So far it has not showed up again (that is, it has only manifested twice) which makes identifying the cause tricky...

It was early minutes...

What I know: you need to have pm remove and re-install the bcm5974 module before and after sleep.

Add a file to /etc/pm/config.d that contains this:
SUSPEND_MODULES="bcm5974"

And... don't sleep with LibreOffice/OpenOffice running.

That's it. Something is badly wrong with LibreOffice/Nvidia/trackpad that causes LibreOffice to run slow when refreshing, the bcm5974 module can die and it seems to happen to those with Nvidia module installed.

I can go a whole day without the problem with LibreOffice running, and other days I have to kill LibreOffice and rmmod/modprobe bcm5974 if I forget and leave it running.

---

### Post by cmatts on 2011-07-15
[unbuntu noob]hi, i am trying to install ubuntu v11 narwale on my macbook air 3,2
i made it through about 5 pages of this thread. 

my tractpad is almost unusable. keep acting like i did a mouse click and doing unpredictable things generally.

 did the driver update on the first page. then started reading all the code tweaks to get it to work (?).

so is there a simple - install this drive solution? or do i need to finish reading the 15pages of trial and error?

thanks.
 [/unbuntu noob]

edit: just read this thread. 
[http://ubuntuforums.org/showthread.php?t=1799460](http://ubuntuforums.org/showthread.php?t=1799460)
might just move on and look into a pc laptop or just go back to my old macbook pro that has unbuntu running (seemingly fine)

---

### Post by dfacto on 2011-07-27
Hey all--trying to get this driver working on the new MacBookAir4,2.

I [posted at xf86-input-mtrack: The Other Multitouch Trackpad Driver]("http://ubuntuforums.org/showthread.php?p=11093861#post11093861") but now I'm wondering if I should have asked here.

dmesg doesn't give any indication of a problem but synclient -l says no driver loaded.  I am having trouble trying to isolate who "owns" this problem--this kernel driver or the xorg driver.

Any tips/advice is appreciated.

Thanks!


**Update:** I made some minor modifications to bcm5974.c to add support for the MacBookAir4,2.  The patch is available [here]("http://www.almostsure.com/mba42/bcm5974-dkms.patch"); the deb and [all other files]("http://www.almostsure.com/mba42/working/") are available as well.

I had some problems getting the driver to load (blacklisting usbhid didn't work) so I ended up using /etc/rc.local as a workaround.  Suggestions welcome.  (More details can be found in the  [MacBookAir4,1/2 thread]("http://ubuntuforums.org/showpost.php?p=11106203&postcount=59").)

---

### Post by cnuernber on 2012-04-28
To solve:

bcm5974: could not read from device

edit /etc/default/grub
and change:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nopnp=1"


This will also make your touchpad settings persistent.

---

### Post by bravegag on 2012-04-29
Hello,

I tried several suggestions like the one on the first page and doesn't work in Ubuntu 12.04. The system update fails and the later installation fails as well.

I have a MBP 5,2 and the touchpad works very badly. For all those desperate just plug any decent mouse and move on. I plugged in the Apple Mighty Mouse and works like a charm with right-click and everything. I also tried Logitech mouses and they work tip top too. 

My advice ... "don't get too attached to things" :) be pragmatic and use a viable solution instead.

HTH,
Giovanni

---

