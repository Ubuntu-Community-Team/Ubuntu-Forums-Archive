---
title: "USB Skype phone -not recognized?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Nigeyy on 2008-02-04
Well, I'm almost done configuring Ubuntu 7.10.  Just a couple of issues left.....  I have a Dell 1720, and I'm setup for a dual boot with Vista.

The problem I'm having is that after I've installed Skype, I cannot use the USB Skype phone -no sound is coming through, though it is coming through my internal speakers. I'm not sure that Skype (or my OS for that matter) is recognizing the phone.

Anybody else had anything similar, and how they fixed it?

---

### Post by wieman01 on 2008-02-05
I tried a year ago, but Ubuntu does not support Skype phones as far as I know (used a Cisco one). So I am afraid there isn't much we can do.

But check this out...
> sudo lsusb
...and post the results.

---

### Post by Nigeyy on 2008-02-05
Thanks for the reply.  Running lsusb:

[FONT="System"]Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 04b4:0302 Cypress Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0951:1603 Kingston Technology 
Bus 001 Device 001: ID 0000:0000  [/FONT]

The Omnivision is the webcam, the Kingston Tech a usb drive (wanted to make sure that I could see devices on my USB port) -but I'm not sure what the Cypress device is, I assume it's the phone.

fyi, my phone is an EX-03 phone ([http://www.usbphoneworld.com/skypephone/skype-desktop-phone/EX-03.htm](http://www.usbphoneworld.com/skypephone/skype-desktop-phone/EX-03.htm))
Not much on the web about it -tried googling "skype", "EX03", "EX-03" and "ubuntu" but nothing really related came up.

---

