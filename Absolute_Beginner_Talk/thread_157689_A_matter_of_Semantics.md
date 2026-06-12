---
title: "A matter of Semantics?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by K0LO on 2006-04-09
I'm currently in the process of configuring my Intel 2915abg Wireless card to work with AES encryption at home and with Secure-W2 at work, and have found many articles full of helpful advice. Most of them recommend that I install the latest version of the Intel ipw2200 **driver **and ipw2200 **firmware**, since the packages installed by Kubuntu 5.10 aren't the latest version.

I'm somewhat confused by the terminology here. As I understand it, a **driver **is a piece of code that is run by the operating system and is responsible for handling communication between the device and the OS, while **firmware **is a piece of code that is executed by a processor on the device itself.

What concerns me is that I've already upgraded the Intel wireless card with the latest Windows firmware. This operation involved writing the firmware to flash memory in the card. I don't want to do anything to change the firmware that is currently resident in the card. If I install the latest firmware for Linux, will it be written to flash memory and overwrite the current Windows firmware, or is it just another piece of code that is resident in a file on the hard disk and run by the card when Linux is executing?

---

### Post by dcstar on 2006-04-09
[QUOTE=K0LO]
.......
I'm somewhat confused by the terminology here. As I understand it, a **driver **is a piece of code that is run by the operating system and is responsible for handling communication between the device and the OS, while **firmware **is a piece of code that is executed by a processor on the device itself.

What concerns me is that I've already upgraded the Intel wireless card with the latest Windows firmware. This operation involved writing the firmware to flash memory in the card. I don't want to do anything to change the firmware that is currently resident in the card. If I install the latest firmware for Linux, will it be written to flash memory and overwrite the current Windows firmware, or is it just another piece of code that is resident in a file on the hard disk and run by the card when Linux is executing?[/QUOTE]
"**Firm**ware" is something that is not as volatile as "**Soft**ware", essentially this means it remains after the power is turned off in a device - but still can be altered (by various means).

So, to answer your question, yes it will (probably) overwrite the existing firmware in the device - whether that is a good/bad/benign thing you may have to experiment with to determine.

It is possible that the Linux driver only works with a particular firmware version (what, more effort put into Windows updates over other OSs...never....), but the Windows driver may work with the Linux firmware - it may also be that both work with both.

---

### Post by az on 2006-04-09
[QUOTE=K0LO]I'm currently in the process of configuring my Intel 2915abg Wireless card to work with AES encryption at home and with Secure-W2 at work, and have found many articles full of helpful advice. Most of them recommend that I install the latest version of the Intel ipw2200 **driver **and ipw2200 **firmware**, since the packages installed by Kubuntu 5.10 aren't the latest version.[/QUOTE]

Just be aware than when you update your kernel, you may have to repeat the steps to recompile the wireless driver each time you get a new kernel.

Check to see what version is in Dapper.  Maybe you would be better off to run Dapper for a month before it becomes stable.

[QUOTE=K0LO]

I'm somewhat confused by the terminology here. As I understand it, a **driver **is a piece of code that is run by the operating system and is responsible for handling communication between the device and the OS, while **firmware **is a piece of code that is executed by a processor on the device itself.[/QUOTE]

Yes.

[QUOTE=K0LO]
What concerns me is that I've already upgraded the Intel wireless card with the latest Windows firmware. This operation involved writing the firmware to flash memory in the card. I don't want to do anything to change the firmware that is currently resident in the card. If I install the latest firmware for Linux, will it be written to flash memory and overwrite the current Windows firmware, or is it just another piece of code that is resident in a file on the hard disk and run by the card when Linux is executing?[/QUOTE]

Why did you flash your device originally?  It involved running software that flashed a particular file to your device?  Usually, the resident firmware can be backed up, first.  Now, do the steps you read involve the same process for linux or is there just another firmware file that is part of the linux driver package?

If that is the case, it may be that the firmware is being uploaded to the device's ram.  Many wireless devices use both kinds of firmware, with the software firmware being able to override the more premanently flashed firmware until you unplug the device or reboot.

To be sure, ask the people who maintain the linux driver:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by K0LO on 2006-04-10
[QUOTE=azz]If that is the case, it may be that the firmware is being uploaded to the device's ram.  Many wireless devices use both kinds of firmware, with the software firmware being able to override the more permanently flashed firmware until you unplug the device or reboot.

To be sure, ask the people who maintain the linux driver:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)[/QUOTE]

That explanation makes sense. I'll check with the driver maintainers just to be sure before proceeding. Thanks again for your help.

---

### Post by K0LO on 2006-04-11
Just to close out this thread, I contacted the driver maintainers (who are Intel employees BTW) and here's their response:

Question:
[SIZE="1"] If I update the Linux binary firmware image on my Linux partition, am I going to affect the operation of the 2915abg card in Windows in any way?[/SIZE]

Response:
*No.*

Question:
[SIZE="1"] In other words, will the firmware image be transferred into the card and stored in flash memory?[/SIZE]

Response:
*Its transferred to the card every time the adapter is initialized; there is no persistent flash memory on the adapter to store the firmware/microcode.*

So, getting back to the semantics issue, it appears that the "firmware" being referred to is just the microcode for the wireless adapter, and it is executed from RAM by the adapter, and is not persistent. So "firmware" is a poor choice of words because of the implications of it being something permanent (ROM/EEPROM/Flash). It should probably have been called something else ("microcode", perhaps)?

---

### Post by az on 2006-04-11
> **K0LO]J
Response:
*Its transferred to the card every time the adapter is initialized said:**
> 


So what was it you did in windows that involved flashing?

[QUOTE=K0LO]J
So, getting back to the semantics issue, it appears that the "firmware" being referred to is just the microcode for the wireless adapter, and it is executed from RAM by the adapter, and is not persistent. So "firmware" is a poor choice of words because of the implications of it being something permanent (ROM/EEPROM/Flash). It should probably have been called something else ("microcode", perhaps)?

No.  firmware is firmware, regardless of how it is stored.  Firmware is code that the device's processor executes.  That's why there is such a big debate as to whether such firmware blobs should be considered software (in terms of software freedom).  Since the code does not execute in your computer, but inside the device, some say that it does not matter if it is not distributed as free-libre open-source software.  Others take the view that if it is a file on your hard disk, it should be free-libre, regardless of where it is executed.

You decide.

---

### Post by K0LO on 2006-04-12
> So what was it you did in windows that involved flashing?

I may have jumped to the wrong conclusion, but here's what happened. Despite the Intel response that says the card's microcode is loaded and executed in RAM on the card, I know that there is *some *nonvolatile memory on the card. I know this because my laptop's hard disk failed and I replaced it with a new drive, formatted the drive, and installed the OS from scratch. When I fired it up I was quite surprised to find that all of my wireless settings had been preserved -- the list of wireless access points (including those at work, well out of radio range), the priority that I had sorted them in, the WPA passphrases-- all still there, so they **must **have been stored in nonvolatile memory *somewhere*, so I assumed that "somewhere" was in the wireless card.

Later when I upgraded the Intel wireless drivers in Windows, the instructions with the update warned that performing the update would erase all of the WEP/WPA keys. Sure enough, after the update all of the keys and the list of wireless access points were gone, so I assumed that this operation had cleared some portion of nonvolatile memory in the card. Thus my conclusion, perhaps incorrect, that I had "flashed" the card while updating.

I am going to have to respectfully disagree about describing the Linux microcode for the wireless adapter as "firmware". I think that this terminology is clear as mud. It certainly confused me at first, requiring that I take up your valuable time and even requiring me to email Intel for clarification.

The IEEE dictionary of electronics defines **firmware **as:

[SIZE="1"][I](A) Computer programs and data loaded in a class of memory that cannot be dynamically modified by the computer during processing.
(B) Hardware that contains a computer program and data that cannot be changed in its user environment. The computer programs and data contained in firmware are classified as software; the circuitry containing the computer program and data is classified as hardware.
(C) Program instructions stored in a read-only storage.
(D) An assembly composed of a hardware unit and a computer program integrated to form a functional entity whose configuration cannot be altered during normal operation. The computer program is stored in the hardware unit as an integrated circuit with a fixed logic configuration that will satisfy a specific application or operational requirement.[/I][/SIZE]

I think that microcode executed in RAM is really stretching definition (A). Although you *could *protect the code from dynamic modification by proper programming techniques, the fact that it's in RAM makes it easy to modify, intentionally or not.

Definition (C) is what most people think of as applying to firmware. If you don't believe me, have a look at this guy's letter: [http://lists.debian.org/debian-devel/2004/04/msg00518.html]("http://lists.debian.org/debian-devel/2004/04/msg00518.html") which contains links to dozens of definitions of firmware. All of them define firmware as being ROM or EPROM or EEPROM resident.

I'm not sure who decided to call these microcode segments "firmware", but I think it's a poor choice of words because it's misleading.

---

