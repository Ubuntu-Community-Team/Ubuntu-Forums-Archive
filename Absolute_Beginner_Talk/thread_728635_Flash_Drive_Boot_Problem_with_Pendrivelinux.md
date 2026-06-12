---
title: "Flash Drive Boot Problem with Pendrivelinux"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by metalfanatic07 on 2008-03-19
I finally figure out how to boot pendrivelinux. i have to unplug my external HD, but in order for BIOS to recognize the existence of the flash drive, i have to "deactivate" my keyboard under linux. any advice or help?

---

### Post by Xiong Chiamiov on 2008-03-19
What do you mean by deactivating your keyboard under Linux?  Disable it in the BIOS to get it to boot Linux?

---

### Post by metalfanatic07 on 2008-03-19
what happens is if i  disable legacy usb support, the keyboard will work, but then i can't boot from the flash drive. if i enable legacy, the keyboard won't work, but i can boot from the flash drive. the wierd thing is that if i boot with the CD with legacy disabled, i can still read from the flash drive under ubuntu, but not boot from it. it's a similar situation with my external HD

*post edited for clarity*

---

### Post by Xiong Chiamiov on 2008-03-19
> **metalfanatic07 said:**
> what happens is if i don't disable legacy usb support, the keyboard **wont'** work, but then i **can't** boot from the flash drive. if i leave legacy enabled, the keyboard **will** work, but i **can** boot from the flash drive. the wierd thing is that if i boot with the CD with legacy disabled, i can still read from the flash drive under ubuntu, but not boot from it. it's a similar situation with my external HD

Do you mean won't/can will/can't?

Unfortunately, I don't have any particular ideas other than trying a different keyboard.

---

### Post by metalfanatic07 on 2008-03-19
that's sort of what i meant, i edited the post for clarity

---

### Post by IsawSp4rks on 2008-03-19
This is a BIOS issue and something you could take up with your motherboard manufacturer.  This is due to the fact that booting off USB is not a legacy function because back in the day, USB was used only for connecting devices such as mice or graphics tablets.  It's an either/or situation because when you enable legacy device support, the supplants one set of USB microcode for another (non legacy support) - you can't do both at the same time and this is a limit set by design due to BIOS ROM size limits.

The simple answer is to use a non USB keyboard, such as as PS/2 keyboard (it connects via the mini DIN connector, usually green next to the other PS/2 connector, usually purple  for PS/2 mice on the back of your PC).

---

### Post by metalfanatic07 on 2008-03-19
so basically, i'm SoL because my laptop has no external PS/2 plugs.

---

### Post by IsawSp4rks on 2008-03-20
Well, you may get around it by using a Bluetooth wireless keyboard.  I don't think they communicate via legacy standards as they do so via the Bluetooth stack.  But then you add the issue of making sure it works in your Flashdrive installation.

---

