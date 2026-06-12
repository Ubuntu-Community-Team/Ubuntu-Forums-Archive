---
title: "Bluetooth Might Mouse"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by applemacmad on 2006-10-04
Hi, I have just installed Ubuntu 6.10, a daily build from October the 3rd.
I have a bluetooth Mighty Mouse and I was wandering if there is a way to get it working (single or multi button) at all?
Thanks

---

### Post by eidex on 2006-10-05
i did this to connect the (old) onebutton bluetooth mouse:

1.) open a terminal and enter
```
 sudo hidd --search
``` and open the lid of your mouse (or switch it on, i've never seen the bt mighty mouse)
wait a few seconds, if it connects, everything is fine, but you have to do this every time you start gnome
2.) on gdm the mouse worked without any tweaks but when you start gnome it stops working, i found a solution in an old thread which suggested to remove all bluez* packages ```
sudo aptitude remove bluez*
```, which worked fine for me but might be a problem if you use other bluetooth devices

---

### Post by munchbach on 2006-10-07
> **applemacmad said:**
> Hi, I have just installed Ubuntu 6.10, a daily build from October the 3rd.
I have a bluetooth Mighty Mouse and I was wandering if there is a way to get it working (single or multi button) at all?
Thanks

The BT Might Mouse will just work.  Left and right clicking are recognized out of the gate, scrolling works fine.  I can't seem to get mine to connect at startup but typing:

```
sudo hidd --search
```

in a terminal at starup works.

Cheers,
Andrew

---

### Post by bersace on 2006-10-11
Hello,

I have the same problem. but i got this error :

root@thilivren:~# hidd --search
Searching ...
        Connecting to device 00:14:51:C2:7F:5E
Can't create HID control channel: Connection refused
root@thilivren:~# 

I don't know how to sync pair with the mouse.

---

### Post by bersace on 2006-10-11
I paired the mouse with OS X and it works quite nice. I try to pair the mouse with Ubuntu. In installed the gnome passkey agent. It ask me for a pin, but i don't know which pin to set !

How to know which pin is needed ?

---

### Post by munchbach on 2006-10-11
Typically a mouse is "0000".

Cheers

---

### Post by bersace on 2006-10-11
Hi,

Thanks, 0000 is the right pin. But i have to restart bluetooth service in order to get it connected :| How to get it autoconnected ?

Thanks

---

