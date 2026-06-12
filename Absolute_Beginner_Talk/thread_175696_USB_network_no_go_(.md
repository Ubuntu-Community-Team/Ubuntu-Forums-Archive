---
title: "USB network no go? :("
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by HeDanny on 2006-05-13
I have just re-installed windows because Despite my best efforts (which mostly consisted of typing "USB network" into search) I could not get the USB network connection working.  I have [This modem](http://www.netcomm.com.au/ADSL/NB1300PLUS4.php) if that helps at all.  The PC which I want to run ubuntu is connected to it via the USB plug and not the 4 ethernet ports, as those ports are already taken by other PCs elsewhere in the house, none of which would be practical to swap due to several reasons.

Is this possible? or am I going to be out of luck?  I am quite motivated to make the switch to ubuntu, but networking will be the first thing I will need working.

---

### Post by Jussi Kukkonen on 2006-05-13
I believe there is no standard ethernet-over-usb (which is why they offer driver downloads, but only for Windows and Mac), so this might be impossible... More info here: [http://www.linux-usb.org/usbnet/index.html](http://www.linux-usb.org/usbnet/index.html)

There's no harm in trying though, it might Just Work. If it doesn't, please run
```
sudo tail -f /var/log/messages
```
in a terminal, then plug in the usb-cord. Copy whatever gets printed, and paste it here.

Of course, the easiest solution is probably buying a switch, they're not expensive...

---

