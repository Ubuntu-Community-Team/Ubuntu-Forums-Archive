---
title: "Command Line Device Management"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by _AndY on 2007-04-04
Hey there,
I was wondering if there is any way of disabling a USB device through the command line in Edgy, like devcon.exe in Windows. By a device being disabled I mean for it to be unpowered, as if it were disconnected. I have Googled around a bit and looked through available packages in apt-cache but have only turned up command line network device configuration tools although I'm sure there must be a solution. Hopefully someone out there can help me.

Thanks in advance,
Andy

---

### Post by chalex on 2007-04-04
do you mean "unmount"?  you could do "sudo umount /media/usbwhatever"

I don't think you can turn off power to individual USB ports; it's just +5V DC.

---

### Post by _AndY on 2007-04-05
Hey, 
Thanks for the response. I wasn't referring to unmount, I'm actually trying to use this on a USB mouse. Back on Windows whenever you disable a device in Device Manager or using devcon.exe, the device would actually lose power. I think I'm sort of half way there; I can stop the device from functioning by modifying the file '/sys/devices/pci0000:00/0000:00:0b.0/usb1/1-1/bConfigurationValue' to 0, and then back to 1 again to re-enable, but this doesn't cut the power. I'm pretty sure Linux must be capable of this as I know the hardware is.

Andy

---

### Post by _AndY on 2007-04-06
bump?

---

### Post by bmc6053 on 2007-10-18
I'm actually trying to find out the same thing. I need to completely disable a usb wifi stick and then enable it. The wifi stick wont reconnect after a connection was dropped without it being reset (powered off/on).. which means I have to unplug it and then plug it back in. Of course in windows, the software did this automatically. 

I know there has to be a way to disable a device and then enable it again via the cmd line.

[edit

"hciconfig devicenamehere down" type thing for bluetooth mice I think ^

and "echo "0" > /sys/bus/usb/devices/devicenamehere/power/state" to power off and 1 I think powers on.

/edit]

---

