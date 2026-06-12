---
title: "Mac mini 2010 Blank Screen on Ubuntu 10.10 &amp; 9.04 CD Boot"
date: 2010-11-25
forum: Apple Hardware Users
---

### Post by kilowattradio on 2010-11-25
I just purchased a new Mac Mini 2010 to replace my older Mac Mini 2006 Intel. The problem I am having is that when I boot Ubuntu from the MM 2010 CD-ROM the initial menu that allows you to select a language is displayed, but after that the screen goes blank and stays blank. I am using the HDMI port to DVI output and I am wonder if that could be a cause of the blank screen. Is there a boot command that I can use to allow Ubuntu to display with the HDMI port or other item I need to fix to get Ubuntu CD installer video display to work with my MM 2010?

:confused:

---

### Post by nataraj88 on 2010-11-27
> **kilowattradio said:**
> I just purchased a new Mac Mini 2010 to replace my older Mac Mini 2006 Intel. The problem I am having is that when I boot Ubuntu from the MM 2010 CD-ROM the initial menu that allows you to select a language is displayed, but after that the screen goes blank and stays blank. I am using the HDMI port to DVI output and I am wonder if that could be a cause of the blank screen. Is there a boot command that I can use to allow Ubuntu to display with the HDMI port or other item I need to fix to get Ubuntu CD installer video display to work with my MM 2010?

:confused:

After you get the language screen and confirm that, you need to hit f6 and bring up the boot options menu and select nomodeset as a boot option.

I'm surprised you get as far as the language screen, cause usually you have to type a character on the keyboard to bring up any of the boot options menus.  I'm not sure what the MM cdrom is, but my experience is with 10.04.1.  In any case, to boot most linux distributions on the mac mini and work around this video problem, you need to add nomodeset to the boot options.

After you do the install, you will need to add the following line to /etc/default/grub and then run update-grub (booted from the installed system).  You will have to type space to get into grub and add nomodeset the first time you boot.  reboot=pci will make the reboot command work.

GRUB_CMDLINE_LINUX='nomodeset reboot=pci'

Also, if your MM cd does not have an updated broadcom tg3 driver, you may need to download, build and install that.  I transfered the driver source (from the broadcom web site) via usb drive and built it under the live cd then used 'insmod tg3.ko' to bring up the ethernet.


Nataraj

---

