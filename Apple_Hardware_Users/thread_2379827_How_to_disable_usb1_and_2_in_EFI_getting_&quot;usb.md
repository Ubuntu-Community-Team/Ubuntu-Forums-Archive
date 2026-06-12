---
title: "How to disable usb1 and 2 in EFI getting &quot;usb drawing too much current&quot;"
date: 2017-12-10
forum: Apple Hardware Users
---

### Post by admiralmutiny on 2017-12-10
I have a 2006 Mac Pro 1.1 that I am trying to install Ubuntu 16.04 LTS on.  I has always given me the five pop-up messages "A USB device is drawing too much power and has been disabled" at startup, I just move them off the screen and keep going.  I tried everything to fix this on the OSX side.  Even unplugged the USB cables from the motherboard with no luck.  I have done many Ubuntu installs on PC's, used to build hackintoshes, and have booted to linux on usb on Macbooks, but this is the first time for this old MacPro.  During the boot of the Ubuntu install disk I get "usb device drawing too much current" repeating and alternating between usb1 and usb2.  Now I just want to issue a command during boot to disable USB1 and USB2. Is it possible to do this in EFI, grub, or rEFInd?  Use a command like this: " [COLOR=#111111][FONT=Consolas]echo '3-8' |sudo tee /sys/bus/usb/drivers/usb/unbind" found here [/FONT][/COLOR]https://askubuntu.com/questions/714973/reboot-disable-and-enable-usb-ports? I can't disable all of USB, but 1 and 2 are either just the front ports or the internal ones going to bluetooth and something else.

Really thanks for any help you can give me here.

---

### Post by ratell on 2017-12-10
I think you can blacklist them with something like what is described here.
[https://itsfoss.com/how-to-disable-usb-ports-in-ubuntu/](https://itsfoss.com/how-to-disable-usb-ports-in-ubuntu/)

i’ve never done it so don’t know if it really help, but it gives you something to try.

---

### Post by admiralmutiny on 2017-12-10
Thanks, that would probably work, but it does not boot up far enough to type in the command from linux. The install hangs with the "...too much current..." messages.  I need to know how to edit the config file to execute the command or hopefully execute it from rEFInd would be easiest.  I think I have to disable the ports in EFI, this should disable the ports before linux sees the overcurrent.  I think I found the EFI commands here:

[http://wiki.phoenix.com/wiki/index.php/EFI_USB_PORT_FEATURE](http://wiki.phoenix.com/wiki/index.php/EFI_USB_PORT_FEATURE)

I am looking up how to enter this command from rEFInd because that seems easier than editing the iso, but I'm in over my head with it. Does anyone know how to do that?

typedef enum {
  EfiUsbPortEnable = 1,
  EfiUsbPortSuspend = 2,
  EfiUsbPortReset = 4,
  EfiUsbPortPower = 8,
  EfiUsbPortOwner = 13,
  EfiUsbPortConnectChange = 16,
  EfiUsbPortEnableChange = 17,
  EfiUsbPortSuspendChange = 18,
  EfiUsbPortOverCurrentChange = 19,
  EfiUsbPortResetChange = 20
} EFI_USB_PORT_FEATURE;

---

### Post by ratell on 2017-12-10
I think that if you edit /etc/modprobe.d/blacklist you specify things to not be loaded at boot.

[https://askubuntu.com/questions/110341/how-to-blacklist-kernel-modules](https://askubuntu.com/questions/110341/how-to-blacklist-kernel-modules)

Maybe someone who actually knows will chime in.

---

### Post by kevin160 on 2017-12-12
That's really weird.  I have a Pro 1,1 and have never seen that message (Ubuntu 12.04 through 17.04).  It almost sounds like a hardware issue.  Could a bit of metal or a crushed wire be shorting a connection?  Get some canned air and blow out your USB ports on the front and back of your Pro.

---

