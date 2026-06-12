---
title: "Bluetooth USB dongle in feisty"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by PPPP on 2007-09-16
I have an unknown brand USB bluetooth dongle.  I've googled for a while for tutorials to get this setup.  I followed some steps but I couldn't get it to work. 

```

$ lsusb 
Bus 002 Device 008: ID 08ec:0016 M-Systems Flash Disk Pioneers 
Bus 002 Device 002: ID 0424:a700 Standard Microsystems Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
Bus 001 Device 003: ID 045e:002d Microsoft Corp. 
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

```

As you can see above, it recognizes it.  However...

```

$ hcitool dev
Devices:


```

I would get an empty devices list.  Can anyone help me to get this setup?  Ultimately, I would like to have it to transfer files between my SEw810i.  I believe I have all the bluetooth packages installed.

---

### Post by High Camp on 2007-09-16
I recently plugged my USB Bluetooth dongle in. I hadn't before because I didn't expect it to work but it worked right away (it just works). It's a Logitech so that might make a difference. All I had to do is hit the connect button and then the connect button on my mouse and keyboard.

Not sure if that actually helps,

EDIT: Maybe try rebooting with the dongle plugged in to make sure it's recognized and the correct drivers are loaded.

---

### Post by PPPP on 2007-09-17
I actually had the dongle plugged in since the install and I've also tried to unplug and plug it back in.

How do I know if I have the correct driver loaded?  I would guess I don't at the moment.  And how would I load the correct one?

---

