---
title: "Bluetooth Mouse?"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by Doctor J on 2008-05-26
I have a G4 PowerBook that is dual boot OS X and Ubuntu [Feisty until yesterday, now Hardy].  I also use a nice small Macally Bluetooth mouse that is permanently paired with this laptop.  Under Feisty, the mouse was recognized by Ubuntu after i uninstalled bluez-utils.  In Hardy, however, the system won't work with the mouse whether bluez-utils is present or not.  The official HowTo here: [http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673) says to click the connect button on the mouse and run 'sudo hidd --search'.  When i do this i only see: "Searching ..." then nothing else.  Is anybody else having trouble getting Hardy to work with Bluetooth?

---

### Post by stream303 on 2008-05-26
My limited experience with a bluetooth mouse is the same, although after issuing hidd --search, I had to move the mouse and click a number of times before it got recognized while the search was taking place.

---

### Post by Doctor J on 2008-06-02
Okeh, i should have thought of that.

---

### Post by Doctor J on 2008-06-21
This is getting very frustrating.  After much banging my head against various walls, Hardy is still apparently unable to take input from this mouse - which worked fine under Feisty.  "hidd --search" returns "No devices in range or visible", after several attempts at pushing the 'connect' button, rolling the mouse, and/or clicking repeatedly.

I found another page in the wiki [BluetoothInputDevices].  It suggested setting Bluetooth Preferences so that the computer was 'visible', which i did.  More pushing, rolling and clicking ensued, but still no joy.  The amazing thing is that under 'Bonded Devices' i see an entry for it: "MSI Mouse".  At least that's what it is called under OS X.  It is shown as being connected and trusted.  To continue with the preferences, i have the 'input service' running.

In conclusion, it seems like the bluez software is still unable to accomplish really basic functions.  I will also reiterate that the same laptop and same mouse had no problems working together with the Fawn, so apparently something was broken between that release and the Heron.

---

