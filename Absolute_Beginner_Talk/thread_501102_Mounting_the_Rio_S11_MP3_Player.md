---
title: "Mounting the Rio S11 MP3 Player"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-07-14
I have old, reliable Rio S11 mp3 player that I'd like to use with Feisty Fawn but I have no idea how to access it. When I turn on the player I expected it to be recognized in the file system but nothing happens. I suspect I can make some kind of fstab entry, but I have no clue as to what to add. Help is appreciated!

---

### Post by Sleestack on 2007-07-15
OK, since I have gotten any replies maybe I need to be a bit more general. How do you mount a USB device that's not recognized? I understand maybe the device name needs to be used, how is that determined if the dvice is not recognized?

---

### Post by Pragmatist on 2007-07-15
Try this:
First unplug the device and type this:
```
tail -f /var/log/messages
```

Now plug in the device and watch the terminal for new messages.  Do see anything that resembles a /dev file (such as sda, sdb...sdf )

---

### Post by Sleestack on 2007-07-15
Thank you. I did as you suggested and got this result: 

Jul 15 12:11:15 delld800 kernel: [ 4069.548000] usb 2-2: new full speed USB device using uhci_hcd and address 7
Jul 15 12:11:15 delld800 kernel: [ 4069.764000] usb 2-2: configuration #1 chosen from 1 choice

---

### Post by Pragmatist on 2007-07-15
Try to turn the device on.  If it is already on, then turn it off and on again.  Do all of this with this command running **tail -f /var/log/messages**

---

### Post by Sleestack on 2007-07-15
OK, this is the full text of the result: 
Jul 15 12:22:34 delld800 kernel: [ 4748.940000] usb 2-2: new full speed USB device using uhci_hcd and address 8
Jul 15 12:22:34 delld800 kernel: [ 4749.100000] usb 2-2: configuration #1 chosen from 1 choice
Jul 15 12:22:46 delld800 kernel: [ 4760.552000] usb 2-2: USB disconnect, address 8

Does this give me any information I can use to mount the device?

---

### Post by Pragmatist on 2007-07-15
Please give me the complete name of your device.  I am not finding anything for Rio S11   I don't even find anywhere I can buy such a model, so there must be more information on the model.  Is it an old model or new one (when did you buy it)?  What is its capacity (5GB, 256MB, etc...)?  Does it have a hard drive or a flash drive ?

---

### Post by Sleestack on 2007-07-16
It's an old model but it does the trick :-) It's a Rio S11 by Sonic Blue, very close to the S10 except it accepts a SanDisk card up to 512MB. It's probably about 3 years old. I'm assuming from your reply there's a universal system name or ID for the device the kernel needs to reference?

---

### Post by Pragmatist on 2007-07-16
after you plug in the device, type this and post the output here:
```
ls -l /dev/sd*
```

---

