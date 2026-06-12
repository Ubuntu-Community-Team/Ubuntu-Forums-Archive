---
title: "Keyboard failure after MacBook Pro updates"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by andrewenoble on 2009-05-10
Immediately after a successfully upgrade from 8.10 to 9.04, I carefully stepped through the configurations for a MacBook Pro 5,1 listed here: [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty)

(I followed the instructions in the following sections:  Package support for intel macs, Sensors (temps & fans), Video and effects (compiz), touchpad (bcm5974), and Sound.)

Upon reboot, my keyboard does not work:  I cannot type my user name at the first login prompt, although the trackpad, sure enough, has been updated to allow for tap-clicks, as I had specified in the .fdi file.

Is there anyway to recover my keyboard functionality without a full reinstall (starting from an 8.10 DVD in my case)?

Any help would be very much appreciated.

Thank you!
Andrew

---

### Post by xfile087 on 2009-05-10
I myself did a clean install last week and it was all working fine, I installed updates and rebooted into Mac OS X. Today when booting Ubuntu again I have the exact same issue :confused:

---

### Post by inphektion on 2009-05-10
are you sure in /etc/modules you added:
bcm5974
usbhid

usbhid needs to be second.

---

### Post by andrewenoble on 2009-05-10
Yes, I believe I did follow those instructions (and the proper ordering).  But is there a way for me to check the contents of that file if the keyboard is disabled at the login prompt?

Thanks.

---

### Post by inphektion on 2009-05-10
see if a usb keyboard works.

---

### Post by Salohcin on 2009-05-11
Same thing happened for me when i copied the fdi file for the synaptics off of the mactel documentation site. I had to boot into console to remove and then go looking to see where the fault was. I found some bug reports that seemed to follow the same problem, and they had an alternate fdi attached.

Don't know exactly how relevant any of this is to you, but if it helps, i'll attach the file im using now.  Just rename and place in /etc/hal/fdi/policy/.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935")

---

### Post by andrewenoble on 2009-05-11
inphektion- I don't have immediate access to a USB keyboard, but if all else fails, I'll certainly go looking for one.

Salohcin- Could you give me some details on how you managed to delete that fdi file?  At the beginning of the boot, I pressed 'ESC' to enter console mode.  When I selected 'restore' mode, the keyboard was still frozen.  When I entered the command line, I couldn't see a way to access my files.  

Thanks again for your help.

---

### Post by inphektion on 2009-05-11
The difference in the wiki's .fdi file and the one you posted is just palmdetect and fasttaps.  Neither of those would have anything to do with the keyboard not working.  

There was something else that went wrong in your case and it has nothing to do with the .fdi file.

---

### Post by andrewenoble on 2009-05-12
inphektion- You were right!  I was careless in not ordering things properly in the modules file.  I made the fix by booting up from my 8.10 DVD.  

Thanks you!!!

---

### Post by inphektion on 2009-05-12
glad you got it.  and glad i was right, was just guessing.

---

