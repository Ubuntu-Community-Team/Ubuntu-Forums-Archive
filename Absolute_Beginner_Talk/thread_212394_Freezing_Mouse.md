---
title: "Freezing Mouse"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by klesha on 2006-07-09
Dear community!

I have recently installed Ubuntu Dapper on my PIII 733Mhz and so far so good with one exception: My USB mouse cursor will periodically and
temporarily freeze when I'm moving it around, just for a moment, and
then resume its course. It happens frequently enough to be a serious
issue.

Is there anybody outhere who can help me?

Thanks...

---

### Post by richbarna on 2006-07-09
Is it wireless or cable?
Someone else had the same thing with a wireless optical mouse, and solved it by changing the batteries. 

If it's a cable usb optical mouse, try looking underneath and giving the laser a clean.

If it's a plain usb mouse try tacking out the ball and giving the contacts and the ball a clean.

---

### Post by klesha on 2006-07-14
ola barça friend!

thanks for posting..

it is a usb optical mouse (with wire).. i tried to clean it, but the problem remains! 

i am a pure rookie in linux, but i have a feeling that this problem is connected to the graphics configuration... i have an old ati graphic card and i guess i dont have the right drivers installed or something like that...
in windows the mouse works fine...

help needed!!!

---

### Post by jeremy on 2006-07-15
You could try using a USB to PS2 adaptor, that may work better.

---

### Post by klesha on 2006-07-17
The PS2 terminal doesnt´t work in my computer.. that´s why I changed to USB...

Thanks anyway...

---

### Post by klesha on 2006-07-17
by the way, my graphic card is an old ati 3d rage IIc AGP, with 8mb... i think the problem may come from here...

---

### Post by MaximB on 2006-07-17
I have the same problem 
my mouse is optical BUT with no USB.
and no battaries. - GPT
you know - like a ragular mouse but optical.
what am I to do ?

---

### Post by Dominus Suus on 2006-10-22
This topic may long since be dead and solved, but I've been having a problem on my Acer laptop (Intel chipsets).  I ran 'dmesg | grep usb' and it was full of lines looking like this:

[17184258.664000] usb 2-2: USB disconnect, address 85
[17184260.724000] usb 2-2: new low speed USB device using uhci_hcd and address 8 6
[17184260.892000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1 -2

(where the first address value was an increased in each entry).  When I had this problem in Windows with my old mouse, it was because the cord was loose and the mouse lost power.  During my mouse freezes, though, the mouse is still powered.  It's almost like the USB drivers are resetting every few minutes or something...

---

### Post by cendant on 2006-10-27
well, my mouse is optical and PS/2

It worked fine in Dapper, but in Edgy it does freeze for a brief moment.

It happens sometimes, but ennoying a lot

Any ideas?

---

