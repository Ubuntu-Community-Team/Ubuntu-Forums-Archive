---
title: "ubuntu only works while usb is off :'( (mounting root file system)"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by duchednier on 2007-04-11
the only way i can get ubuntu to load up after restarting or shut down, is to have the usb ports disabled (excluding mouse and keyboard they're seperate options) however i need the usb ports for various things, such as my new (and expensive) scanner, also charging my ipod is relatively important

this could relate to the mounting root file system problem, because thats what it gets stuck on when it loads up with usb enabled

please help me i need my scanner!!! ... and i'd prefer to stay on linux
(also i'm really new to linux so dont use alot of advanced terms and stuff or you'll just confuse me further ^^)

thanks for your help
-duchednier

---

### Post by mohjlir on 2007-04-12
You probably have USB enabled as a boot device in your bios. Make sure USB is lower in your boot priority than your hard disk.

---

### Post by duchednier on 2007-04-12
yeah, i tried that but to no avail. it seems that i dont even have a usb option in my BIOS, its the HDD is the first option, and then CD/DVD drive is the 2nd, but thats it.
can anybody else help me?? i'm near desperate here

---

### Post by phr0ze on 2007-04-12
Maybe it's trying to mount something that shuoldn't be, like the scanner. Have you left USB enabled, but unplug all USB devices? If that boots, plug back in just one device and boot again. Keep going until it fails.

---

### Post by Boztech on 2007-04-12
I had a similar problem with my previous motherboard.. I could not install Ubuntu 6.06 or 6.10 without first disconnecting the USB header from my internal card reader to my motherboard (Asus A8R-MVP).  Disconnecting my USB mouse/keyboard made no difference.

I no longer have this problem with my new Core 2 Duo/Asus 650i SLI system.  So it would seem to be a bug with Ubuntu and the way certain motherboards handle USB devices in BIOS.

---

### Post by duchednier on 2007-04-12
ok, i'll try that, but the mouse and keyboard DO work because in the pephirial setup, its a different setup , theres "USB something"
and then Keyboard USB and Mouse USB

i'll try that now though, but just with the scanner (because the mouse and keyboard work obviously)

---

### Post by duchednier on 2007-04-12
ok i unplugged the scanner and rebooted with usb enabled, and still, nothing >__<

aaaghhh, why is my computer so stupid!!! anyone else have any ideas??

---

### Post by x8668x on 2007-04-12
I have a similar issue.  I am running ubuntu server 6.10 and I continuously get the error: usb device not accepting address 2, error -71.
If I unplug my servswitch (belkin omniview usb KVM switch) it goes away.  Belkin offers no drivers for it so I am a bit puzzled.
Any ideas?

Thanks in advance.

---

### Post by duchednier on 2007-04-12
hmm, i'm currently switching to edgy, my friend is on the phone teaching me linux ( I know nothing about it) but he doesnt even know what to do about this

---

### Post by annda on 2007-04-12
some people have reported problems with "legacy usb" in their BIOS. i'm sorry but i can't fing the right thread at the moment. try to find the option in your BIOS and disable it. reboot.

---

### Post by Boztech on 2007-04-12
try these boot options 

>live acpi=off noapic pci=bios

---

### Post by duchednier on 2007-04-12
Tried and failed, i dont have a "legacy usb" in my bios >__<

gahh, i dont wanna go back to windows! does anyone have any more ideas or anything?

---

### Post by duchednier on 2007-04-12
ok... but... um... where are these in the bios i'm assuming? (probobly a stupid question) just those things dont seem familiar, so i thought i might run that in the terminal...:P i dunno >__<

---

### Post by phr0ze on 2007-04-12
The Ipod isn't plugged in is it? What motherboard is it? Thanks.

---

### Post by duchednier on 2007-04-13
no, i have only the mouse and keyboard plugged in >__<

what is the live acpi = off noapic pci= bios things?
where do i type them in or set them?

also,i dont know how to tell... exactlyl... what my motherboard is, but its an Acer "aspire" and on the tower it says ASE500-UP801M
i think this is the right info? maybe not? (i'm a nerd with some programs... for windows... and know nothing about the hardware, sorry)

---

### Post by duchednier on 2007-04-13
Crazy update here!

although my usb pepherials are all shut down, i plugged in my ipod and its working, i mean, i can navigate to it on my computer, scroll through all the files and everything!?!

this is a good sign, but i think its different for a scanner, is it possible to find a linux program to run an HP Scanjet G4010?

---

### Post by Frontier on 2007-11-01
> **duchednier said:**
> 
this is a good sign, but i think its different for a scanner, is it possible to find a linux program to run an HP Scanjet G4010?

It seems that this scanner is currently not supported by the XSane project; I do have the same problem working with the - otherwise excellent - scanner. :(

Any help and suggestions would be greatly appreciated.

---

