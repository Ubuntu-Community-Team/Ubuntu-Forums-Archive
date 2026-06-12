---
title: "Stuck with 1215n and Optimus"
date: 2011-08-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by daemon.d on 2011-08-06
Hi!

I recently installed Ubuntu 11.04 and that was were the fun (sarcasm) part begun. As you know, 1215n has the nVidia Optimus technology for switching between onboard GPU's - and now I'm completely stuck with trying to make run Linux on this comp well.
So, here is what I did (step by step):

1. Fresh install. 
2. What I wanted to do a) run Unity (it doesn't work with Intel gpu, which is on by default) b) be able to run some apps using the ION GPU.
3. What I did: 
a) uninstalled nvida's proprietary drivers
b) blacklisted nouveau drivers in /etc/modprobe.d/blacklist.conf
c) ran update-initramfs -u
d) installed Bumblebee and Bumblebee UI
e) configured Bumblebee with one of the available pre-set configurations

So far it was ok, I was able to optirun glxspheres, the nvidia card turned on and off. Then I rebooted. What I got was Unity running perfectly fine, but when I try to execute optirun glxspheres it returns this:

einars@brutalizer:~$ optirun glxspheres
Polygons in scene: 62464
 * Stopping Bumblebee X server bumblebee                                 [fail] 
ERROR: Module nvidia does not exist in /proc/modules
FATAL: Module acpi_call not found.
Error: acpi_call module not loaded

I tried to reinstall bumblebee, but nothing. I'm stuck and this point. Unity runs, but no other apps can use the ION. I know, that I'm doing something wrong, but I can't figure out what. I already did three complete reinstalls before making it work and I'm becoming tired of this. If someone has any advice or knows how to sort this (or at least give me a hint what to do next) I'll be happy to hear.

---

### Post by BicyclerBoy on 2011-08-13
Was interested in buying one of these because of the newer atom & lower power chipset.

Surely you need the nvidia proprietary driver installed.
Your error message is basically reporting this.
 
Without nvidia or nouveau drivers you got nothing left but vesa & Xfree86?

---

### Post by AmiNimA on 2011-08-27
just do not uninstall the nvidia drivers from your fresh install.

---

### Post by BicyclerBoy on 2011-08-27
Do you mean you have to setup Bumblebee & the intel driver first before installing the nvidia driver ?

---

### Post by AmiNimA on 2011-09-10
I found a way to manually disable / enable the nvidia cards using some scrpits I fount over the internet.

1- first install acpi_call from the attachments.
2- black list the nouveau as you know above.

3- install nvidia-kernel-common and nvidia-kernel,dkms from package manager.
4- do a reboot!

5- download disablecard, enablecard and nvidiastatus scripts.
6- run disablecard script with sudo and check the status with nvidiastatus.

now you must have a switched off nvidia card on your 1215n.
to turn it on, run enable script. but I get this error: 
FATAL: Error inserting nvidia (/lib/modules/2.6.37-6/updates/dkms/nvidia.ko): No such device

any idea to solve that?

---

