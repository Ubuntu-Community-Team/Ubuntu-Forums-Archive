---
title: "Mouse Frozen at Login (Hardy Heron)"
date: 2008-07-04
forum: Apple Hardware Users
---

### Post by Gamma6 on 2008-07-04
After having trouble before on my mac with Gutsy (with no right click and no sound) I decided to try my new Ubuntu Hardy Heron CD that had only recently arrived in the mail.
I installed into a 6GB partition (including swap) and didn't use it for sometime. It was only the other day I decided I wanted to get rid of my XP partition and use Linux when at home (Mac OS 10.5 for school) I was playing around with my mouse settings, and took off touch-pad click by accident. The mouse then froze, wouldn't move at all when logged in. I reinstalled gutsy, then had another crack at hardy. The installation and went smooth, but upon logging in the mouse froze again. The whole OS runs fine, but the mouse just doesn't move or click. No idea whats happening, I feel helpless.:mad:

> Model Name:	MacBook
  Model Identifier:	MacBook3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	4 MB
  Memory:	1 GB
  Bus Speed:	800 MHz

Using 6GB for Ubuntu. 8.04 Hardy Heron Desktop Editing (64 Bit)
  

---

### Post by dustynus on 2008-07-06
once logged in, try alt-f2 to run a command then
 
```

sudo modprobe -r appletouch
sudo modprobe appletouch

``` 

that'll reload the trackpad drivers, should work.

---

### Post by excrabot on 2008-07-07
Hey guys,

i have the same trouble, no response from the track pad at all. i'm running the same macbook as the original poster.

the terminal command in the previous post works a treat.. but does anyone know how to make this command run on startup?

---

### Post by kosumi68 on 2008-07-07
After reboot, with the mouse frozen, what is the output of these commands:

```

lsusb | grep 05ac
grep appletouch /lib/modules/`uname -r`/modules.usbmap
dmesg | grep appletouch:

```

---

### Post by excrabot on 2008-07-07
here you go..

$ lsusb | grep 05ac

Bus 005 Device 004: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc. 
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 001 Device 004: ID 05ac:021a Apple Computer, Inc.
 
$ grep appletouch /lib/modules/'uname -r'/modules.usbmap

grep: /lib/modules/uname -r/modules.usbmap: No such file or directory

$ dmesg | grep appletouch:

[   31.898897] appletouch: Geyser mode initialized.
[   41.918570] appletouch: incomplete data package (first byte: 2, length: 4).

thats straight after a reboot with a frozen trackpad.

---

### Post by kosumi68 on 2008-07-07
Another thing to try:

```

grep quirks /etc/modprobe.d/*

```

If there are quirk lines here, they will override the kernel settings. Thus if present and wrong...

---

### Post by excrabot on 2008-07-07
that entry didn't produce any output.

i'm guessing that's a good thing..

---

### Post by kosumi68 on 2008-07-07
Indeed, that is a good thing. The line for checking the usbmapping should contain `uname -r`, those are backward apostrophes.

You have a geyser4 touchpad, and it seems to initialize as it should.

What is the output of this command:

```

grep -B2 -A8 appletouch /proc/bus/input/devices

```

Do you see anything on the screen when running this command (replace X by the number matching the event device on the H: line of the output of the previous command):

```

sudo cat /dev/input/eventX

```

And turning attention to the synaptics driver, what is the output of

```

grep -i synaptics /var/log/Xorg.0.log

```

---

### Post by excrabot on 2008-07-07
$ grep -B2 -A8 appletouch /proc/bus/input/devices

I: Bus=0003 Vendor=05ac Product=021a Version=0016
N: Name="appletouch"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=1000003

$ sudo cat /dev/input/event7

There wasn't any output after the above command, or for..

grep -i synaptics /var/log/Xorg.0.log

is that normal?

---

### Post by kosumi68 on 2008-07-07
No :)

There is information buried in the command that didnt get properly executed in the first post. Please retry that one.

If your configuration changed recently, it could also be a good idea to try running "sudo depmod -a", which will rebuild the module dependencies.

---

### Post by kosumi68 on 2008-07-07
Ok, synaptics testing:

```

synclient -l

```

If this command complains, the synaptics driver is not loaded, which seems to be the case. Then the focus of attention is the /etc/X11/xorg.conf file.

---

### Post by excrabot on 2008-07-07
sudo cat /dev/input/event7    jst outputs all sorts of random alphanumerics and spaces very  slowly.

synclent -l gave me this though..

$ synclient -l
Parameter settings:
    LeftEdge                = 100
    RightEdge               = 1120
    TopEdge                 = 50
    BottomEdge              = 310
    FingerLow               = 10
    FingerHigh              = 20
    FingerPress             = 256
    MaxTapTime              = 150
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 257
    VertScrollDelta         = 30
    HorizScrollDelta        = 24
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.7
    MaxSpeed                = 0.88
    AccelFactor             = 0.015
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 38
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
    RTCornerButton          = 3
    RBCornerButton          = 3
    LTCornerButton          = 2
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 2
    TapButton3              = 3
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 0
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1

how does that sound.

---

### Post by kosumi68 on 2008-07-07
The output from /dev/input/event7 should be correlated to touching the trackpad. If you got output right after a reboot, it means your appletouch is fully operational at boot time.

The fact that synclient -l responded with output also means that synaptics is up and running, which makes the problem even more puzzling. In particular when not getting any output from the "grep -i synaptics /var/log/Xorg.0.log" command... unless you issued this command in text mode somehow?

I am currently out of ideas :)

---

### Post by excrabot on 2008-07-07
now that i know that the output of "sudo cat /dev/input/event7" should show trackpad input.. i'm pretty sure it was only showing keyboard input. 

that command isn't responding to trackpad but is spouting out random text as i type  on the keyboard.

---

### Post by kosumi68 on 2008-07-07
Good, then the current conjecture is this:

* The touchpad is detected, the right driver is loaded, it *claims* to be correctly initialized, it gets registered as it should, but there is no trackpad info to be read from the appletouch device.

* This in turn makes synaptics initialize as it should, it finds the correct device, sets it up... and waits for input that doesnt arrive.

* Reinitializing the appletouch somehow wakes it up, messages start to find their way to the synaptics driver, business as usual.

In other words, the problem does seem to lie with the appletouch driver. Could you provide the output of this command, please:

```

sudo lsusb -v -d 05ac:021a

```

what I am fishing for is the number of interfaces and their corresponding types and usb endpoints, it could help understanding what logic is executed in the appletouch driver.

---

### Post by kosumi68 on 2008-07-07
another thing: the synaptics driver tries to grab the trackpad for exclusive use, that could be another reason for not seeing any trackpad events. Try adding this line to the synaptics section of your /etc/X11/xorg.conf:

```

        Option		"GrabEventDevice"	"0"

```

---

### Post by excrabot on 2008-07-07
Here's the output for 'sudo lsusb -v -d 05ac:021a"

Bus 001 Device 004: ID 05ac:021a Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x021a 
  bcdDevice            0.16
  iManufacturer           1 Apple Computer
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
          wDescriptorLength      73
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
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
          wDescriptorLength      89
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
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              3 Apple Internal Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      20
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

---

### Post by excrabot on 2008-07-07
Thankyou Kosumi68,

adding 

 Option		"GrabEventDevice"	"0"

did the trick, i have trackpad functioning at startup again.

I apreciate your time on this one.

---

### Post by kosumi68 on 2008-07-07
Ah, great! In case you do experience further problems in the future, there are more things to test :)

Cheers!

(note to self: is the geyser4 sending packets when idle? if no, appletouch might need a patch)

---

