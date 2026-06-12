---
title: "usb optical mouse"
date: 2005-01-02
forum: Apple PPC Users
---

### Post by tiiim on 2005-01-02
how do i get an external USB optical mouse to work on Ubuntu?

I try plug and play but dont work.... is there an option or something? or a module to install?

Tim

---

### Post by wulf on 2005-01-02
What kind of mouse? I've got a Microsoft optical wheel mouse attached to my USB and it works with no problems (although I did have it when I installed the system - it's possible that hardware detection in the installer did something to make it work).

Also, what kind of machine are you using it on? I'm using a Packard Bell EasyNote M5262 laptop.

Wulf

---

### Post by tiiim on 2005-01-02
[QUOTE=wulf]What kind of mouse? I've got a Microsoft optical wheel mouse attached to my USB and it works with no problems (although I did have it when I installed the system - it's possible that hardware detection in the installer did something to make it work).

Also, what kind of machine are you using it on? I'm using a Packard Bell EasyNote M5262 laptop.

Wulf[/QUOTE]


Im using a mini-optical mouse cant remember the manafature off hand just says mini-optical mouse.

Im using an Apple iBook.

---

### Post by wulf on 2005-01-02
Apple iBook? Outside my experience I'm afraid but that might be enough to prompt another iBook user to pipe up. Anyone?

Wulf

---

### Post by danderso on 2005-01-02
Did you try to reboot after installing the mouse?  If you did, sorry and feel free to ignore this very simple suggestion...

---

### Post by tiiim on 2005-01-03
[QUOTE=danderso]Did you try to reboot after installing the mouse?  If you did, sorry and feel free to ignore this very simple suggestion...[/QUOTE]


I just put the mouse in and booted up but no luck still dont reconise it....

any other ideas? is this a Ubuntu bug or is it the mouse? Or is there something silly like a adding program. I think i remember correctly that when i installed YDL ages ago and dowloaded the Red Hat mouse config prog it didnt reconise it so may not be supported... in which case what optical mouse is supported? pref a small laptop one...

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]how do i get an external USB optical mouse to work on Ubuntu?

I try plug and play but dont work.... is there an option or something? or a module to install?

Tim[/QUOTE]

OK, you did not have this mouse when you installed, correct?

You will need to check /etc/X11/XF86Config-4, look for the inputdevice section of you mouse.
It will have one option that specifies the device (/dev/...).  This needs to point to the device where your mouse is actually connected (the USB port).

---

### Post by tiiim on 2005-01-03
yes i didnt have the mouse installed when i install so that a prob. The file has detected by touchpad on laptop but descion where it says "configured mouse" links to

/dev/input/mice

protocal "ImPS/2"


etc

so how do i config it for the USB i only have 2 on my iBook can i config to hotplug for both or just one either way one is fine. once set up will it hotplug it if i plug and play?

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]yes i didnt have the mouse installed when i install so that a prob. The file has detected by touchpad on laptop but descion where it says "configured mouse" links to

/dev/input/mice

protocal "ImPS/2"


etc

so how do i config it for the USB i only have 2 on my iBook can i config to hotplug for both or just one either way one is fine. once set up will it hotplug it if i plug and play?[/QUOTE]


OK, that will be the problem.
Can you try something.  Unplug the mouse, open op a terminal window.
run:
tail -f /var/log/messages

plug in the  mouse.

What appears in the messages?

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]
so how do i config it for the USB i only have 2 on my iBook can i config to hotplug for both or just one either way one is fine. once set up will it hotplug it if i plug and play?[/QUOTE]

Perhaps some explanation is in order.

Hotplug should detect your mouse when plugged in (if it is supported).  It will then load the kernel module to make it function.

It will however not do anything else (such as modifying your X configuration to point to the new device).   Your X configuration was auto-detected at install time, and is now static (this is still a drawback for Linux).
This means you will need to modify it to point to the USB device.

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]OK, that will be the problem.
Can you try something.  Unplug the mouse, open op a terminal window.
run:
tail -f /var/log/messages

plug in the  mouse.

What appears in the messages?[/QUOTE]


ok i type exluding the date and time


ohci_hcd 0001:01:1b.1: wakeup
usb 3-1: new low speed USB device using address 4
usbhid: prob of 3-1:1.0 failed with error -5
usbhid: already loaded



on the left side was date name of comp and whether from kernel or usb.agent

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Perhaps some explanation is in order.

Hotplug should detect your mouse when plugged in (if it is supported).  It will then load the kernel module to make it function.

It will however not do anything else (such as modifying your X configuration to point to the new device).   Your X configuration was auto-detected at install time, and is now static (this is still a drawback for Linux).
This means you will need to modify it to point to the USB device.[/QUOTE]

well its detected it so hotplug supported

maybe someone should write to the X developers and get them to fix this bug in todays USB plug in windows world i dont think the rest of the world want to be hacking X11 or XORG files to sort this...


anyways back to resolving my issue...

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]ok i type exluding the date and time


ohci_hcd 0001:01:1b.1: wakeup
usb 3-1: new low speed USB device using address 4
usbhid: prob of 3-1:1.0 failed with error -5
usbhid: already loaded



on the left side was date name of comp and whether from kernel or usb.agent[/QUOTE]

Hmm.  Can you try two things (with the mouse plugged in).
In a terminal type:
lsmod
and paste the output

In a terminal type:
find /dev |grep -i usb |grep -i mouse
and paste the output

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Hmm.  Can you try two things (with the mouse plugged in).
In a terminal type:
lsmod
and paste the output

In a terminal type:
find /dev |grep -i usb |grep -i mouse
and paste the output[/QUOTE]


Ismod does not work no command even as sudo

and /dev one just says its a directory and as sudo says command not found.

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]Ismod does not work no command even as sudo

and /dev one just says its a directory and as sudo says command not found.[/QUOTE]

Do you have any entries in /dev like
/dev/input/mouse0, /dev/input/mouse1, ... ?

what does 
ls -ld /dev/input/mice 
say?

(I'm going to get a sandwich right now, will be back in 15 minutes)

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Do you have any entries in /dev like
/dev/input/mouse0, /dev/input/mouse1, ... ?

what does 
ls -ld /dev/input/mice 
say?

(I'm going to get a sandwich right now, will be back in 15 minutes)[/QUOTE]


i do have those entries in /dev/input      :D 


the command says:

1513 /dev/input/mice


(im taking my Fiancée out to lunch now wont be back until much later if  not early eve... so you have a few hours to bang your heads together  :D )

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]i do have those entries in /dev/input      :D 


the command says:

1513 /dev/input/mice


(im taking my Fiancée out to lunch now wont be back until much later if  not early eve... so you have a few hours to bang your heads together  :D )[/QUOTE]

Ok, I will be online until 1600 UTC (possibly later).  
I'm guessing one of those is your mouse. 

What can help is this.
- unplug your mouse
- reboot (with mouse unplugged)

run:
find /dev >/tmp/nomouse.list
 
plug in the mouse.
run:
find /dev >/tmp/mouse.list

Now check the difference:
diff /tmp/nomouse.list /tmp/mouse.list

Another thing, try googling for your type/brand of mouse to see which protocol it uses (IMPS/2 is not for all mice).

I hope you enjoy your dinner.

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Ok, I will be online until 1600 UTC (possibly later).  

run:
find /dev >/tmp/nomouse.list
 
plug in the mouse.
run:
find /dev >/tmp/mouse.list

Now check the difference:
diff /tmp/nomouse.list /tmp/mouse.list

Another thing, try googling for your type/brand of mouse to see which protocol it uses (IMPS/2 is not for all mice).
[/QUOTE]

ran the program

on the difference it said there was no nomouse.list

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]ran the program

on the difference it said there was no nomouse.list[/QUOTE]

Did you run both ?
find /dev > /tmp/**nomouse.list** 
find /dev > /tmp/**mouse.list** 

then 
diff /tmp/nomouse.list /tmp/mouse.list

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Did you run both ?
find /dev > /tmp/**nomouse.list** 
find /dev > /tmp/**mouse.list** 

then 
diff /tmp/nomouse.list /tmp/mouse.list[/QUOTE]
 ah!! done!

The output was blank.

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]ah!! done!

The output was blank.[/QUOTE]

Strange... did you run the first find after a clean boot with the mouse unplugged and the second after plugging in the mouse?

What brand/type of mouse are you using?

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Strange... did you run the first find after a clean boot with the mouse unplugged and the second after plugging in the mouse?

What brand/type of mouse are you using?[/QUOTE]
 sorry misread you but did it again and was still blank.

im using well it doenst say a brand really just says "mini optical mouse"

However S/N is 0003831
model: AM-1310-u

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]sorry misread you but did it again and was still blank.

im using well it doenst say a brand really just says "mini optical mouse"

However S/N is 0003831
model: AM-1310-u[/QUOTE]

Hm, I think it is this one:
[http://www.protacnz.co.nz/products/mouse/AM1310U.htm](http://www.protacnz.co.nz/products/mouse/AM1310U.htm)

I can't find much about it though.

Can you check another logfile.  It is in /var/log called xfree -  something.

Is there anything about the mouse in there.

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]Hm, I think it is this one:
[http://www.protacnz.co.nz/products/mouse/AM1310U.htm](http://www.protacnz.co.nz/products/mouse/AM1310U.htm)

I can't find much about it though.

Can you check another logfile.  It is in /var/log called xfree -  something.

Is there anything about the mouse in there.[/QUOTE]
 thats the mouse!

read the XF86 file and one bit says "|-->input device "configured mose" that line is before the touch pad input

if that links to something else can see off hand 

then scrolling to end i find "configured mouse: Protocal: "imps/2"

then scroll more it says /dev/input/mouse



If this is going to be a problem just point me to an optical mouse that will work and i just give this one to some one else lol.

---

### Post by nocturn on 2005-01-03
[QUOTE=tiiim]thats the mouse!

read the XF86 file and one bit says "|-->input device "configured mose" that line is before the touch pad input

if that links to something else can see off hand 

then scrolling to end i find "configured mouse: Protocal: "imps/2"

then scroll more it says /dev/input/mouse



If this is going to be a problem just point me to an optical mouse that will work and i just give this one to some one else lol.[/QUOTE]

The problem is that for each mouse you buy, you will have to figure out what protocol it uses.  For most bigger brands, you will quickly find that information on google.

That, and I'm not sure on which device it is connecting.  If I had access to my Ubuntu system I could check something.... (maybe tonight if my baby-son allows it).

---

### Post by tiiim on 2005-01-03
[QUOTE=nocturn]The problem is that for each mouse you buy, you will have to figure out what protocol it uses.  For most bigger brands, you will quickly find that information on google.

That, and I'm not sure on which device it is connecting.  If I had access to my Ubuntu system I could check something.... (maybe tonight if my baby-son allows it).[/QUOTE]

sure well let me know when you can. If not i buy a bigger brand mouse and check it on google first before i purchase. But check ya system when ya can and we decide later which is the best option and if you know a good big brand that be a bonus. Hear from ya at somepoint.... thanks so far you been very helpful.

---

### Post by nocturn on 2005-01-04
[QUOTE=tiiim]sure well let me know when you can. If not i buy a bigger brand mouse and check it on google first before i purchase. But check ya system when ya can and we decide later which is the best option and if you know a good big brand that be a bonus. Hear from ya at somepoint.... thanks so far you been very helpful.[/QUOTE]


OK, I tried this on my system yesterday.
I normally use a PS/2 mouse (Logitech).  So I plugged in an optical USB mouse next to it.  And both mice just worked, at the same time.

So, I'm assuming that /dev/input/mice points to multiple devices in some way.
You mouse should also attach to this device, so that should not be the problem.

What I noticed is that when I plug in my USB mouse, a message gets logged:

```

ohci_hcd 0000:00:02.2: wakeup
usb 1-3: new low speed USB device using address 2
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on
usb-0000:00:02.2-3
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver

```

It says the actual brand and type of the mouse used, regardless what the box said.

Can you check that on you system by:
- open a terminal
- plug in the mouse
type:
dmesg

---

### Post by tiiim on 2005-01-04
[QUOTE=nocturn]OK, I tried this on my system yesterday.
I normally use a PS/2 mouse (Logitech).  So I plugged in an optical USB mouse next to it.  And both mice just worked, at the same time.

So, I'm assuming that /dev/input/mice points to multiple devices in some way.
You mouse should also attach to this device, so that should not be the problem.

What I noticed is that when I plug in my USB mouse, a message gets logged:

```

ohci_hcd 0000:00:02.2: wakeup
usb 1-3: new low speed USB device using address 2
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on
usb-0000:00:02.2-3
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver

```

It says the actual brand and type of the mouse used, regardless what the box said.

Can you check that on you system by:
- open a terminal
- plug in the mouse
type:
dmesg[/QUOTE]


The bit of dmesg you want says:
> 
ohci_hcd 0001:01:1b.1: wakeup
usb 3-1: new low speed USB device using address 2
usbhid: probe of 3-1:1.0 failed with error -5



hmmm

---

### Post by nocturn on 2005-01-04
[QUOTE=tiiim]The bit of dmesg you want says:



hmmm[/QUOTE]

There is no line like this:
input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on ...

So this is the problem.
It is not recognizing your mouse as ... a mouse.

Ok, try using lsusb like this (in a terminal with the mouse plugged in)
sudo /sbin/lsusb -v

Look for the section for your mouse

---

### Post by tiiim on 2005-01-04
[QUOTE=nocturn]There is no line like this:
input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on ...

So this is the problem.
It is not recognizing your mouse as ... a mouse.

Ok, try using lsusb like this (in a terminal with the mouse plugged in)
sudo /sbin/lsusb -v

Look for the section for your mouse[/QUOTE]

i dont think that file exists on my machine...

---

### Post by tiiim on 2005-01-04
[QUOTE=tiiim]i dont think that file exists on my machine...[/QUOTE]
 ah if i run slusb -v i get something its not in /sbin hang on i try paste the code

---

### Post by tiiim on 2005-01-04
```


Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.8.1-4-powerpc ehci_hcd
  iProduct                2 NEC Corporation USB 2.0
  iSerial                 1 0001:01:1b.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  bytes 2 twice
        bInterval              12


```

I think that the bit its on number if not i past the whole lot in.

I may not be able to reply until this eve if not reply soon so either i follower up in few mins if not in few hours.

---

### Post by tiiim on 2005-01-04
i get confused here rest of code just in case i missed it

```


Bus 003 Device 002: ID 04b4:0202 Cypress Semiconductor Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x0202
  bcdDevice            0.00
  iManufacturer           1 Adomax
  iProduct                2 USB/PS2 Scroll Mouse
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         8704
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HID-Compliant Mouse
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              5 ??
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  bytes 4 three times
        bInterval              10
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      76

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.8.1-4-powerpc ohci_hcd
  iProduct                2 NEC Corporation USB (#2)
  iSerial                 1 0001:01:1b.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  bytes 2 twice
        bInterval             255

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.8.1-4-powerpc ohci_hcd
  iProduct                2 NEC Corporation USB
  iSerial                 1 0001:01:1b.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  bytes 2 twice
        bInterval             255

Bus 001 Device 002: ID 05ac:1000 Apple Computer, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x1000
  bcdDevice           15.86
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength        15104
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  bytes 16 once
        bInterval               1
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  bytes 16 once
        bInterval               1
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      61

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.8.1-4-powerpc ohci_hcd
  iProduct                2 Apple Computer Inc. KeyLargo/Intrepid USB (#3)
  iSerial                 1 0001:01:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  bytes 2 twice
        bInterval             255


```

beep in mind i do have a touch pad on comp

---

### Post by nocturn on 2005-01-04
[QUOTE=tiiim]i dont think that file exists on my machine...[/QUOTE]

You mean lsusb?
If it is not installed try:
aptitude install usbutils

On a seperate thought, do you know anyone near you who has another optical mouse (USB).  Maybe you can borrow it and try if that one works just to be sure (I have no experience with ibook hardware).

If you consider buying a new one, I have very good experiences with Logitech on Linux.

---

### Post by nocturn on 2005-01-04
Something interesting here:
[http://gentoo-wiki.com/HARDWARE_ID_04b4:0202_Cypress_Semiconductor_Corp#Works_With](http://gentoo-wiki.com/HARDWARE_ID_04b4:0202_Cypress_Semiconductor_Corp#Works_With)

It says XF86Config should be like this:

```
 
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"

```

Do you have the SendCoreEvents in it?

---

### Post by tiiim on 2005-01-04
[QUOTE=nocturn]Something interesting here:
[http://gentoo-wiki.com/HARDWARE_ID_04b4:0202_Cypress_Semiconductor_Corp#Works_With](http://gentoo-wiki.com/HARDWARE_ID_04b4:0202_Cypress_Semiconductor_Corp#Works_With)

It says XF86Config should be like this:

```
 
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"

```

Do you have the SendCoreEvents in it?[/QUOTE]


BINGO! We killed a bird with 2 stones.

One other mice did work straight away.

two when i added sendcore the mouse works! Problem fixed! THANK YOU SO MUCH! :D

---

### Post by tiiim on 2005-01-04
[QUOTE=tiiim]BINGO! We killed a bird with 2 stones.

One other mice did work straight away.

two when i added sendcore the mouse works! Problem fixed! THANK YOU SO MUCH! :D[/QUOTE]
 well works on the other USB port anyway but dont matter it works that main thing!

---

### Post by nocturn on 2005-01-04
[QUOTE=tiiim]well works on the other USB port anyway but dont matter it works that main thing![/QUOTE]


The previous link I send you warned that it had to be unplugged/replugged sometimes, so you might still experience some problems.

anyway, good luck with it.

---

### Post by tiiim on 2005-01-04
[QUOTE=nocturn]The previous link I send you warned that it had to be unplugged/replugged sometimes, so you might still experience some problems.

anyway, good luck with it.[/QUOTE]

correction works on both USB ports but yes it does happen if you unplug and re plug lots it does not respond you have to restart X the wait to all loaded and try again it does resolve itself after a moments anyway

---

