---
title: "In a linux / ubuntu context, what does &quot;firmware&quot; mean?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by e_james on 2008-02-02
Until recently I thought I knew the meaning of "firmware". It's the software which runs my motherboard (also known as the "bios"), my dvd writer, my dvd recorder, my adsl router etc. Originally the only way to change it was to replace the chip but, in more recent years, the software can be updated by "flashing". This "flashing" procedure is not to be undertaken lightly because, if it goes wrong, the hardware is usually permanently useless.
What is now confusing me is the way "firmware" downloads are often a part of the linux driver installation for less common hardware. Am I really changing the built in software of my hardware? Have I broken 2 perfectly good adsl modems? Why is it necessary to change the hardware to get it to work with linux? Have I misunderstood the meaning of "firmware"?

---

### Post by spiderbatdad on 2008-02-02
frimware is only a program. It can be update by flashing ROM or it can be uploaded as a binary image into the existing hardware.[http://en.wikipedia.org/wiki/Firmware](http://en.wikipedia.org/wiki/Firmware)

I'm guessing that firmware is updated by certain linux drivers to prevent a bios lockout. In otherwords, to prevent your machine from be rendered useless when the aspects of a device are not recognized by the bios...I'm just guessing! I know that some bios have a whitelist of hardware...the wrong hardware would cause a lockout....IBM thinkpad mini pci cards for example.

---

### Post by e_james on 2008-02-02
spiderbatdad

Thanks for that wikipedia link. I have copied a small part of it below.

> Some devices, such as video adapters and modems, frequently rely on firmware that is loaded dynamically by the operating system device driver

I hadn't considered that possibility. Maybe my modems aren't broken after all. If it is necessary to upload software to a device before it can function, it explains why linux device driver installation includes firmware. The distinction between firmware and driver being that firmware runs on the device processor while the driver runs on the computer processor.

It also explains something else. It is reasonable that the driver is applicable to several similar devices, but the firmware will be very specific to one version of a device.

Any further comments anyone? Have I got it right?

---

### Post by Cypher on 2008-02-02
You are correct in thinking that firmware is something that natively handles the operation of a certain device. In most cases it is usually that's held in flash accessible to the device upon power-up and provides from the most basic to the most complicated functionality.

One set of firmware (things like on your router) are those that get updated once and unless a new version is programmed in, the same version continues to operate. There are other devices that have a very SIMPLE firmware that basically configures the device to accept a more complicated firmware that provides the actual functionality. This firmware is usually included in the drivers and when the device is first contacted by the driver, the fimware is sent over.

This way new functionality can be added to the firmware and safely sent to the device and should the firmware not work properly, you can just power-cycle and get a newer version without risking "bricking" your hardware.

Additionally when certain chips are designed, all the logic can be laid out in the silicon itself and this means that any errors or problems will require a silicon re-spin and some manufacturers want to avoid that, so they put only the most basic fool-proof code is in silicon and everything else comes from a firmware that is downloaded by a driver..

---

### Post by dcstar on 2008-02-03
> **e_james said:**
> 
...........
Any further comments anyone? Have I got it right?

"Firmware" means any computer code that remains without power to a system, but still can be changed by one means or another.

"Hardware" code is (virtually) permanent, any change to it means changing the actual hardware.

"Software" is named thus because it was (in the past) only run in memory that relies on power to retain the various zeros and ones and was therefore a lot more fragile - but extremely easy to change (as you experience every time you load a program on your system).

In essence, "Firmware" is between the ethereal software code in memory (which can change at any time) and the permanent hardware code - hence the term of something in the middle of "Soft" and "Hard" - "Firm".

---

