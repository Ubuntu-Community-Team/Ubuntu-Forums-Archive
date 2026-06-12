---
title: "Logitech quickcam communicate stx"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by dawna_2001 on 2007-11-14
I recently upgraded from ubuntu 7.04 to 7.10.  I bought a logitech quickcam communicate stx.  I cant get this stupid thing to work!  I tried it on another machine with 7.10 newly installed and it works fine!!!!  I have tried it with and without the gspca driver and no go.  I have also tried the easycam2 and no go.  Can someone please help me?????????????????????????????????????????????????

camera info 
Bus 002 Device 003: ID 046d:08d7 Logitech, Inc. 

I have checked the chart and this particular model is supported..................................:confused:

---

### Post by philinux on 2007-11-14
I had to install this from kanotix

qc-usb-messenger-source_1.1-2_all.deb

Not sure if it works for your cam though mines a quickcam messenger

This might help too for a driver [http://mxhaard.free.fr/](http://mxhaard.free.fr/)

---

### Post by dawna_2001 on 2007-11-14
I have done this as well and no go.....................

---

### Post by philinux on 2007-11-14
Your cam is listed at [http://mxhaard.free.fr/](http://mxhaard.free.fr/) as supported by the gspca driver.

However If i remember I had trouble and I cant remember how I got the link to kanotix. But the deb file did it for me. I'll try to remember how I got the package.

---

### Post by philinux on 2007-11-14
I would try the deb it looks like a universal messenger driver.

[http://mirrors.ecology.uni-kiel.de/debian/kanotix/pool/main/q/qc-usb-messenger/](http://mirrors.ecology.uni-kiel.de/debian/kanotix/pool/main/q/qc-usb-messenger/)

---

### Post by dawna_2001 on 2007-11-14
I just tried this again and no go..................................... It says no /dev/video0 this file doesn't even exhist???????????

---

### Post by philinux on 2007-11-14
With cam plug in and

lsusb does it's power light flicker?

---

### Post by dawna_2001 on 2007-11-14
Yes with the cam plugged in.  The light doesn't flicker at all.

---

### Post by philinux on 2007-11-14
I use Kopete and using it's configure then devices my camera fires up and power light is on.

In this state I just checked in media and there is no video0 entry on my system.

There is a /dev/video0 though.

---

### Post by dawna_2001 on 2007-11-14
My camera doesn't work in kopete or ekiga.

---

### Post by mcurtiss1970 on 2007-12-05
as crazy as this sounds, nothing worked on my quikcam communicate until i did wht this site said:  [http://doc.ubuntu-fr.org/spca5xx?s=gspca](http://doc.ubuntu-fr.org/spca5xx?s=gspca)

even if you don't speak french, follow the inputs into the terminal.  worked for me

---

