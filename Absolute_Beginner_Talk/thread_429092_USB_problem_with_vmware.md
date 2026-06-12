---
title: "USB problem with vmware"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by 71CH on 2007-04-30
Hello
Can somebody please tell me how I can get my vmware player to recognize an usb flash drive and an external hard drive.  I am running XP home in the vmware player.  Thank you.

---

### Post by oilchangeguy on 2007-04-30
treat a virtual machine just as you would a normal computer. from windows, right click my computer, properties, device manager. is the usb controller present?

---

### Post by 71CH on 2007-04-30
yes it is

---

### Post by oilchangeguy on 2007-04-30
when you installed these items did the found new hardware wizard start?

---

### Post by 71CH on 2007-04-30
no it did not

---

### Post by oilchangeguy on 2007-04-30
did you install them with windows running, or shutdown? (normally won't make any difference).

---

### Post by AscendedDaniel on 2007-04-30
Does the device appear in VM > Removable Devices > USB devices (or something similar, I can't remember)?

Usually you can virtually unplug a usb device from the host and plug it into the vm using the above menu path. Additionally, if the device is plugged in while the vm has focus, it should be plugged into the vm automatically, but it doesn't always happen. 

Hope this helps.

---

### Post by delphiguy on 2007-04-30
I had the same problem with VMWare, but I happen to find a workaround.
Hopefully someone can give a more better answer.

Before booting up your VM, plug in your USB Device.
After the USB Device is plugged in and recognized by the system (Ubuntu), 
you can now boot your VM.

After that you can now see your USB Device, in your VM's Removable device.

This is how I make my USB Devices under XP in VM.

Hopefully this will also work for you.

---

### Post by 71CH on 2007-05-01
Thanks for your replies guys.  I got it working :)

I did have a few other questions that are OT.  I currently have vmware configured with 10 gigs.  Can I increase or decrease this?  I have the same question for RAM as well.  Also, do I need to shut down XP everytime I'm done with vmware or can I just shut down vmware.  Lastly, is the RAM that I allocated to vmware only used when vmware is open or do I pretty much lose that RAM even when I don't have vmware open.  Thanks guys. :P

---

### Post by 71CH on 2007-05-01
bump bump bump

---

