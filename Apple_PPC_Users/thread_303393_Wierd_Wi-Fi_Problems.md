---
title: "Wierd Wi-Fi Problems"
date: 2006-11-20
forum: Apple PPC Users
---

### Post by applemacmad on 2006-11-20
I have just done a fresh install of Ubuntu 6.10 - and I can't get wireless working. I have had edgy on before and got the wireless working, but I just can't remember how I did it!
I have a Powerbook G4 1.5ghz.
 Thanks for any help

---

### Post by bogoliubov on 2006-11-20
I guess you have the Airport extreme card then..., so try this:

Install the bcm43xx-fwcutter:
sudo apt-get install bcm43xx-fwcutter

Get Airport Extreme firmware here: MAC-OS-HD:/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2 
If you don't have OS X installed, google!

Extract the firmware:
sudo bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o

Reload the module.
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx


ALTERNATIVE:
Firmware-cutter:
[http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)
Compile! Then

./fwcutter AppleAirPort2 
sudo cp *.fw /lib/firmware/ 



Hope it works!

---

### Post by applemacmad on 2006-11-21
Thanks for the help. I have got the fwcutter and the Airport 2, but I am stuck on the next step - I am fairly new to linux!
Could you explain what I need to do next?

---

### Post by bogoliubov on 2006-11-21
> **applemacmad said:**
> Thanks for the help. I have got the fwcutter and the Airport 2, but I am stuck on the next step - I am fairly new to linux!
Could you explain what I need to do next?

Ok, open up a terminal. Go to the folder where you've stored your AppleAirPort2 file, then type
fwcutter AppleAirPort2 

This will create several files. We're interested in the .fw-files.
These we will put in the /lib/firmware folder. This is done by typing
sudo cp *.fw /lib/firmware/

You will be asked for your password. "sudo" means that we perform the commands that follow "sudo" as "superuser" (administrator). That's why we need to type our password.

Now things should hopefully work. You might need to restart some services or your computer (might be easier).
Your settings for the wireless network you whish to connect to can be set up in System-Administration-Network. You can also add a widget in the gnome-panel to control some settings.

Please let me know if it works and if my explanation was clear enough.

Cheers!

---

