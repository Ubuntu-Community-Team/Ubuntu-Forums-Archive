---
title: "Device for SD cards not working"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2008-01-05
Hi I have a device in my laptop(Toshiba Sattelite a135 s4656) to read SD cards from digital cameras. But I put a SD card from my digital camera, or from anyother camera, and nothing happens, I searched in my computer for a folder with the photos but no success.

Probably the drivers for this device are not installed. But the question is, what are the devices considering the type of my laptop?

Thanks.

Bruno Krebs

---

### Post by Bufke on 2008-01-05
Does entering lshal | grep SD in a terminal bring up anything?  Also try looking in the folder /media.  Is accessing the camera via usb an option?  If so you could access the SD while in the camera.

---

### Post by brunoskrebs on 2008-01-06
>   info.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  pci.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
  pci.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)

This is what brings me... I don't know what does this means. And I don't have the USB cable :P so this is a big problem. And I want all my devices working also...

The output from your code means that I have the device installed or not? If yes how do I access it? Because I went to /media and I couldn't find anything. And if it is not installed how do I install??

Thanks again.

Bruno Krebs

---

### Post by Bufke on 2008-01-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53923) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				That code just means ubuntu at least knows you have a SD card reader, getting it to work is another story.  There was a bug relating to this card reader that appears to have been fixed, are you running Gutsy with the latest updates?

---

### Post by brunoskrebs on 2008-01-07
Yes, My gutsy is up to date. I read the post that shows the bug file but is too complicated for a noob like me.

Can someone give me a support please??

---

