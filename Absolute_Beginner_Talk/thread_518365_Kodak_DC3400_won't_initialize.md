---
title: "Kodak DC3400 won't initialize"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by theonlyrealperson on 2007-08-05
Hey all, I'm using Ubuntu Feisty and I'm trying to connect my ancient Kodak DC3400 to get some photos off of it. When I connect the camera to the computer, I get an "Import Photos" message but when I click on it nothing happens. I've tried digikam and gtkam and both see the camera but can't initialize it. When I connect the camera, I get this from dmesg | tail:

```
[99921.556000] usb 4-4.1: USB disconnect, address 16
[100235.604000] usb 4-4.1: new full speed USB device using ehci_hcd and address 17
[100235.696000] usb 4-4.1: configuration #1 chosen from 1 choice
[100238.732000] usb 4-4.1: USB disconnect, address 17
[100436.812000] usb 4-4.1: new full speed USB device using ehci_hcd and address 18
[100436.904000] usb 4-4.1: configuration #1 chosen from 1 choice
[100903.804000] usb 4-4.1: USB disconnect, address 18
[100907.588000] usb 4-4.1: new full speed USB device using ehci_hcd and address 19
[100907.680000] usb 4-4.1: configuration #1 chosen from 1 choice

```

Any ideas?

---

### Post by theonlyrealperson on 2007-08-05
**bump, hoping someone has some info***

---

### Post by overdrank on 2007-08-05
Hi I did a quick search ( as I assume you have to) there is not much info to help. 
[http://ubuntuforums.org/showthread.php?t=53185&highlight=Kodak+DC3400](http://ubuntuforums.org/showthread.php?t=53185&highlight=Kodak+DC3400)

:(

---

### Post by theonlyrealperson on 2007-08-05
Yeah, I had seen that one - he had a different problem. I can't even see the photos on the camera.

A Google search faired little better, I got conflicting advice. One site told me to build and load the DC2xx kernel module, the other said the module was there and I needed to take it out because it conflicted with my camera.

Both of the pieces of advice came from Mandrake users...

---

### Post by overdrank on 2007-08-05
> **theonlyrealperson said:**
> Yeah, I had seen that one - he had a different problem. I can't even see the photos on the camera.

A Google search faired little better, I got conflicting advice. One site told me to build and load the DC2xx kernel module, the other said the module was there and I needed to take it out because it conflicted with my camera.

Both of the pieces of advice came from Mandrake users...

Yea to bad, I cant remember if that camera uses a memory card or not but if it does them maybe a card reader would do the trick. Good luck!

---

