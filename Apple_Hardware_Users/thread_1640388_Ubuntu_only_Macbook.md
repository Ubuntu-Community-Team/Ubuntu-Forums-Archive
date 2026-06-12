---
title: "Ubuntu only Macbook"
date: 2010-12-07
forum: Apple Hardware Users
---

### Post by m3tro on 2010-12-07
I have a Macbook 2,1 since 2007. Last week my hard drive just died, so I decided to replace it with a new one, no problems with that. The problem came when I had to install an operative system, because my DVD drive has been broken for a year and a half now. I know we can easily install MacOSX from an external usb drive, but I don't have a big enough pendrive at the moment.

So I went for Ubuntu. I have managed to get an Ubuntu 10.10 live usb stick working like charm, if anyone is interested. I just downloaded the latest i386 iso and followed [this advice by pxwpxw]("http://ubuntuforums.org/showthread.php?p=7926629") for the 32bit EFI. The only thing I had to change in the boot.cfg was the name of the iso and -very important- changed initrd.gz for initrd.lz

The live usb works great. But I decided to do an installation on the hard drive. I installed it using the whole hard drive and didn't get any errors. But when I boot the macbook it doesn't detect anything. I guess I need an EFI bootloader or something to make it work. I've tried to follow [this]("http://grub.enbug.org/TestingOnMacbook") guide but it seems to be intended for someone who already has MacOSX and the Ubuntu installation working. I just want to install a bootloader or whatever I need from the "outside" (from the live usb I'm using). 

I tried to just throw reFit into the main hard drive's root folder but it doesn't work. I think that maybe creating an HFS+ partition and installing reFit in it may work, but I don't think I can create that kind of partition from the Ubuntu usb and I also need a working MacOSX to run the enable.sh. I've also read of elilo but I've seen that it hasn't been updated for 3 years now so I don't know if it's a good idea.

Any suggestions or ideas? If someone wants more info on how to create the live usb I'll be glad to help.

---

### Post by m3tro on 2010-12-07
I did it. I built the GRUB2 as said in [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) (32Bit EFI), then created a 100MB Fat32 partition and put the Grub in it as /EFI/BOOT/BOOTIA32.EFI. Then I edited the grub.cfg as they say in that page, except pointing to sda2 instead of sda3. For the moment I'm using it without BIOS dump and works perfectly, but I have to try the other way just to check it out.

So now I have my Ubuntu-only Macbook!

---

### Post by linuxopjemac on 2010-12-08
Could you write a little manual how you did it? I would like to publish that.

---

### Post by m3tro on 2010-12-08
I'll be busy for the next few days but I'll try to do it when I have some time!

---

### Post by linuxopjemac on 2010-12-09
Great thanks!

---

