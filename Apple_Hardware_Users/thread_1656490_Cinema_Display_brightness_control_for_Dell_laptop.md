---
title: "Cinema Display brightness control for Dell laptop"
date: 2010-12-31
forum: Apple Hardware Users
---

### Post by Tomei Ningen on 2010-12-31
Hi,

I tested my Dell XPS 14 (L401X) and it can display 2560x1440 on the 27" Cinema Display. However, since there is a real hatred for buttons, there's no way to control the brightness of the display.

Is there are tool for non Apple computers to control the brightness of the Cinema Display?

I am using Ubuntu 10.10, 64-bit.

Thanks

---

### Post by Tomei Ningen on 2011-01-03
I figured it out myself, and now I am a happy (and newly impoverished) owner of the 27 inch Cinema Display :-)

To change the brightness, use acdcontrol. You can get it from:

[http://sourceforge.net/projects/acdcontrol/files/acdcontrol/0.4/acdcontrol-0.4.tar.gz/download](http://sourceforge.net/projects/acdcontrol/files/acdcontrol/0.4/acdcontrol-0.4.tar.gz/download)

And patch with

```
*** acdcontrol.cpp~     2007-04-05 07:41:50.000000000 -0700
--- acdcontrol.cpp      2011-01-03 00:53:42.000000000 -0800
***************
*** 59,64 ****
--- 59,65 ----
  const int CINEMA_DISPLAY_20_NEW           = 0x9219;
  const int CINEMA_DISPLAY_24               = 0x921e;
  const int CINEMA_DISPLAY_30               = 0x9232;
+ const int CINEMA_DISPLAY_27               = 0x9226;
  
  const int S1                              = 0x8002;
  
***************
*** 540,545 ****
--- 541,548 ----
                                       "Apple Cinema Display 24\"" ));
    supportedDevices.insert( DeviceId( APPLE, CINEMA_DISPLAY_30,
                                       "Apple Cinema HD Display 30\"" ));
+   supportedDevices.insert( DeviceId( APPLE, CINEMA_DISPLAY_27,
+                                      "Apple Cinema HD Display 27\"" ));
  
    supportedDevices.insert( DeviceId( SAMSUNG, S1,
                                       "Samsung SyncMaster 757NF" ));
```
Then, to find the current brightness:

```
~/apple/acdcontrol-0.4$ sudo ./acdcontrol /dev/usb/hiddev0 
Apple Cinema and Studio Display Control Program. Please, use --about switch to learn more
hiddev driver version is 1.0.4
/dev/usb/hiddev0: BRIGHTNESS=285

```To change:

```
~/apple/acdcontrol-0.4$ sudo ./acdcontrol /dev/usb/hiddev0  600
Apple Cinema and Studio Display Control Program. Please, use --about switch to learn more
hiddev driver version is 1.0.4

```Also, when you buy an ACD 27inch, the factory setting is set to auto-adjust according to ambient lighting conditions. So even if you can't get acdcontrol to work (e.g., you're using Windows), you should still get acceptable brightness.

Valid brightness values seems to be from 0 (darkest) to 1011 (brightness). Setting to higher than 1011 doesn't seem to hurt, but I won't recommend it :-)

---

### Post by TranceMusicAddict on 2011-10-24
Does anyone know if this is still working for Ubuntu 11.10 / the new kernel?
I read something about an apple_bl driver but i didn't find very much info about that at least no informations i'd understand. Is this tool obsolete with the new kernel? If yes, how does the brightness control work now?
I'm asking because I'm thinking of buying an Apple Cinema Display.

Thanks in advance

---

### Post by [o_0] Rob on 2011-10-26
> **TranceMusicAddict said:**
> I'm thinking of buying an Apple Cinema Display.

I'm considering the same thing and it would be great to know how hard it is to adjust the brightness.

---

### Post by joshnabbott on 2011-12-20
For anyone out there considering running a cinema display, I just got a new 27" Cinema Display working beautifully with this patched version of acdcontrol.

Thanks!

---

### Post by robfindlay on 2012-01-01
> **Tomei Ningen said:**
> I figured it out myself, and now I am a happy (and newly impoverished) owner of the 27 inch Cinema Display :-)

To change the brightness, use acdcontrol. You can get it from:

[http://sourceforge.net/projects/acdcontrol/files/acdcontrol/0.4/acdcontrol-0.4.tar.gz/download](http://sourceforge.net/projects/acdcontrol/files/acdcontrol/0.4/acdcontrol-0.4.tar.gz/download)

And patch with

```
*** acdcontrol.cpp~     2007-04-05 07:41:50.000000000 -0700
--- acdcontrol.cpp      2011-01-03 00:53:42.000000000 -0800
***************
*** 59,64 ****
--- 59,65 ----
  const int CINEMA_DISPLAY_20_NEW           = 0x9219;
  const int CINEMA_DISPLAY_24               = 0x921e;
  const int CINEMA_DISPLAY_30               = 0x9232;
+ const int CINEMA_DISPLAY_27               = 0x9226;
  
  const int S1                              = 0x8002;
  
***************
*** 540,545 ****
--- 541,548 ----
                                       "Apple Cinema Display 24\"" ));
    supportedDevices.insert( DeviceId( APPLE, CINEMA_DISPLAY_30,
                                       "Apple Cinema HD Display 30\"" ));
+   supportedDevices.insert( DeviceId( APPLE, CINEMA_DISPLAY_27,
+                                      "Apple Cinema HD Display 27\"" ));
  
    supportedDevices.insert( DeviceId( SAMSUNG, S1,
                                       "Samsung SyncMaster 757NF" ));
```
Then, to find the current brightness:

```
~/apple/acdcontrol-0.4$ sudo ./acdcontrol /dev/usb/hiddev0 
Apple Cinema and Studio Display Control Program. Please, use --about switch to learn more
hiddev driver version is 1.0.4
/dev/usb/hiddev0: BRIGHTNESS=285

```To change:

```
~/apple/acdcontrol-0.4$ sudo ./acdcontrol /dev/usb/hiddev0  600
Apple Cinema and Studio Display Control Program. Please, use --about switch to learn more
hiddev driver version is 1.0.4

```Also, when you buy an ACD 27inch, the factory setting is set to auto-adjust according to ambient lighting conditions. So even if you can't get acdcontrol to work (e.g., you're using Windows), you should still get acceptable brightness.

Valid brightness values seems to be from 0 (darkest) to 1011 (brightness). Setting to higher than 1011 doesn't seem to hurt, but I won't recommend it :-)

Hate to re-open an old thread but could someone point me to some instructions on how to run this script?

-rob

---

