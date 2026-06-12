---
title: "Blank screen at install"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by XA1 on 2007-07-27
I downloaded the iso and burned a disk. I then booted with the disk in the drive and selected the install option. The Ubuntu logo appears with a scrolling orange bar, and this goes on for a while. Then it goes through loading all the drivers and such, and appears to complete that. However, when that is over, the screen goes blank and the harddrive and CD drive stop. Can anybody help me?

---

### Post by AlexenderReez on 2007-07-27
i think there is something wrong with that particular livecd :) ....don't burn live cd using too fast speed :) 
where do you download ubuntu ?

if still won't work,please use alternate cd to install :)

---

### Post by XA1 on 2007-07-27
I tried downloads from two separate mirrors listed on Ubuntu's official site, and I checked hash and disk integrity both times. I'm pretty dang sure it's not the CD. I also tried both 64-bit and x86 versions (I have a Turion 64 mobile) to no avail.

Any other ideas?

---

### Post by mozkill on 2007-07-27
could be a bad piece of RAM.  use Memtest86 on the computer and test the memory.

---

### Post by XA1 on 2007-07-27
I checked memory integrity with all 4 different runs, and it says I'm just fine :confused:

---

### Post by RedSquirrel on 2007-07-27
Do you have an ATI X**** card? There are problems with those:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by XA1 on 2007-07-27
Negative, I've got an nVidia card.

My computer is an HP Pavilion DV6000us.

---

### Post by Ek0nomik on 2007-07-27
> **XA1 said:**
> Negative, I've got an nVidia card.

My computer is an HP Pavilion DV6000us.

I would try to install using the Alternate CD.  On the Get Ubuntu webpage, there is a checkbox below the green Start Download button.  The Alternate CD is a text based install, thus it won't load the graphical interface.  This may be able to allow you to install the operating system, and getting to a command prompt after the installation to install your proper video card drivers.

If you are able to install with the Alternate CD, then just use a guide for your video card to install the latest drivers.

---

### Post by XA1 on 2007-07-27
Alright, I installed with the text installer (alternate CD) and that worked fine. Now, when I put up, I get the GRUB menu, which is good. However, if I select either Linux kernel, it just does the whole blank screen thing again. Grr...

---

### Post by XA1 on 2007-07-28
[[[bump]]]

---

### Post by mozkill on 2007-09-19
I don't know the details, but it sounds like you need to experiment with GRUB boot options during the installation.   The installer could be getting hung up on a drive controller or something. 

Here is an example of what you might need to do that I sniped from Google:

> Take the Ubuntu 7.04 or 6.10 live cd and on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding “noapic nolapic pci=noacpi acpi=off” at the end of the line (without " "). This disable for the moment the acpi daemon.

---

### Post by mozkill on 2007-09-19
I don't know the details, but it sounds like you need to experiment with GRUB boot options during the installation.   The installer could be getting hung up on a drive controller or something. 

Here is an example of what you might need to do that I sniped from Google:

> Take the Ubuntu 7.04 or 6.10 live cd and on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding “noapic nolapic pci=noacpi acpi=off” at the end of the line (without " "). This disable for the moment the acpi daemon.

here is another snippet I took from Launchpad.net 

>  Bob Stuart said on 2007-08-25: 
Ican't install Ubuntu 7.04 on an old computer--Pentium ii. 233mhz, 288mb ram, 8 gig HD.
Disk boots to install screen, on ist choice, get some action, then "can't find RSPD" and something about "failed to allocate memory resource #6".
Then I get a logo and "UBUNTU" in orange letters on a black screen with an orange bar going back & forth. Then the bar stops and the computer freezes up.
I tried the suggestion about F6 and typing "noapic nolapic pci=noacpi acpi=off" that solved a similar problem for others but the only difference was that I DIDN'T get the
"can't find RSPD" message. I had Win XP installed when I first tried and then deleted the partion on the HD with a startup floppy and repartitioned. Tried again with same result. Then tried the F6 and additional typing with the result as above.
THanks for any help.

---

### Post by mozkill on 2007-09-19
I don't know the details, but it sounds like you need to experiment with GRUB boot options during the installation.   The installer could be getting hung up on a drive controller or something. 

Here is an example of what you might need to do that I sniped from Google:

> Take the Ubuntu 7.04 or 6.10 live cd and on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding “noapic nolapic pci=noacpi acpi=off” at the end of the line (without " "). This disable for the moment the acpi daemon.

here is another snippet I took from Launchpad.net 

>  Bob Stuart said on 2007-08-25: 
Ican't install Ubuntu 7.04 on an old computer--Pentium ii. 233mhz, 288mb ram, 8 gig HD.
Disk boots to install screen, on ist choice, get some action, then "can't find RSPD" and something about "failed to allocate memory resource #6".
Then I get a logo and "UBUNTU" in orange letters on a black screen with an orange bar going back & forth. Then the bar stops and the computer freezes up.
I tried the suggestion about F6 and typing "noapic nolapic pci=noacpi acpi=off" that solved a similar problem for others but the only difference was that I DIDN'T get the
"can't find RSPD" message. I had Win XP installed when I first tried and then deleted the partion on the HD with a startup floppy and repartitioned. Tried again with same result. Then tried the F6 and additional typing with the result as above.
THanks for any help.

It might be easier to get a different computer. LOL

---

