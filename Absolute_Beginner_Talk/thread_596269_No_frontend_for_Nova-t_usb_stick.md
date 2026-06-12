---
title: "No frontend for Nova-t usb stick"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by djhig on 2007-10-29
Hi, I'm running feisty and am trying to watch tv with my Nova-T usb stick. I have the newest firmware (dvb-usb-dib0700-03-pre1.fw) and i have kaffeine installed yet my dmesg output is still telling me i have no frontend for the dvb stick:

[   21.524000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   21.524000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   21.524000] DVB: registering new adapter (Hauppauge Nova-T Stick).
[   21.716000] dvb-usb: no frontend was attached by 'Hauppauge Nova-T Stick'
[   21.716000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

How would i go about attaching a frontend to this. Any help would be appreciated

---

### Post by anaconda on 2007-10-29
The only thing that comes to mind is that:
is the stick inserted to a main usb-port?

I have had similar problems with my digiTV when it was connected to USB-divider 
(or whatever it is called.. a box that makes 4 usb ports from 1)

---

### Post by djhig on 2007-10-29
yeah, it's a main usb port. This is really weird as i had it working at home but since i've come to university it stopped working. I haven't made any majorly system altering changes either

---

