---
title: "[SOLVED] Used ndiswrapper for WUSB11v2.6, still using old driver???"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2007-12-28
Very noobish here...

I ran ndiswrapper for my Linksys WUSB11v2.6.  Everything appeared to run smoothly, but when I tried ndiswrapper -l, I got the following:
```
netusb : driver installed
        device (077B:2219) present (alternate driver: at76_usb)
```

Why is it still using the default driver, and how can I get it to use the netusb driver?

---

### Post by RomeReactor on 2007-12-28
Hi. You can uninstall the one you don't want from the terminal:
```
sudo ndiswrapper -r at76_usb
```

---

### Post by cifdtruckie on 2007-12-28
> **RomeReactor said:**
> Hi. You can uninstall the one you don't want from the terminal:
```
sudo ndiswrapper -r at76_usb
```

Thanks!!  Will there be anything else I have to do to get it to use the netusb driver, or will it work right away when I uninstall the bad driver?

---

### Post by RomeReactor on 2007-12-28
I don't think there's anything else to do; once you remove the unwanted driver, try:
```
ndiswrapper -l
```
again just to make sure it was removed.

---

### Post by cifdtruckie on 2007-12-28
Didn't seem to work...

```
chris@chris-desktop:~$ sudo ndiswrapper -r at76_usb
[sudo] password for chris:
couldn't delete /etc/ndiswrapper/at76_usb: No such file or directory
chris@chris-desktop:~$ 

```

I really appreciate you helping me out with this!

---

### Post by RomeReactor on 2007-12-28
Just found out that the **at76_usb** driver comes with Ubuntu; you need to blacklist it:
```
gksudo gedit /etc/modprobe.d/blacklist
```
Once it opens, add the following at the end of the file:
```
blacklist at76_us
```
Save the file, close the text editor, and reboot.

---

### Post by cifdtruckie on 2007-12-29
Tried that... (I figured that you meant at_76usb).  Still didn't work - got the same message when I tried ndiswrapper -l again.  Oddly enough, I'm still able to get online, though according the network manager I'm not connected to the network...

---

### Post by RomeReactor on 2007-12-29
Make sure you don't have an ethernet cable plugged in now; it may be that Ubuntu is using it to connect to the internet. Other than that, some drivers with ndiswrapper don't provide you with the same functionality as in windows, so it may be that it is correctly connected to the internet using your wireless USB, but doesn't report it.

---

### Post by cifdtruckie on 2007-12-29
Great - thanks for all of your help!! \\:D/

---

