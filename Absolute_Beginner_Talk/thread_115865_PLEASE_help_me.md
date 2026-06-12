---
title: "PLEASE help me"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by lost1234 on 2006-01-11
Could anyone tell me how to get a usb webcam to work on ubuntu 2.10, 5.04 I believe it is called hoary.
the camera vendor and product id match a driver called sn9c102
i have installed sn9c102-1.24
everytime i install anything like motion or sn-webcam or gqcam ...
and I fix the dependancies and they install, I try to run them and they tell me that I dont have a video* or video0...
ie : 
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Thread is from /etc/motion/motion.conf
[1] Thread started
[1] Failed to open video device /dev/video0: No such file or directory
[1] Capture error calling vid_start
[1] Thread finishing...

as you can see I need help.
also the device manager says that the camera is unknown.

also in /dev there is only a video1394 entry, if that helps
there is /.dev/video0 to video63

---

### Post by srt4play on 2006-01-11
What is the make and model of the camera?

---

### Post by lost1234 on 2006-01-11
ohci_hcd 0000:00:02.0: ALi Corporation USB 1.1 Controller
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 9, pci mem 0xdf800000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using ohci_hcd and address 2
Linux video capture interface: v1.00
sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.19
usb 1-2: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
usb 1-2: No supported image sensor detected
usb 1-2: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
usb 1-2: No supported image sensor detected
usb 1-2: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
usb 1-2: No supported image sensor detected
usbcore: registered new driver sn9c102
usbcore: registered new driver snd-usb-audio
via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5



this is from dmesg
I forget how I got the product id and vendor id
if you could tell me how to get this.
The box for the webcam says icam

---

### Post by srt4play on 2006-01-11
Have you been to this site already? 

[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")

---

### Post by lost1234 on 2006-01-11
yes it has the sn9c102 software.
I think one of the numbers was 0x608f for vendor id
If you can tell me the command to check the vendor and product numbers, I will respond with the info.

---

### Post by lost1234 on 2006-01-11
could anyone help me with this.
I have tried all I have found so far.

---

### Post by Sef on 2006-01-11
Have you thought about upgrading to Breezy 5.10?  That might help.

---

### Post by lost1234 on 2006-01-12
I started with warty 2.8 and got vnc working and amsn working , but could not get camera to work or usb harddrive to be recognized, I was able to share files and print to a hp but not an epson c66, I had ftp working and apache1 working with php. 
But due to the camera and usb drive I installed 2.10 hoary and started all over again, I now have ftp working, apache2 working the usb drive can be seen, i have telnet going and can print to hp again, can share files on network. I can not print to epson or use camera.
Now you tell me I should start again with breezy. I can't bring myself to do all that work over again to be disappointed when the camera does not work again.
This is my first try with linux and I could install crappy windows and the camera would work in 2 minutes.
I just want the camera to work. I like ubuntu and want to learn more programs and install more software, but I have been working on getting this camera going for 4 weeks and a different camera before that on warty, which did not work, so i went out and bought the new webcam.
tried it then upgraded to hoary.
I am just frustrated at all the time I have put in that it does not work and the  members of this site that are fully versed in ubuntu do not give me any assistance. I tried to send a message to one of them and they told me to make a thread, which does not get responses.

---

### Post by YoungJules on 2006-01-12
I know how it feels, I went through several distros and much pain just trying to get a simple usb wireless doo-hickey to work.  I can say that Breezy 5.10 is the best distro I've tried so far, and it even supported (finally!) my usb-doohickey right out of the box!
Stick with it, don't give in to temptation even though Bill :evil:  wants you back and will make it oh-so-simple for you...

As for the poor responses, I guess you can't force people to reply... 

... BUT sending private messages is a bad idea, even from just a mathematical standpoint (never mind the fact you might be bugging someone who doesn't want to be bugged).  Think about it, one PM, gets to one person who might know the answer... one post gets to x hundred thousand pepole who might know the answer... :lol: 

Keep with it, you'll get there.

---

### Post by lost1234 on 2006-01-12
Thanks for the support.
It is frustrating, none of my friends know linux and you can not make people reply.
I have spend all my free time in the last 3 months learning how to use the os (simple commands like ls, then i found ls -l) and dependancies and packages, then errors and make and make install. 
I have tried different camera's (2) and 3 different drivers and other software like motion, spca5xx, sn-webcam etc.. to no avail.
is there a way to upgrade to breezy without losing my ftp and apache setup?

---

### Post by YoungJules on 2006-01-12
No problem, I PM'd you already on the Webcam question.  As for keeping your Apache and ftp setup, that shouldn't be a problem if you upgrade to 5.10, just make sure you don't choose an option that sounds anything like "erase all partitions and install Ubuntu completely from scratch"... ;-)

---

### Post by YoungJules on 2006-01-13
Hi, I tried 3 different webcams last night.  The one that appeared to be most successful (according to dmesg) was one from Zoom.  But, I get the same error as you on trying to run xawtv or webcam etc.  I'll check it out more thoroughly over the weekend as I want to use a webcam on my system too :-)

---

### Post by chele on 2006-01-14
Please see this [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam")  page for EasyCam, an easy to use utility to download and build drivers for many webcams.

---

### Post by YoungJules on 2006-01-16
It's less simple than that.  The package has already been renamed to easycam2 (follow the instructions to the letter and you get "package not found"), also you will get a warning that the package is not authenticated (so you take a chance that it's a rootkit or something worse...).  Then you have to know which additional 'easy' script to take... based on the particular model of webcam you have.
But, thanks for the pointer anyway.  I'll let you know how it goes... :-)

---

### Post by migraineboy on 2006-01-16
Hi! I'm trying to install easycam, but it seems that the repository indicated it's not working. Does anybody know where I can find it?

---

### Post by flip on 2006-01-16
[QUOTE=lost1234]yes it has the sn9c102 software.
I think one of the numbers was 0x608f for vendor id
If you can tell me the command to check the vendor and product numbers, I will respond with the info.[/QUOTE]
For those looking to get usb device info try 'cat /proc/bus/usb/devices'. Mine turns up this for my QuickCam

```

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=0850 Rev= 1.00
S:  Product=Camera
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=quickcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   1 Ivl=16ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=quickcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   1 Ivl=16ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS= 100 Ivl=1ms

```

I have a super old QuickCam so the drivers "just work" but the image quality is pretty crappy. 

Good luck and I hope this helps a bit.

---

### Post by rklauco on 2006-06-26
Was there any progress in this one?
I am just trying to get the Genius Track 310 infra to work under dapper.
I tried the latest spca5xx driver, also the ov511 and sn9c102 (all recompiled from the latest version on web).
No luck yet.
After the spca compilation I finnaly get at least the image sensor to be known, but nothing more - no v4l program works (e.g. camorama).
The gmesg follows:
```
[17186711.828000] usb 4-1: new full speed USB device using uhci_hcd and address 10
[17186711.968000] usb 4-1: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
[17186712.040000] usb 4-1: OV7630 image sensor detected
[17186712.176000] usb 4-1: Initialization succeeded
[17186712.176000] usb 4-1: V4L2 device registered as /dev/video0
```
From what I can see, the device is recognized, so is the image sensor, but when starting camorama I get:
```
Could not connect to video device (/dev/video0).
Please check connection.
```
And the debug mode says:
```
VIDIOCGCAP  --  could not get camera capabilities, exiting.....
```
The lsusb -vv follows:
```
Bus 004 Device 010: ID 0c45:608f Microdia
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0c45 Microdia
  idProduct          0x608f
  bcdDevice            1.01
  iManufacturer           0
  iProduct                1 USB camera
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          370
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x02a8  1x 680 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0320  1x 800 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0384  1x 900 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       8
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03eb  1x 1003 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0
      iInterface              0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           30
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0
        iTerminal               0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               1
        iTerminal               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]         8000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0014  1x 20 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
Device Status:     0x0000
  (Bus Powered)

```

---

