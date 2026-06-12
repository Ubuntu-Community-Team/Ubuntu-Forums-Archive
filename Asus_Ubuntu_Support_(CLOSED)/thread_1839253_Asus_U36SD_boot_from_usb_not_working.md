---
title: "Asus U36SD: boot from usb not working"
date: 2011-09-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ilSignorCarlo on 2011-09-05
Hi,
I've just bought an Asus U36SD and I'm trying to install Ubuntu on it. There is no cd drive so I created a bootable usb drive with usb-creator.

This is what I did:
1) I inserted a CD with Ubuntu 11.04 64 bit
2) opened usb-creator
3) chose the cd in the top panel
4) chose the usb drive in the bottom panel

In the asus laptop I changed the boot sequence in the bios, where it appeared the correct name of my usb drive, but when I restart the computer it just runs windows.

What can I do?

---

### Post by ThomasArildsen on 2011-09-08
I had problems with this as well. Whenever I need to boot from USB, I enter the BIOS, go to the right-most tab "Save & Exit". In the list "Boot Override", I select my USB device and press ENTER. Then it reboots from the device.

---

### Post by pedal on 2011-09-08
Are you guys not able to change the boot priority order in BIOS to Removable Media/Device as the first?

I'm considering buying an U36SD and I need this feature to work without the need of going in to BIOS every time I boot.

---

### Post by ThomasArildsen on 2011-09-09
I played around with it a bit more just now since I am experimenting with an alternative OS install on an external hard drive. Under "Boot" in the BIOS, I found "Hard Drive BBS Priorities". Here I was able to change the boot order, so the external hard drive is used before the internal one. A USB flash drive I have connected was also in the list.

---

### Post by pedal on 2011-09-09
Was this a permanent solution so if you removed the hdd, rebooted, plugged it in again, reboot and it boots from the external hdd again without needing to go in to bois?

Have anyone tried booting from an SD card?

---

### Post by ThomasArildsen on 2011-09-09
I just tried what you suggest. Unfortunately, it seems that having had the external drive disconnected, it gets demoted to the bottom of the boot order once plugged back in.
Specifically, I have an internal HDD with Ubuntu 11.04, a USB flash disc with the Ubuntu 11.04 installer, and an external SSD with Ubuntu 11.04. I set the boot order as follows:
[LIST=1]
[*]External SSD
[*]USB flash disc
[*]Internal HDD
[/LIST]
I then reboot, remove the external SSD, reboot without it, and it boots from the USB flash disc. I plug in the external SSD, reboot, and it still boots from the USB flash disc. I reboot and check the BIOS, the boot order is now:
[LIST=1]
[*]USB flash disc
[*]Internal HDD
[*]External SSD
[/LIST]

However, this was all done using the "Hard Drive BBS Priorities" option, which the BIOS has the following note for: "Set the order of the legacy devices in this group". Unfortunately, I don't know what BBS is or why it is "legacy".
There also seems to be an option of modifying the boot order in another way: one can add boot options to a list. In this list, you can add a new custom option before the default option (that seems to be governed by the "Hard Drive BBS Priorities" setting). Maybe you can use this approach. Unfortunately, I cannot test it. I can only add my USB flash disc here; not the external SSD - maybe this has to do with the way the partitions are configured? It requires me to set a "Path for boot option" which I don't know how to find :-(

---

### Post by ThomasArildsen on 2011-09-09
There seems to be yet another option. The BIOS also lets you enable "UEFI boot". This adds another boot option to the list - "UEFI..." Setting this option as first priority causes the computer to boot from the USB flash disc, yet with a different boot loader than when I normally from it. I suppose this has to do with how UEFI boot works, but I am not very familiar with it. Unfortunately, it doesn't seem to work and the system just hangs after selecting "Try Ubuntu without installing" in the boot loader. I hope this is the USB disc's fault and not the computer's...
Unfortunately, this UEFI boot option also seems to be down-prioritized when the computer has been booted without the USB flash drive :-(

---

### Post by girinlg on 2011-09-09
After inserting the usb go to bios by pressing the F8 or F12. On the screen it will display your usb. Click on it, I think it will work fine.

---

### Post by jmk08 on 2011-09-18
Go to Asus.com then navigate to their support page. Download the bios firmware and the adjacent program which actually installs the download (winbios or something like that.

Once you have downloaded both programs, open the installer and use it to navigate to your firmware file. It will take about at minute. 

Once done, your ready to go. Restart your computer, ensure that a USB option is selected in the boot menu of your bios, and that you have a usb in, and enjoy Ubuntu!

Once in Ubuntu, navigate to your 'driver update' program. After a minute or two of searching it will display a list of (probably) two options. One will be a nvidia driver by nvidia, the other will be a nvidia driver by Ubuntu, install the Ubuntu one! After that your pretty much good to go. Enjoy!

---

### Post by BjarteMØstvold on 2011-09-22
I have the specific problem mentioned by ThomasArildsen in #7:

I can boot from a USB stick, but after selecting "Try Ubuntu without installing" the U36SD just hangs.  The stick, made from ubuntu-11.04-desktop-amd64.iso, works fine on another laptop.  In fact, there it boots into a GUI whereas on the U36SD it enters some text UI.

Any ideas how to proceed would be greatly appreciated!

(Message #[**9**]("http://ubuntuforums.org/showpost.php?p=11262582&postcount=9") suggests upgrading the BIOS, but I was unsure to what problem that replay was intended.  And I'm wary of doing a BIOS upgrade having read stories about how it may brick the laptop...)

  Bjarte

---

### Post by TweFoju on 2011-09-26
Did you happen to plug the Flash Drive into the 3.0 USB?

because 3.0 is the problem, try sticking it to the 2.0 instead

and try follow this steps:

[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

---

### Post by @Craw on 2011-09-28
> **BjarteMØstvold said:**
> I have the specific problem mentioned by ThomasArildsen in #7:

I can boot from a USB stick, but after selecting "Try Ubuntu without installing" the U36SD just hangs.  The stick, made from ubuntu-11.04-desktop-amd64.iso, works fine on another laptop.  In fact, there it boots into a GUI whereas on the U36SD it enters some text UI.

Any ideas how to proceed would be greatly appreciated!

(Message #[**9**]("http://ubuntuforums.org/showpost.php?p=11262582&postcount=9") suggests upgrading the BIOS, but I was unsure to what problem that replay was intended.  And I'm wary of doing a BIOS upgrade having read stories about how it may brick the laptop...)

  Bjarte

Bjarte,

Your problem (hanging, no GUI) looks like a video card driver problem. Make sure you have the latest driver installed.

Or you can install using the command line then boot to Recovery (this is GUI, "Safe Mode" in Windows) and install the latest drivers from there.

Good luck.

---

### Post by jadahl on 2011-10-22
I have a U36SD as well, and to boot a USB drive I press Esc during the BIOS splash screen, select the USB drive in the list that pops up, then I it boots the Ubuntu installer.

---

### Post by BjarteMØstvold on 2011-11-07
> **BjarteMØstvold said:**
> 

I can boot from a USB stick, but after selecting "Try Ubuntu without installing" the U36SD just hangs.


Turns out the problem was my stupidity: I selected the boot option called (from memory) "UEFI: boot from USB".  Instead, I should have selected the option called XXX where XXX is the name with which the USB stick identifieds itself.

---

