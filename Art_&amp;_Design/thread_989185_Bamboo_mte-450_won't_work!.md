---
title: "Bamboo mte-450 won't work!"
date: 2008-11-21
forum: Art &amp; Design
---

### Post by olskar on 2008-11-21
Hi,

My Bamboo mte-450 won't work.. 

I have tried both A) and B) at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) but it does not help.

I would be very glad if someone told me how to get it working with GIMP

---

### Post by olskar on 2008-11-22
This is what I see in dmesg:

[19305.744045] usb 1-6: new full speed USB device using ohci_hcd and address 4
[19305.966605] usb 1-6: configuration #1 chosen from 1 choice
[19306.131694] input: Wacom Bamboo as /devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.0/input/input6
[19306.179606] usbcore: registered new interface driver wacom
[19306.181848] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

---

### Post by olskar on 2008-11-26
Can someone with a similar wacom please check what their dmesg say?

---

### Post by shyft on 2008-11-28
My dmesg says the same for the most part. (different usb ports i imagine)

What troubles me is that it was working fine with default settings noon today.

Then, as i was working on a program that i had written in Processing, the program crashed and i have not been able to get it working the way that it was before (plain-jane stylus nothing special).

The information at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) did allow me to get some functionality out of it by modifying my xorg.conf, 

BUT... the eraser was the only part that would act as a pointing device

I could not find a way to flip them or dereference the eraser in xorg AND have the xserver start properly. so i have no uber-custom xorg.conf to post. That is to say that i followed the directions on the page to a "T".

If i were a more tolerant person, I would be grateful that I regained that much functionality, but I am not... holding the pen upside down infuriates me... no joke...

the project that i am working on requires me to connect the laptop to a projector and thus dick with the nvidia-display settings in System->Admin

I repeat; it was working before my application crashed.

My application is simple. isnt dicking around with files or anything...

press and hold the mouse button and it draws a line from point a to point b... simple...

any way, I am at a loss as to what to do. 

theres always a format reinstall... but really... i thought linux was above that.

hopefully, someone has some help for the fellow above and myself.

oh btw, in case you were wondering system is as follows:
FRESH INSTALL OF IBEX  /w updates (1 day old at time of writing)
3gb ram
core2duo 2ghz t5750


thanks,
-shyft

---

### Post by olskar on 2008-11-30
So you mean its working for you (or worked) without making any settings in Intrepid?

---

