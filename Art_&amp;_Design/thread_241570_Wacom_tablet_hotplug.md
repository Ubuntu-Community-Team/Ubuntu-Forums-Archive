---
title: "Wacom tablet hotplug"
date: 2006-08-22
forum: Art &amp; Design
---

### Post by firenewt on 2006-08-22
I'm not sure how the hotplug for the wacom tablet is set up, but could somebody tell me how to turn it off to how it was before? When you re-plug, it changes event number which makes the settings in xorg.conf useless. Then you have to go back and edit it to make it work right again. Then the event number may change again by itself after some reboot. How can I disable hotplug to how it was before in ubuntu? Or can I freeze the event number to stop it from changing like this?

---

### Post by daller on 2006-08-22
Follow this howto, and give some feedback:

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

...You need some udev-rules to assign a static eventfor your device...

If that howto didn't help you, try the "Setting up udev (If the tablet is USB)" part (and ONLY that part) from my howto:

[https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen)

---

### Post by firenewt on 2006-08-23
[COLOR="Sienna"][FONT="Palatino Linotype"][SIZE="5"]Thank you. The wiki on the wizard pen also gave me the hint to place the udev rules for this tablet but it was a different set. I got it from the linuxwacom site. Now at least there is no need to re-edit xorg.conf when the tablet is re-plugged. Just the same old way of restarting X will fix it right up. I don't know if there is way to get it to hotplug with settings and all, but I couldn't figure out how. If someone has more info on that please explain. If not this is enough for now.[/SIZE][/FONT][/COLOR]

---

