---
title: "64 bit nvidia drivers in feisty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by theovercoat on 2007-04-19
the card is a 7900gs
i have downloaded the newest 64 bit driver from nvidia website onto my desktop
i have enabled writing
install method:

sudo /etc/init.d/gdm stop

alt+f1  (login)

sudo sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

here is where i must cross the bridge..

in edgy package would then compile the kernel and i could startx without reboot and remove common kernel and enjoy a succesful install.  

in feisty the package isnt found.  

is there a repo with the 64 bit 9755 or an alternative method?

i am from windows xp mass exodus

---

### Post by Fangs404 on 2007-04-19
I'm still at work and haven't been able to update to Feisty yet, but [http://www.getautomatix.com/](http://www.getautomatix.com/) should install them for you.

---

### Post by theovercoat on 2007-04-19
used automatix, rebooted, unable to use gui/gnome because of you know what.

let feisty reinstall while i grabbed some beer from grocery store.

disabled restricted driver, reinstalled automatix, reinstalled 64 bit 9755 driver through automatix, reboot, no errors.

could someone please point to HOWTO for using 64bit nvidia driver installer in feisty?  the HOWTO i DID see seemed based on too many workarounds.  too many workarounds = ubuntu noob second=guessing

thank you for the automatix recommend.   though not manual, a necessary step to continue venturing.

---

### Post by Fangs404 on 2007-04-20
> **theovercoat said:**
> used automatix, rebooted, unable to use gui/gnome because of you know what.

let feisty reinstall while i grabbed some beer from grocery store.

disabled restricted driver, reinstalled automatix, reinstalled 64 bit 9755 driver through automatix, reboot, no errors.

could someone please point to HOWTO for using 64bit nvidia driver installer in feisty?  the HOWTO i DID see seemed based on too many workarounds.  too many workarounds = ubuntu noob second=guessing

thank you for the automatix recommend.   though not manual, a necessary step to continue venturing.

Alright, I got Feisty installed tonight (64-bit), and I wound up using Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) to install my drivers.  It worked perfectly.  You'll want to uninstall whatever Automatix2 installed, and you'll want to make sure the NVIDIA drivers aren't enabled under the Restricted Driver Manager.

---

### Post by rsambuca on 2007-04-20
I always find that the easiest way to install the nvidia drivers is just to make sure you have the linux-restricted-modules installed for your kernel (use Synaptic for this).

Then just 

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

---

