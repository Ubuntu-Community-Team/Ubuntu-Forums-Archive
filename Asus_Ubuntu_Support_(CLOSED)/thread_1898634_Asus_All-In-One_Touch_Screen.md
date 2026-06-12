---
title: "Asus All-In-One Touch Screen?"
date: 2011-12-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cbanakis on 2011-12-21
I just got an Asus All-in-one-PC (ET2410IUTS-B019C)
(Running Ubuntu 11.04)

It has a multi-touch screen.

Anyone got one of these working?

As far as I can tell, Ubuntu supports touch screens, but maybe this one is too new?

I have no idea where to begin.

Thanks

---

### Post by cbanakis on 2011-12-21
I think i found the correct driver at [http://www.conan.de/touchscreen/evtouch.html#download](http://www.conan.de/touchscreen/evtouch.html#download)

But I'm having trouble with the install.

Instructions say to add info to either
"/etc/X11/XF86Config-4" or "/etc/X11/xorg.conf"

It does not look like I have either of those files in my /etc/x11/ directory.

Should I create a file?

If so, which one?

Is there a command I can use to simply convert the driver into a deb?

I'm not completely incapable, but this driver install seems a little  more advanced than what I am used to, and I really don't want to screw  anything up.

---

### Post by cbanakis on 2011-12-27
*Bump

---

### Post by bpb101 on 2011-12-28
i think there something called ktouch 
i wanted to install it with a multi touch pc , but i never got it working , however i was using wubi
look for k touch i think it in the software center

---

### Post by cbanakis on 2011-12-28
Unless I am totally mistaken, ktouch appears to be an app for teaching people how to type.
It does not appear to have anything to do with touch screens.  :(

Thanks for the thought though.

---

### Post by bpb101 on 2011-12-29
sorry it actual Utouch 
[http://techie-buzz.com/foss/ubuntu-10-10-will-support-multi-touch.html](http://techie-buzz.com/foss/ubuntu-10-10-will-support-multi-touch.html)

i forgot the name , everything in Ubuntu is it function with a K in front of it eg ktorrent and kteatime and Kthesaurus  and the list goes on :D

---

### Post by cbanakis on 2011-12-30
Yeah, I guess a bunch of stuff does start with K.

What are the odds that there actually was a program called ktouch?

LOL

Anyways, still no luck.

I installed utouch, and it does not seem to do anything.

I tried all the instructions found at [http://www.conan.de/touchscreen/evtouch.html#download](http://www.conan.de/touchscreen/evtouch.html#download)

And just ended up breaking my computer.  (Had to boot to cli in order to fix everything)

This is frustrating.

There has to be someone that knows what the heck needs to be done to get this screen working.

I really do not want to throw my nice new computer out the window, but eventually, I'm sure to snap.  :)

---

### Post by bpb101 on 2011-12-30
funny enough i think it crashed on me when i was messing with it too , however i was using wubi so it was easy just to unistall

interesting
i know  there is touch screen support iand hat as their are tablets running ubuntu , 
i say your best beet is too drop the utouch guys an email , i say they would be quite helpful

but to be honest , you probable wont use the touch screen as much as you think. I never use mine ,it just so pointless tbh   and is just a gimmick in my option

---

### Post by cbanakis on 2012-01-01
I agree that I will probably never really use the touch screen.

But its the principle.

I'm supposed to be able to touch it, and so I wanna.  :)

Plus, I managed to get absolutely everything else (Hardware/Software) working perfectly.

So all thats preventing my box from attaining perfection, is the touch screen.

---

### Post by bpb101 on 2012-01-01
i know , what you mean
i say just goooooogle all days is the best things to do

---

### Post by cbanakis on 2012-01-03
Well, I installed "device manager" from the software center, and it looks like Ubuntu is detecting the touchscreen, but I cant figure our how to manage/activate it.

---

### Post by cbanakis on 2012-01-03
I also installed xinput-calibrator (which I guess is needed with utouch?)

But when I run Calibrate Touchscreen, it returns Error: "No calibratable devices found."

I'm pretty positive, all I need to do is somehow install this driver...
[http://www.conan.de/touchscreen/evtouch.html#download](http://www.conan.de/touchscreen/evtouch.html#download)

But if I follow the instructions, it seems to brake my computer.
I assume I am doing something wrong, but I have no idea what.

---

### Post by cbanakis on 2012-01-05
*Bump

---

### Post by bpb101 on 2012-01-09
nothing in additional drivers?

---

### Post by cbanakis on 2012-01-10
Only my Ethernet card.  :(

> **bpb101 said:**
> nothing in additional drivers?

---

### Post by cbanakis on 2012-01-13
*Bump

---

### Post by cbanakis on 2012-01-20
*Bump

---

### Post by cbanakis on 2012-01-23
Well, I tried installing egalax-multitouch-driver-common

Still nothing.

not sure if its just the wrong driver, or if there is more involved than simply installing the driver.

But one thing is for sure.

I cannot for the life of me figure out how to install the evtouch driver.

Any ideas or experiences will be greatly appreciated.

Now that Ubuntu-TV is on the horizon, I really want to get this working.

This computer with Ubuntu-TV, and an operational touch screen would make a great addition to my kitchen.  :)

---

### Post by cbanakis on 2012-01-23
Not sure if this helps at all, but here is my output from lsusb

```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 174f:1447 Syntek 
Bus 002 Device 003: ID 1926:0dbf NextWindow 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 001 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Device 003 "Next Window" is definitely my touch screen.

So it is detected, but I cant get any results out of it.

Tried sudo evtest /dev/input/event"0-10" and there are no events associated with "Next Window"

Seems like there is probably just 1 simple thing I'm missing, but I really have no idea.

---

### Post by cbanakis on 2012-01-26
*Bump

---

### Post by Favux on 2012-01-26
Run:
```
dmesg | grep NextWindow
```
in a terminal and see if if there is a (presumably hid) kernel driver installed for the touchscreen.  If there is the evdev driver should probably be the X driver running it.  Although I'd feel more confident of that if you were in Oneiric.

---

### Post by cbanakis on 2012-01-26
Thanks for the reply.

dmesg | grep NextWindow gave me this...
```

[   14.953662] generic-usb 0003:1926:0DBF.0001: hiddev0,hidraw0: USB HID v1.11 Device [NextWindow Touchscreen] on usb-0000:00:1d.0-1.3/input1
```

I know Oneiric is newer, but I say "No Thanks" to Unity.

I did have Oneiric on here for a while, in hopes that I could get the touch working in there, but the results seemed the same, so I bounced back to natty.

> **Favux said:**
> Run:
```
dmesg | grep NextWindow
```in a terminal and see if if there is a (presumably hid) kernel driver installed for the touchscreen.  If there is the evdev driver should probably be the X driver running it.  Although I'd feel more confident of that if you were in Oneiric.

---

### Post by Favux on 2012-01-26
Alright it is in the kernel.  To see what the kernel is reporting go ahead and install evtest if not already installed.  Then to get a clue what event the touchscreen is on run:
```
ls -l /dev/input/by-path
```
and compare the usb description to the one from dmesg.  Then with the event # run in a console (so X isn't running and doesn't hide things):
```
sudo evtest /dev/input/eventX > evtest_log.txt
```
The NextWindow site claims the HP Touchsmart all-in-ones use it to, so there might be help looking at any threads on those.

Also what do you see with?:
```
xinput list
```

---

### Post by cbanakis on 2012-01-27
[FONT=monospace]OK...

ls -l /dev/input/by-path
[/FONT]```
total 0
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 pci-0000:00:1a.0-usb-0:1.2.2:1.0-event-kbd -> ../event4
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 pci-0000:00:1a.0-usb-0:1.2.2:1.1-event -> ../event5
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 pci-0000:00:1a.0-usb-0:1.2.3:1.0-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 pci-0000:00:1a.0-usb-0:1.2.3:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 pci-0000:00:1d.0-usb-0:1.4:1.0-event -> ../event3
lrwxrwxrwx 1 root root 9 2012-01-25 16:52 platform-i8042-serio-0-event-kbd -> ../event2
```[FONT=monospace]

Unless I am misunderstanding this, I dont think I can run sudo evtest /dev/input/eventX > evtest_log.txt
Until after I know what x is.


xinput list
[/FONT]```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Mitsumi Electric Apple Optical USB Mouse    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard                   id=8    [slave  keyboard (3)]
    &#8627; Apple, Inc Apple Keyboard                   id=9    [slave  keyboard (3)]
    &#8627; USB2.0 Camera                               id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard     

```[FONT=monospace]
It does not look like there is an event for the touchscreen.

Thanks again for your help.


[/FONT]

---

### Post by Favux on 2012-01-27
I'm not seeing it either.  I suppose you could just run through event numbers, but I'm not real hopeful.  Need to look at the kernel I guess.  Don't think I have the Natty kernel.

It's not in the *xinput list* output either.


Edit:  I think I found it in the linux-3.2-rc2 kernel I have laying around.  In linux-3.2-rc2/drivers/hid/hid-ids.h I see:
```
#define USB_VENDOR_ID_NEXTWINDOW	0x1926
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN	0x0003
```
You'll have to download your kernel's source code and see if it is in there:
```
apt-get source linux-image-`uname -r`
```
So I'm seeing the Vendor ID but apparently not the Product ID.

---

### Post by cbanakis on 2012-01-27
So I should run this?

apt-get source linux-image-`uname -r`

is that just a kernel update?

Or more of a customized kernel?

Sorry, I have done quite a bit in ubuntu, but never messed with the kernel.

---

### Post by Favux on 2012-01-27
That command will download your current Natty's 2.6.38 kernel source code.  Then in that downloaded file you want to go to the file hid-ids.h on the directory path I show and see if you have the NextWindow stuff I found in 3.2.

My guess is:
```
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN	0x0003
```
is the HP Touchsmart NextWindow touchscreen.

I looked further and in the hid-quirks.c file at linux-3.2-rc2/drivers/hid/usbhid I found in the blacklist:
```
	{ USB_VENDOR_ID_NEXTWINDOW, USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN, HID_QUIRK_MULTI_INPUT},
```
This quirk is presumably for the 0x0003 touchscreen.


Edit:  By the way we should see if we can get a HID report on the device.  That's a diagnostic that will be useful down the road.
```
sudo lsusb -vvvv
```

---

### Post by cbanakis on 2012-01-27
ok, my output from lsusb contains a section on Next Window.

I'm also attaching a text file of the entire output, just in case.
Was a bit tricky too.
Output is too big for terminal. (first half of output gets lost)
So I had to figure out how to export the output rather than display it.

```
Bus 002 Device 003: ID 1926:0dbf NextWindow 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         1 
  bMaxPacketSize0        64
  idVendor           0x1926 NextWindow
  idProduct          0x0dbf 
  bcdDevice            0.08
  iManufacturer           1 NextWindow
  iProduct                2 Touchscreen
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           57
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              3 Touchscreen
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              4 Touchscreen
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
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)
```

Thank you so much for your help with this.

For the 1st time in months, I am starting to feel hopeful that this will work at some point.

I still need to look into the other stuff you posted.

I am curious about the blacklist statement though.

I think I have run into info on that in my searches.

Why would it be blacklisted?

---

### Post by cbanakis on 2012-01-27
I found this in /drivers/hid/hid-ids

Not sure what that means though?

This seems to be way over my head.

```
#define USB_VENDOR_ID_NEXTWINDOW    0x1926
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN    0x0003

#define USB_VENDOR_ID_NTRIG        0x1b96
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN   0x0001
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_1   0x0003
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_2   0x0004
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_3   0x0005
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_4   0x0006
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_5   0x0007
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_6   0x0008
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_7   0x0009
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_8   0x000A
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_9   0x000B
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_10   0x000C
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_11   0x000D
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_12   0x000E
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_13   0x000F
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_14   0x0010
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_15   0x0011
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_16   0x0012
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_17   0x0013
#define USB_DEVICE_ID_NTRIG_TOUCH_SCREEN_18   0x0014
```

And

```
{ USB_VENDOR_ID_NEXTWINDOW, USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN, HID_QUIRK_MULTI_INPUT},
```

Is listed in drivers/hid/usbhid/hid-quirks.c

---

### Post by Favux on 2012-01-27
Sorry, my fault.  I wasn't clear, we needed the NextWindow section which you posted.

So basically I think we are looking at the fact that your model isn't yet supported by or added to the kernel.  If it is a standard HID input device then it would be on hiddev I think.  Which would mean the evdev driver would pick it up automatically, even in Natty maybe.  Sometimes all that is needed is to add the correct quirk for your Product ID to get it working.  Since the 2.6.38 kernel already contains the above NextWindow stuff then the first thing would likely be to add your Product ID to hid-ids.h, something like:
```
#define USB_VENDOR_ID_NEXTWINDOW	0x1926
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN	0x0003
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN	0x0dbf

```
And then compile the resulting new kernel module, hid.ko(?), and copy that into place in your current kernel.  Doing that would then probably get it using the quirk that is already there in the blacklist.  Not sure that's what you want.

Looking further I found on the Ubuntu multi-touch wiki's supported hardware page:  [https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport)
> Nextwindow is a touch device company. While no open source drivers exist for their products, they do support Ubuntu through their Nextwindow Fermi Driver project. 
The Nextwindow Fermi Driver project:  [https://launchpad.net/nwfermi](https://launchpad.net/nwfermi)  people are likely who you want to direct questions to.  You've now got some diagnostics you can share with them.  Doesn't look like they support your touchscreen yet, but if it is new they may want to.  It's multi-touch, right?  Do you know how many finger touch?  It is possible their current X driver might actually work for you once you get your touchscreen in the kernel.  Or only require minor changes.

Anyway using the Fermi Driver might be why the blacklist.

---

### Post by Favux on 2012-01-27
Ah, interesting.  I asked Chris Bagwell a couple questions about this touchscreen and he was nice enough to respond.  You may be able to get it working through the hid-multitouch.c in /drivers/hid:
> Multitouch's have to be white listed inside hid-multitouch.c.

There was a patch to hid-multitouch that auto-detected multi touch HID
devices that strictly followed HID standard and bound them to
hid-multitouch but it got reverted.

Its probably hard to describe to people how to add new touchscreen to
hid-multitouch.c because it has some pretty wide range of quirks.
They need to add something to mt_devices[] array and optionally to
mt_classes[] array if their device needs a custom set of quirks.  If
they start with this as a basis with no quirks, then when driver loads
there will be some stuff under /sys/kernel/debug or /sys/bus/hid that
will help debug further.

       /* GoodTouch panels */
       { .driver_data = MT_CLS_DEFAULT,
               HID_USB_DEVICE(USB_VENDOR_ID_GOODTOUCH,
                       USB_DEVICE_ID_GOODTOUCH_000f) },
That would be the ideal thing, keep it all OSS i.e. hid-multitouch for the kernel driver and evdev for the X driver.  But unless we got lucky we probably need a developer like Chris to figure out how to get hid-multitouch to work for us.

---

### Post by cbanakis on 2012-01-27
I can't remember where I saw the spec, but I'm pretty sure it said this display supports 10 touches.

Which seems pretty crazy advanced and not necessary to me.

But I guess most people have 10 fingers, so there ya go.

not sure how anyone could actually utilize that feature though.

---

### Post by Favux on 2012-01-27
Wow, 10?  I think N-Trig claims that too, but no one uses that many.  I think most stop at 4 or maybe 5.

Alright Chris is telling me we have to de-register the device from hidraw to get a full HID descriptor.  Because hidraw is claiming it we're not see the goodies in:
```
       Report Descriptors:
         ** UNAVAILABLE **

```
where "it should talk about having X and Y axis, a digitizer, and if its a multitouch device it should talk about "contacts"  Thats what makes it a multitouch HID device."  Unfortunately to de-register seems like a pain:  [http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)

Maybe if we check dmesg using the Vendor and/or Product ID we could glean a little more?
```
dmesg | grep 1926
```

---

### Post by cbanakis on 2012-01-27
dmesg | grep 1926
```
[    1.192675] PCI: CLS 64 bytes, default 64
[    1.192677] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.192680] Placing 64MB software IO TLB between ffff88001bc00000 - ffff88001fc00000
[    1.192682] software IO TLB at phys 0x1bc00000 - 0x1fc00000
[    1.193139] type=2000 audit(1327531926.800:1): initialized
[   14.953662] generic-usb 0003:1926:0DBF.0001: hiddev0,hidraw0: USB HID v1.11 Device [NextWindow Touchscreen] on usb-0000:00:1d.0-1.3/input1
```Honestly I would be happy with single touch.

I would like to use this as an htpc for my kitchen, and I doubt there is any use for multitouch in any htpc interfaces, nor do I see any benefit.

Edit...
It would be sweet to get all 10 touches, but thats mainly just on the principle that its supposed to do 10.
And so I can play with, and show off my toy.  :)

---

### Post by Favux on 2012-01-27
Well the first thing would be to add the touchscreen to the kernel.  Looking at other devices like the NTRIGs it appears what you should use is:
```
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN_1	0x0dbf
```
And looking at my current kernel it does look like the hid-ids.h gets compiled with hid-core.c etc. and becomes hid.ko.  So you'd copy the compiled hid.ko to:
```
/lib/modules/`uname -r`/kernel/drivers/hid
```
I believe.

---

### Post by cbanakis on 2012-01-27
> **Favux said:**
> Well the first thing would be to add the touchscreen to the kernel.  Looking at other devices like the NTRIGs it appears what you should use is:
```
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN_1    0x0dbf
```And looking at my current kernel it does look like the hid-ids.h gets compiled with hid-core.c etc. and becomes hid.ko.  So you'd copy the compiled hid.ko to:
```
/lib/modules/`uname -r`/kernel/drivers/hid
```I believe.


I am very sorry, please try to continue to bare with me...

I have no idea how to do that.

LOL

I found the file, but I'm not sure how to edit it.

Tried sudo gedit

But I guess gedit cannot open them?

Should I just add 
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN_1	0x0dbf
to the hid-ids.h file in the kernel source?
(Just add the line anywhere?)

Then somehow convert than into a hid.ko file.

Then use that file to replace /lib/modules/2.6.38-13-generic/kernel/drivers/hid/hid.ko

?

---

### Post by Favux on 2012-01-27
I was sort of musing aloud because I wasn't sure if you wanted to contact the folks at the Nextwindow Fermi Driver project first or go ahead and give the kernel a whirl.  Sounds like you want to try the kernel.

You've basically got it right.  I haven't actually worked in the HID directory before but I figure it is probably the same as the /drivers/input/tablet.

OK, give me a bit to whip up a mini HOW TO for you.

---

### Post by Favux on 2012-01-27
Assuming you want to work on your Desktop in a terminal you would enter:
```
cd Desktop

apt-get source linux-image-`uname -r`
```
Of course you've already downloaded the kernel source so you don't need to do this again.

Next backup your current hid-ids.h so you can restore it from the command line in Recovery mode if you need to.  I don't expect we'll break anything but best be prepared.
```
sudo cp /lib/modules/`uname -r`/kernel/drivers/hid/hid.ko /home/yourusername/Desktop/hid.ko.bak

```
Use your user name of course.  Then to restore the hid.ko:
```
sudo cp /home/yourusername/Desktop/hid.ko.bak /lib/modules/`uname -r`/kernel/drivers/hid/hid.ko
```
Write this down so you don't need the computer to access it.

Open a new terminal and edit the hid-ids.h file using:
```
gksudo gedit linux-2.6.38-13-generic/kernel/drivers/hid/hid-ids.h
```
I'm guessing the name of your kernel's downloaded source code folder is linux-2.6.38-13-generic.  If it is something else tell me.  It helps to turn on the line numbers in gedit (edit > preferences > view > display line numbers).  At around line #523 you'll see the NextWindow stuff.  Add:
```
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN_1	0x0dbf
```
so it looks like:
```
#define USB_VENDOR_ID_NEXTWINDOW	0x1926
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN	0x0003
#define USB_DEVICE_ID_NEXTWINDOW_TOUCHSCREEN_1	0x0dbf
```
Save and close.

Now in the original terminal change directory to the kernel source code /drivers/hid directory/folder and run this command:
```
make -C/lib/modules/`uname -r`/build M=`pwd` modules
```
Hopefully that will compile the stuff in the HID directory and you will be able to see a new hid.ko when you look with Places/Nautilus.  Then copy that into place
```
sudo hid.ko /lib/modules/`uname -r`/kernel/drivers/hid/hid.ko
```
Now rebuild all of the module dependencies:
```
sudo depmod -a
```
and then reboot.

Once it is back up see if the screen reacts to your finger.  Check the *dmesg* and *xinput list* commands and see if anything has changed with them.  Maybe we'll get lucky.

---

### Post by cbanakis on 2012-01-27
Thank you so much for your impeccable assistance.

Right now my computer as at work, so I won't be able to try till Monday.

But it looks like this should work.

Thank you very much.

I will post results Monday.

Fingers crossed.

---

### Post by cbanakis on 2012-02-02
Sorry it took me so long to get back.
This week ended up being twice as busy as our busiest week ever at work.

Been working 16 hour days, and never saw this coming.

Anyways, I had to improvise a little, but managed to add the line to hid-ids.h, and compile the hid.ko file, and I replaced the file in my system with the new one.

On the bright side, my computer did not break, but still no touching...

Is there anyway to see if the task succeeded?

Maybe the problem is elsewhere?

---

### Post by Favux on 2012-02-02
So we didn't get lucky, darn.  If the evdev driver claimed it you should see the touchscreen in *xinput list*.  Then you could use:
```
xinput list-props #
```
where # is the ID # in the output for the touchscreen or alternatively the "device name" (in quotes) from the output instead of the ID #.  That would show it is on the evdev driver.  So would looking in your Xorg.0.log in /var/log.

Alright, we could add it to the blacklist like the other NextWindow screen but I don't think that gets us anywhere.  Or we could try adding it to hid-multitouch.c.  But that isn't straight forward, if you remember the quote from Chris or have looked at the source code for it.  Unfortunately there isn't just a simple list in it we can add the touchscreen to so the white listing in the quote is a misnomer.  Basically we'd need a developer interested in adding the touchscreen to the open source drivers to have a chance.

I looked some more at the deb from "Nextwindow Fermi Driver":  [https://launchpad.net/nwfermi](https://launchpad.net/nwfermi)  It turns out that the package is actually a kernel driver.  And looking at the source code in the deb (the nw-fermi.c file) it actually looks like your model's product ID is close to some actually in there.  As a matter of fact it might just fit in here:
```
	{ USB_DEVICE(0x1926, 0x0DB6) },
	{ USB_DEVICE(0x1926, 0x0DB7) },
	{ USB_DEVICE(0x1926, 0x0E11) },
	{ USB_DEVICE(0x1926, 0x0E12) },
```
like so:
```
	{ USB_DEVICE(0x1926, 0x0DB6) },
	{ USB_DEVICE(0x1926, 0x0DB7) },
	{ USB_DEVICE(0x1926, 0x0DBF) },
	{ USB_DEVICE(0x1926, 0x0E11) },
	{ USB_DEVICE(0x1926, 0x0E12) },
```
around line #163, who knows?  Then from the FAQ they have on compiling the X driver I found "Nextwindow Xorg Input Driver for Fermi":  [https://launchpad.net/~djpnewton/+archive/xf86-input-nextwindow](https://launchpad.net/~djpnewton/+archive/xf86-input-nextwindow)

So I'm thinking your best bet is contacting the Fermi folks.  You'd want to copy your hid.ko.bak (i.e. the original) back into place to use their kernel (with the patch for your model) driver and X driver.

---

### Post by cbanakis on 2012-02-03
So, I spend a long time reading, tried a few things, and somewhere along the line broke my system to the point that I could not even get to a command line.

Then, using a live session usb stick, I spend a few hours undoing everything I did, and for some reason that did not work either.

Backing up all my stuff now, and doing a clean install, I guess I'll upgrade to 11.10 while I am at it.

Bah!!! unity...

I guess a fresh start might be what I need anyways.

*Sigh  ](*,)

---

### Post by Favux on 2012-02-03
Ouch.  Sorry, that is a bummer.  Oneiric Unity is better than Natty's.  And the evdev driver is better/more capable.  I think Precise will see further improvement.  Plus it should get the new multi-touch support that is now in the upcoming X server 1.12.

---

### Post by cbanakis on 2012-02-04
ok, so I did a clean install of 11.10 32bit

out of the box...

it is listed in lsusb as...
Bus 002 Device 003: ID 1926:0dbf NextWindow
 

And it is listed in dmesg as...
[    2.351389] generic-usb 0003:1926:0DBF.0003: hiddev0,hidraw2: USB HID v1.11 Device [NextWindow Touchscreen] on usb-0000:00:1d.0-1.3/input1


And I brought my computer home, so I can dedicate the entire weekend to making this thing work.

---

### Post by cbanakis on 2012-02-07
Well, that was a waste of time.

No progress at all.

I think I'm just gonna stick this on the back burner, and hope it will fix itself some day.

I'm still gonna leave this thread open, in case someone has a solution.

But it looks like I'm gonna have to revert to windows media center if I want to have a touch-screen htpc.

---

### Post by bpb101 on 2012-02-13
i had a quick google ,  try this.
[http://www.bytetips.com/touchscreen-support-ubuntu/](http://www.bytetips.com/touchscreen-support-ubuntu/)

---

### Post by cbanakis on 2012-02-13
> **bpb101 said:**
> i had a quick google ,  try this.
[http://www.bytetips.com/touchscreen-support-ubuntu/](http://www.bytetips.com/touchscreen-support-ubuntu/)

Thanks for the post, but I already tried than one.  :(


```
W: Failed to fetch http://ppa.launchpad.net/chasedouglas/multitouch/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/chasedouglas/multitouch/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
```

And then the obvious
```
E: Unable to locate package multitouch-kernel-source
```

---

### Post by grcastleton on 2012-07-12
I got this working by doing the following:

(Taken from this thread
[https://answers.launchpad.net/nwfermi/+question/186766](https://answers.launchpad.net/nwfermi/+question/186766) )

[LIST]
[*]sudo add-apt-repository ppa:djpnewton/xf86-input-nextwindow
[*]sudo apt-get update
[*]sudo apt-get install xf86-input-nextwindow patch
[*]wget [http://launchpad.net/nwfermi/trunk/0.6.1/+download/nwfermi-0.6.1.0_i386.deb](http://launchpad.net/nwfermi/trunk/0.6.1/+download/nwfermi-0.6.1.0_i386.deb)
[*]sudo apt-get install dkms
[*]sudo dpkg -i nwfermi-0.6.1.0_i386.deb
[*]sudo modprobe nw-fermi
[*]sudo sh -c "echo 1926 0dbf > /sys/bus/usb/drivers/nwfermi/new_id"
[/LIST]
At that point I was able to use the touch screen. Then to make the change persistent across a reboot, I did this:
[LIST]
[*]Add the line nw-fermi to the end of /etc/modules
[*]Added a few lines to /etc/rc.local so end of the file looks like following:
[/LIST]

# By default this script does nothing.
sh -c "echo 1926 0dbf > /sys/bus/usb/drivers/nwfermi/new_id"
/usr/sbin/nwfermi_daemon /daemon /instanceid 0
exit 0

---

### Post by glugauer on 2012-10-28
Thanks for leaving this trail on how you solved your problem.  I have a batch of private label (NextLink 5225-PL from Seneca Data) All-In-One touchscreens that I am configuring with 12.04.  These steps did the trick:

Get the nwfermi package from [https://launchpad.net/nwfermi](https://launchpad.net/nwfermi)
(nwfermi-0.6.5.0_i386.deb was the current version at this writing).  Assuming this is downloaded into your current directory:

```
sudo add-apt-repository ppa:djpnewton/xf86-input-nextwindow
sudo apt-get update
sudo apt-get install xf86-input-nextwindow
sudo dpkg -i nwfermi-0.6.5.0_i386.deb

```

```
sudo lsusb
```

Looks for a line like this:

```
Bus 002 Device 003: ID 1926:0e21 NextWindow
```

Note the "1926:0e21", this is what will be added to rc.local, substituting a space for the colon.

Add these lines to /etc/rc.local:

```
sh -c "echo 1926 0e21 > /sys/bus/usb/drivers/nwfermi/new_id"
/usr/sbin/nwfermi_daemon /daemon /instanceid 0
```

Add this line to /etc/modules:

```
nw-fermi
```

Reboot.

This worked like a charm for me, and that is because you paved the way first.  Thanks!

-G

---

### Post by FishRCynic on 2012-11-01
the above works great
purged - completely removed driver and x86 in synaptic
rebooted
installed using nwfermi-0.6.5.0_amd64.deb (amd64 system)
rebooted
works great 


------------------------------
used to work in 1204
since kernel updates in 1204.1 to current kernel

dmesg:
nw_fermi: disagrees about version of symbol module_layout
---------------------------------------------------------

---

### Post by Palfreman on 2013-03-21
I found I had to revert to the Linux 3.2 kernel in Ubuntu 12.04.2 to make the above work for nwfermi-0.6.5.

---

### Post by danielmgarcia on 2013-04-08
I wish multitouch was my only problem :(

from reading your thread, was wondering if you had any video driver issues and whether or not you needed and/or were able to find new drivers. I have an ET2012EUTS AIO that works fine on a generic VGA driver from fresh install, but when i start applying updates all hell breaks loose. Any feedback is greatly appreciated

---

