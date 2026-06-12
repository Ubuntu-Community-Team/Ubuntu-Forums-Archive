---
title: "can anyone tell me specifically how to dual boot ubuntu from an external hard drive?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by lg325 on 2007-01-18
hey, im a computer amateur and recognize that a little knowledge can be a dangerous thing (drink deep the pierian spring or not at all, and whatnot) but i have recently been told about ubuntu from a computer-friend of mine and am intrigued. i love my windows programs and abilities, but i hate the problem of viruses and and the other trash that comes hand in hand with windows.

so i was hoping that i might be able to try ubuntu on an external hard drive and get the best of both worlds. i realize this is not a new idea, and have googled the topic briefly, but i dont know quite enough about computers to feel safe with anything i find that way. can anyone tell me, in laymen's terms, exactly how i would go about doing this? i have not yet purchased an external so if there is a specific kind i could try buying that. 
also, if i had it on an external, could i move the external from computer to computer easily and thus retain the operating system? (just for kicks)

i've looked through the board briefly and didnt see anything i could use, but if there is an old thread please tell me about it, otherwise, hopefully someone is ptient enough to go all the way through it. Thanks!

---

### Post by rai4shu2 on 2007-01-18
It highly depends on whether you BIOS can boot using that hardware (if you use a USB device for example, your BIOS needs to be able to boot USB).

---

### Post by lg325 on 2007-01-18
how exactly do i check my BIOS? im pretty sure i can, it wasn't mine but a computer of the same model tried booting off of an ipod and the hardware im looking at runs off of USB 2.0 ( Western Digital Passport WDXMS1200TN 120GB 5400 RPM USB 2.0 External Hard Drive) [i have a Dell E510 if that matters]

---

### Post by rai4shu2 on 2007-01-18
If you bring up BIOS setup (usually at the start of a reboot), you can usually find an option like Device Boot Order or something along those lines. If it can list your hardware there, then it may be able to boot it.

---

### Post by lg325 on 2007-01-18
well i dont actually own the hardware yet, is there a way i can test it? hook up an ipod or something? i've opened up the menu, however, and it seems fine, it has USB floppy and cd-rom drives on the list (disabled, i dont own any)

once i actually do have it hooked up and in the boot menu, how do i install ubuntu onto it? once i have the hardware up, do i boot to it and with the ubuntu disk in the tray does it do the rest?

---

### Post by dannyboy79 on 2007-01-18
your bios needs to say usb-zip or usb-hdd I believe. Even if it doesn't boot to a usb devise you could always take the hard drive out of the external enclosure and install into your computer!!! do you have any open ide channels? nomoral computers have 4 ide channels. channel 0, master and slave and then channel 1, master and slave. some might be channels 1 and 2. you can find out without opening your machine by going into your bios. if you just want to try Ubuntu out just use a Live CD. Woops, I remember you saying that you don't have a cd drive. How in the world do you get any software installed without a cd drive???? You could try to boot an ipod or a usb stick by copying all the files that get put on a windows boot disk only for the purpose to tell you if your computer boots to a usb device. I think anyway. Good luck.

---

### Post by PaulFXH on 2007-01-18
Check this guide which explains in detail how to boot Ubuntu (or other Linux) from an external HDD even if your BIOS does not recognise the exterlnal drive as bootable
.[https://help.ubuntu.com/community/BootFromUSB?highlight=%28](https://help.ubuntu.com/community/BootFromUSB?highlight=%28)

However, you will need to have a CD dive for this to function.

Paul

---

### Post by lg325 on 2007-01-18
no, i have two internal cd-drives, sorry for the confusion, the boot menu listed a possibility for USB floppy drive and USB cd-rom drives, not knowing if it would be helpful or not, i mentioned it, as an afterthought i mentioned that i dont have any USB CD-rom/floppy, mine are onboard. i'd be in quite the sorry state if i tried to do anything without a cr drive...

---

### Post by lg325 on 2007-01-18
thanks for the link paul, i was hoping something like that existed somewhere...now i just pray that my comp can recognize a USB device without all that...

anyways, this all sounds like it might be a little too complicated for forum chatter so i might have to skip the DIY approach and find someone to show me. unless anyone has anything important to share i'll just snoop around these documentation files.
thank you guys for your help

---

### Post by hoarsecourser on 2007-01-19
Okay...I have a similar question...I want to install Ubuntu onto a USB HDD...but I don't have a working CD drive.  I can get access to all the files on the install CD by using the .iso and VirtualCloneDrive and my BIOS will allow me to boot from USB HDD, but I need to find a way to get initrd onto that drive...I think.  I am, unfortunately, not well versed enough in this and I just killed my other Ubuntu box (hardware hell).  Can someone help me get this USB HDD to boot Ubuntu, with all the installation done within XP?  Looking forward to creative solutions...

---

### Post by derjames on 2007-01-19
Please read the post by Dabrugo, it may be useful

[http://ubuntuforums.org/showthread.php?t=80811&highlight=dabrugo](http://ubuntuforums.org/showthread.php?t=80811&highlight=dabrugo)

cheers

---

