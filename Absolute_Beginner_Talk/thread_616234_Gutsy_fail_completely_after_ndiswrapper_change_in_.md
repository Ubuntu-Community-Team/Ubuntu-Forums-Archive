---
title: "Gutsy fail completely after ndiswrapper change in alsa-base"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by devilhan on 2007-11-18
Gutsy was fine until I did these couple things
1. blacklist ipw2200, ipw2100
2. use ndiswrapper to install driver windows driver for intel 2200BG wireless card.
3. add entries in /etc/modprobe.d/alsa-base to use ndiswrapper for the wireless card.

After rebooting, both normal mode, recovery mode throws me into an infinite loop with repeattting message like this:
bug scheduling while atomic............................

Can anyone please help me and tell me how I can go about fix this?  I just need to be able to modify the /etc/modprobe.d/alsa-base file but it never gives me the chance to bring up a command line with enough permission to do so.
Thanks in advance for your help.

---

### Post by MaximusTG on 2007-11-21
You need to boot the live-cd, and then mount the drive you have installed ubuntu on.

You should open a terminal on your live cd, and then type

sudo mkdir ubunturoot
sudo mount /dev/hdax ubunturoot 

where /dev/hdax stands for the drive you installed ubuntu on. (could be /dev/sda1 or /dev/hda3 etc)

Then you can edit the /etc/modprobe.d/alsa-base file, it is located in the directory ubunturoot you just created (ubunturoot/etc/modprobe.d/alsa-base).
Remove the entries you added and reboot into your installed ubuntu.

Then you can install ndiswrapper. The location to add modules that you want loaded at boot is /etc/modules and not /etc/modprobe.d/alsa-base (that one is for the configuration of the sound driver)
BTW, why do you want to install ndiswrapper? I thought intel wireless cards had great linux driver support?

---

### Post by daimaru on 2007-11-21
> **MaximusTG said:**
> BTW, why do you want to install ndiswrapper? I thought intel wireless cards had great linux driver support?

exactly just enable your intel wireless in the restricted driver manager .. worked for me.

---

