---
title: "nivida X server settings gone after reboot"
date: 2009-05-20
forum: Apple Hardware Users
---

### Post by larslarsson on 2009-05-20
Hi,

I'm running Intrepid on a MacBook 5,1 (off of a USB stick). After a reboot I go to System->Administration->NVIDIA X Server Settings and get "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig'....". So I do that and restart the X server by doing a Logout. When I login again everything is fine.
BUT: then I reboot the system and I have the same problem again. Does a reboot change the X server settings (in another way than a Logout+Login)?

(Note: when running nvidia-xconfig, I get VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.
)

Thanks for any help!

---

### Post by cyberdork33 on 2009-05-20
xorg should be able to autodetect the driver to use, but it sounds like it is having trouble when you reboot for some reason.

add to your /etc/X11/xorg.conf
```
Driver    "nvidia"
```
in the Device section.

---

### Post by larslarsson on 2009-05-22
Thanks for your reply, but I had Driver "nvidia" there.
Must be something to do with the reboot, because it "survives" an X server restart (logout/login).

Lars

---

### Post by larslarsson on 2009-05-22
Correction:
The line Driver "nvidia" is NOT in the /etc/X11/xorg.conf after reboot.
What can alter the xorg.conf file at reboot?

Lars

---

### Post by larslarsson on 2009-05-24
Found out what the problem was: xorg.conf not persisted when running off of a USB stick.
Solution is here: [http://ubuntuforums.org/showpost.php?p=6089763&postcount=8](http://ubuntuforums.org/showpost.php?p=6089763&postcount=8)

---

