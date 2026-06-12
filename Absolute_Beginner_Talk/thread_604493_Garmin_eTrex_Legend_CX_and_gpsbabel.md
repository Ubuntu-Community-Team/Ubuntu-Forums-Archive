---
title: "Garmin eTrex Legend CX and gpsbabel"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-11-06
I have a Garmin eTrex Legend CX and I want to add some tracks. GpsBabel works well with converting the data from Google Earth to gpx, but this is where everything stops.

With dmesg I get 
```
[153538.516000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
```
over and over again. With gpstrans I get an additional segfault to this.

The line is
```
gpsbabel -r -i gpx -f foo.gpx -o garmin -F /dev/ttyUSB0
```
and the kernel is
```
Linux LilBull 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

```

The irony is that I can download tracks from the GPS, the problem is only with upload.

Cheers,
Sidd

---

### Post by siddartha on 2007-11-06
I just followed the info on gpsbabel page
[http://www.gpsbabel.org/os/Linux_Hotplug.html]("http://www.gpsbabel.org/os/Linux_Hotplug.html")
and there are no more dmesg messages. Yet, there seems to be no connection from the computer to the Garmin toy and I don't have any route on the list after using the same line as above.

---

### Post by siddartha on 2007-11-06
If I do a
```
gpsbabel -i garmin -f usb: -o gpx -F blah.gpx
```
I do get a 'transfer complete on the GPS and I can examine the results in blah.gpx

---

### Post by siddartha on 2007-11-06
I found QLandkarte, but so far it has no driver for Garmin Lagend CX

---

### Post by siddartha on 2007-11-06
```
gpsbabel -r -i kml -f Route.kml -o garmin -F usb:-1
```
returns
```
0 3332381093 421 eTrex LegendCx Software Version 2.60
```
so the unit is clearly visible.

---

### Post by siddartha on 2007-11-12
Found something interesting:
the garmin_gps kernel module is very good as it is the only help to make the connection under Wine between MapSource and the gps device.
the same garmin_gps should be unloaded for gpsbabel to work, otherwise you get a nice message telling you that device xxx is blocking the communication.

---

### Post by gerkin on 2007-12-21
For Garmin eTrex yellow see my post here: [http://ubuntuforums.org/showthread.php?p=3994981#post3994981](http://ubuntuforums.org/showthread.php?p=3994981#post3994981)

---

