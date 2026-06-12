---
title: "command to disable a usb port?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-09-30
Is there a way to disable a usb port such that it provides 5V but does not enumerate?  I mean a software way in ubuntu command line or menu option!  Thanks!!

---

### Post by jfinkels on 2007-10-02
> **outer_space said:**
> Is there a way to disable a usb port such that it provides 5V but does not enumerate?  I mean a software way in ubuntu command line or menu option!  Thanks!!

I don't really know what 'enumerate' means in this context, but maybe you could try changing the permissions of the USB device in /dev/ in some way?

---

### Post by NovaAesa on 2007-10-02
I think outer_space means he/she wants to set up a USB port such that it only provides power without a datastream signal. Right?

I'm not sure how to do this as a software way but maybe is could be done by only having the voltages wired connected at the port.

---

