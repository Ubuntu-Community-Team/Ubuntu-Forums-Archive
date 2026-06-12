---
title: "/dev/sd*"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by martin_prior on 2006-10-12
I have installed Ubuntu Dapper. Can anyone tell me if /dev/sd* should have been created during the install?

It appears that this device is needed to get my camera to work with Gphoto2 etc. 

How are they created?

Regards

Martin Prior

---

### Post by PriceChild on 2006-10-12
Plug your camera in.... it should be made then.

---

### Post by martin_prior on 2006-10-12
Thanks for the response. No they are not created when the camera is plugged in. The camera is recognised and work fine with the spca500x/v4lin streaming video. It just will not connect to download pics from the camera.

```
env LANG=C gphoto2 --debug -P
0.000029 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000362 main(2): gphoto2 2.1.6
0.000526 main(2): gphoto2 has been compiled with the following options:
0.000685 main(2):  + gcc (C compiler used)
0.000841 main(2):  + no popt (for handling command-line parameters)
0.000997 main(2):  + exif (for displaying EXIF information)
0.001154 main(2):  + cdk (for accessing configuration options)
0.001310 main(2):  + no aa (for displaying live previews)
0.001466 main(2):  + jpeg (for displaying live previews in JPEG format)
0.001622 main(2):  + readline (for easy navigation in the shell)
0.001788 main(2): libgphoto2 2.1.6
0.001951 main(2): libgphoto2 has been compiled with the following options:
0.002110 main(2):  + gcc (C compiler used)
0.002266 main(2):  + EXIF (for special handling of EXIF files)
0.002423 main(2):  + no ltdl (working around buggy libltdl, eh? :-)
0.002579 main(2):  + /proc/meminfo (adapts cache size to memory available)
0.002745 main(2): libgphoto2_port 0.5.1
0.002908 main(2): libgphoto2_port has been compiled with the following options:
0.003068 main(2):  + gcc (C compiler used)
0.003226 main(2):  + USB (for USB cameras)
0.003442 main(2):  + serial (for serial cameras)
0.003599 main(2):  + no resmgr (serial port access and locking)
0.003756 main(2):  + no baudboy (serial port locking)
0.003912 main(2):  + no ttylock (serial port locking)
0.004070 main(2):  + no lockdev (serial port locking)
0.004226 main(2):  + no ltdl (working around buggy libltdl, eh? :-)
0.005178 gphoto2-camera(2): Listing files in '/'...
0.005588 gphoto2-camera(2): Initializing camera...
0.005819 gphoto2-port-usb(1): Looking for USB device (vendor 0x40a, product 0x300)... found.
0.006005 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep ffffffff, outep ffffffff, intep ffffffff, class ff, subclass 00
0.006176 gphoto2-camera(2): Loading '/usr/lib/gphoto2/2.1.6/libgphoto2_ez200.so'...
0.006742 gphoto2-port(2): Opening USB port...
0.007173 gphoto2-port(0): Could not query kernel driver of device.
0.007415 ez200/library.c(2): Initializing Kodak EZ200

0.007609 gphoto2-port(2): Setting settings...
0.007796 gphoto2-port-usb(2): releasing the iface for config failed.
0.008536 gphoto2-port(0): Could not set config 1/1 (Device or resource busy)
0.008766 gphoto2-port(2): Closing port...
0.008950 gphoto2-port(0): Could not release interface 1 (Invalid argument).
0.009239 context(0): An error occurred in the io-library ('Error updating the port settings'): Could not release interface 1 (Invalid argument).

*** Error ***
An error occurred in the io-library ('Error updating the port settings'): Could not release interface 1 (Invalid argument).
*** Error (-37: 'Error updating the port settings') ***

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug -P

Please make sure there is sufficient quoting around the arguments.

0.065080 gp-camera(2): Freeing camera...
0.065264 gphoto2-port(2): Freeing port...
0.065427 gphoto2-port(2): Closing port...
0.065617 gphoto2-port(0): Could not release interface 1 (Invalid argument).
0.065892 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.066065 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.066222 gphoto2-filesystem(2): Internally deleting all folders from '/'...
```

I assume this is becasue the /dev/sd* file is not being created.

---

### Post by PriceChild on 2006-10-12
> **martin_prior said:**
> The camera is recognised and work fine with the spca500x/v4lin streaming video.
Could you check the settings menu of your camera please.

I think that you may likely find a place to switch from "webcam" to "disc" on usb.

---

### Post by martin_prior on 2006-10-12
Sorry, the camera ez200 is a real cheap and quite old camera, it does not have these settings.

I just moved from Mandriva to Ubuntu. Gphoto2, DigiKam etc worked fine with thsi camera and machine.

---

