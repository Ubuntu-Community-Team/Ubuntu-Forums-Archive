---
title: "Install on Macbook Pro without DVD drive"
date: 2010-04-11
forum: Apple Hardware Users
---

### Post by aderowbotham on 2010-04-11
I have a Macbook Pro with a b0rked DVD drive, and want to install Ubuntu on it.

I have followed the instructions here: [https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Mac](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Mac)

But when rebooting and holding ALT, I don't get the option of booting from USB.

Possibly related, when I view the USB drive in Disk Utility it's marked as "Bootable: no" :
[IMG]http://home.adeweb.co.uk/png/ubuntu-usb.png[/IMG]

Any ideas? I've tried this with two different USB sticks.


I've also burned a Ubuntu install disk from the original ISO, loaded it into another mac and started that mac in Target Disk Mode. Then I connected them with Firewire, rebooted the mac *without* the disc drive, held ALT and chose the shared disc as the boot device. Though weirdly it was named "Windows". Sadly, I then got a message on a black background saying it was not a bootable device.

Any ideas ?? Just wanna get Ubuntu onto this Mo' Fo' !

---

### Post by linuxopjemac on 2010-04-11
Maybe [this]("http://mac.linux.be/content/how-create-ubuntu-live-usb-both-mac-and-pc") or [this]("http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick") will help you.

---

### Post by aderowbotham on 2010-04-11
Hi. Thanks for that.

However, I don't want to install Ubuntu onto a USB drive, I want to install it on the Macbook Pro's hard disk, wiping OS X altogether.

I merely want to boot to the USB drive to run the Ubuntu installer (as it has no working optical drive).

---

### Post by tom4everitt on 2010-04-11
Macs are often bad at starting from usb:s unfortunately. Its not quite supported in the firmware or something like that.

Did you try with rEFIt?

---

### Post by linuxopjemac on 2010-04-11
If you put the iso of an Ubuntu liveCD on the USB stick you will end up with a liveUSB. You can then install from the USB...

---

### Post by aderowbotham on 2010-04-12
@linuxopjemac - yes but the problem is that the machine won't boot off usb, it doesn't appear to see the device at boot-up.

---

### Post by aderowbotham on 2010-04-12
@tom4everitt

Thanks. Now got rEFIt installed, and rEFIt boot menu is showing up. Still need to figure out how to run the Ubuntu installer I've got on the USB, from there.

---

### Post by tom4everitt on 2010-04-12
> **aderowbotham said:**
> @tom4everitt

Thanks. Now got rEFIt installed, and rEFIt boot menu is showing up. Still need to figure out how to run the Ubuntu installer I've got on the USB, from there.

Okay, cool. As I mentioned, it might be impossible to boot from usb. My current mbp (v 1,1) will not boot from usb for example (at least I haven't figured out how to it yet), and I know that usb-booting is badly supported in the mac firmware. 

On the black macbook i had before, there was never any problem with usb-booting though. So I guess it can be worth a try nevertheless (especially since I can't think of any similarily simple procedure to get ubuntu installed on the drive. perhaps you could take out the hard drive and install ubuntu on it from another computer?)

---

