---
title: "FireWire Drive"
date: 2007-05-11
forum: Apple Intel Users
---

### Post by cbrain on 2007-05-11
Greetings,

I have an Intel iMac and I would like to know if it is possible to install ubuntu on a partition I made on my external.

Thanks.

---

### Post by erkker on 2007-05-11
I have a new MBP 15" 2.33Ghz and I have failed at this miserably using 2 different USB drives (one being an ipod) using rEFIt.  It install fine, but rEFIt fails to boot even after it recogzines the the drive at startup. Things maybe different with a firewire drive though.

-E

---

### Post by cbrain on 2007-05-11
I'm not using rEFIt, i'm using the origanal EFI firmware.

---

### Post by benanzo on 2007-05-11
I don't think EFI will boot a usb device at this time.  I'm pretty sure we are waiting on Apple for a firmware update for that...

The current EFI will, however, boot a firewire device just fine.  While I am not too knowledgeable on exactly how (I think you will just install Ubuntu to the external disk as normal, and reboot holding option to get the built in EFI OS selector.  You will have to use rEFIt if at any time you want to boot three OSs -- the current EFI version only supports two choices in the selector.  Hopefully Apple will get to work on that soon.  ( or just chainload two OSs in the GRUB selector )

---

### Post by AWerner32 on 2007-05-13
I have treid this before and while it will try to boot i have had GRUB errors. i am going to try again to give you some more details

---

### Post by AWerner32 on 2007-05-13
Ok after installing ubuntu on the firewire drive when trying to boot with the apple firmware is gives me a grub hard drive error and with rEFIt it says it cannot find the legacy boot loader. if anybody could diagnose the grub problem then we would be in the clear i think

---

### Post by AWerner32 on 2007-05-25
If i installed the grub solely on the linux partition rather than on the entire drive do you think it would work?

---

### Post by AWerner32 on 2007-05-25
so answer my own question again, after trying it. still doesnt boot

---

### Post by soundless on 2007-05-27
> **benanzo said:**
> I don't think EFI will boot a usb device at this time.  I'm pretty sure we are waiting on Apple for a firmware update for that...



no, efi does support usb booting, i am running the 10.5 beta on an external usb drive just fine. but i too had problems getting ubuntu to run on a usb drive

---

### Post by AWerner32 on 2007-05-27
Well if anybody has successfully configured a portable drive to boot it would be great if they could report how they did it. So far it seems all of the problems lie in the grub loader. I don't have the knowledge or know-how to figure out where the problems lie so everything i do is trial and error but just the slightest hint could be really helpful.

Thanks

---

### Post by soundless on 2007-05-27
i think it is not that hard to do if it is in 1 partition, but when there are multiple, you can't do the automatic install thing, that is what screwed me up

---

### Post by PostScript on 2007-06-14
If I remember correctly, Boot Camp does give you the option of installing Windows on an external HD... I may be wrong though....

---

### Post by 11xzeginx11 on 2007-06-25
There is a OSX backup program called SuperDuper. It clones a drive, CD, or image. and makes it bootable on a target FIREWIRE drive. Sure you can use USB, but i don't think you can boot from it. Give that a try. Its free

---

### Post by ivesjd on 2007-06-25
> **soundless said:**
> no, efi does support usb booting, i am running the 10.5 beta on an external usb drive just fine. but i too had problems getting ubuntu to run on a usb drive

I think thats cause your running the beta of 10.5. Which means that leopard will probably support it.

---

