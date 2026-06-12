---
title: "Missing Driver"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by PantheraPardus on 2008-03-24
I can't get my UMAX DC AstraPix 380 webcam to work.
The drivers that come with it don't indicate support for linux, and once plugged Ubuntu recognized some other camera that, obviously, didn't work.
THX.

---

### Post by linuxwizard on 2008-03-24
Have you just tried using your webcam with any apps. to see if it would work ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. 
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing.
If that does not work post the results of the commamd > lsusb

---

### Post by PantheraPardus on 2008-03-24
It won't work...

Here it is:

```

Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0d64:1021 DXG Technology Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

```

---

### Post by linuxwizard on 2008-03-24
I have searched everywhere I can think of trying to find your webcam > Bus 003 Device 002: ID 0d64:1021 DXG Technology Corp. > no listings anywhere to see which driver you may need. Not sure what else to say but looks like no driver for linux. Maybe someone else will make a suggestion or offer some input. Good Luck

---

### Post by Shazaam on 2008-03-24
+1 for no drivers. UMAX or DXG Technology.  :( You can try installing the drivers in Wine but you may be out of luck.

Look here......
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

