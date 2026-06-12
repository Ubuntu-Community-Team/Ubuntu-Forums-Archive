---
title: "Bluetooth Keyboard Mouse"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by Houli on 2008-09-03
Hey I have an Apple Wireless Keyboard and a Wireless Mouse how do I get these working with the live cd so i can install? I have a usb mouse that I can use but no keyboard and pairing with the utility isn't working.

---

### Post by cyberdork33 on 2008-09-03
> **Houli said:**
> Hey I have an Apple Wireless Keyboard and a Wireless Mouse how do I get these working with the live cd so i can install? I have a usb mouse that I can use but no keyboard and pairing with the utility isn't working.
you need a usb keyboard unfortunately to get your wireless keyboard to work.

---

### Post by Houli on 2008-09-04
I can use on screen keyboard? So what do I do to connect them?

---

### Post by cyberdork33 on 2008-09-04
> **Houli said:**
> I can use on screen keyboard? So what do I do to connect them?
I guess if you can get logged in, then yes... 
Someone recently posted this blog post that explains very well how to set your bluetooth keyboard and mouse properly.
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

---

### Post by hajk on 2008-09-04
That very useful blog describes a little trick to enter the pairing code via the Bluetooth keyboard... worth a try. 

The other problem seems to be that you can't reboot your GNU/Linux session without first shutting down the computer. The reason is that your BT keyboard needs to operate in USB-HID mode for it to be used during login, the Apple firmware does that after a complete shutdown. A future Linux kernel may do that reset, but current kernels don't.

---

### Post by Doctor J. on 2008-09-13
Am i reading this correctly?  It looks like we need to tell OS X to unpair the device before using it in Ubuntu??

---

### Post by cyberdork33 on 2008-09-13
> **Doctor J. said:**
> Am i reading this correctly?  It looks like we need to tell OS X to unpair the device before using it in Ubuntu??
no
I use it in both just fine.

---

### Post by hajk on 2008-09-14
> **Doctor J. said:**
> Am i reading this correctly?  It looks like we need to tell OS X to unpair the device before using it in Ubuntu??
This must be a mistake in that blog (there are a few others as well); I have paired my BT mouse in GNU/Linux without first unpairing it in Mac OS X.

---

### Post by Houli on 2009-01-16
Sorry to have to reply to such an outdated post but I still haven't been able to get Ubuntu wireless keyboard working. Has the situation improved since 8.04? I really need Ubuntu on my Mac. I wish I had have gotten the USB keyboard now :(

---

### Post by cyberdork33 on 2009-01-16
> **Houli said:**
> Sorry to have to reply to such an outdated post but I still haven't been able to get Ubuntu wireless keyboard working. Has the situation improved since 8.04? I really need Ubuntu on my Mac. I wish I had have gotten the USB keyboard now :(
you are going to need a USB keyboard for the install anyway... If you have an extra keyboard and you want to try it out, download one of the new alphas of Jaunty, boot it up and see if you can pair your bluetooth device.

---

