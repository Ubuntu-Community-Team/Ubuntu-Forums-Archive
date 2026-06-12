---
title: "Dapper install..."
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Peter F. on 2006-05-12
I've tried Dapper 6.04 with the 'live' cd but it stops after a few seconds.
Does anyone know what to enable/disable in my bios?

Uncompressing linux...ok, booting the kernel
MP-Bios bug: 8254 timer not connected to IO-APIC
PCI: Cannot allocate recource region 0 of device 0000:00:11:0

Thanks!! Peter F.
PackardBell W3420/1GB/Radeonxpress200

---

### Post by skippy81 on 2006-05-12
Laptops are funny things :p But don't worry your problem is a common one, and linux can work around it. You need to tell the kernel not to use ACPI when it boots.  

I only have the installation CD, not the live version so you may have to adapt this procedure:

1) Press F6 for boot options

2) Add the phrase "noapic nolapic" to the end of the string of text that appears at the bottom.

3) Press enter.

This should work, if it doesnt then keep fiddling. Try deleting a few of the dash (-) symbols at the end of the text string.  You could also try adding "noacpi".

There is a tiny chance you will get a different format - a prompt which says "boot", just type "linux noapic nolapic" after it if this is the case.

If this still isnt working, you could try the BIOS, diable APIC if you can find it as a setting (APIC stands for Advanced Programmable Interrupt Controller ;) )#

Good luck, report back if you have probs.  Let us know what sort of menu the CD offers you when you boot from it, and what the option keys are.

---

### Post by damianubuntu on 2006-05-12
I've no idea how relevant this is ;-) but have you tried the Breezy live, just in case its a Dapper bug rather than anything to do with your box?

Edit:  (to me!) if you don't know, don't just guess wildly!  Someone else might know what they're talking about :-#

---

### Post by Peter F. on 2006-05-12
Thank you 'skippy81' for the detailled info , and... you first option was great.
The noapic option made the first problem go away and made me go a bit further on the live-cd.
Still it now stops at: mounting root file system , and after a minute or so I get: Buffer i/o error on device hdc , logical block 158576

ps. unfortunatly I can make no changes in the bios , packard bell doesn't seem to like customers fiddling with it..
No options for disabling sound,wifi or anything..

Thanks for your help!


<Damianbunto>
I also tried breezy but there it stopped at 'hotplug subsystem'
But still rather go ahead with Dapper because a new release always should be better.
Thanks anyway...

Regards...Peter F..

---

### Post by skippy81 on 2006-05-12
> Buffer i/o error on device hdc , logical block 158576

hdc = the first CD-ROM drive on the ide bus.  

This suggests to me that the problem could with your live disc - is there any way you can test it by burning another one?  I havnt used windows for a while, but if you have it installed maybe you could see if there is a way of running "scandisk" on a CDROM - that would test both your disc and your drive for optical errors.

---

### Post by Peter F. on 2006-05-12
Great , but the live cd works fine on my son's Dell Inspiron 6000 ! grrrrr... :)
(both breezy and Dapper!)
So...I can still get an impression from Dapper 6.04 and I really like what I see.
Unfortunatly a long as I do not have it working on my PackardBell W3420 I do not want to take the risk of installing it and erasing WinXP....

Regards... Peter F.

---

### Post by Peter F. on 2006-05-13
Stupid question: unmounting hdc would not be an option, would it?
But then, dapper will not install because the DVD does not work....!?

regards..Peter...

---

### Post by skippy81 on 2006-05-13
Nope thats not an option.  Here are a few more boot parameters to experiment with:

nobiospnp

nopcmcia

nousb

Try and get into the BIOS, disable acpi, pnp, and apci from there if possible.

---

### Post by Peter F. on 2006-05-13
Thanks!  :-D   I'll try asap and let you know if this helps.
I can get into the bios but the bios will not let me change anything! No options for disabling pnp,acpi etc.

best regards... Peter F.

---

### Post by skippy81 on 2006-05-13
Have a look around the HP website and see if you can get a BIOS flash upgrade.  Usually the early BIOS revisions which ship with PCs are very weak, and a lot of the 'advanced' features are badly implemented.  For example, my Asus board couldn't use cool'n'quiet until Bios version 6 came out - and the thing was sold with "C&Q Technology" all over the box lol.

---

### Post by Peter F. on 2006-05-13
Good idea , i've flashed the bios to the latest version but that did not help.
Still no option for disabling hardware...
So...tried nobiospnp,nosound,nousb etc.
It still hangs,  I get the ubuntu splash screen and get past 'loading essential drivers' ok
Then 'mounting root file system' and after one or two minutes I get the black screen with the message: Buffer i/o error on device hdc , logical block 158576
The problem seems to be the mgs I get when loading the kernel ; 
PCI: Cannot allocate recource region 0 of device 0000:00:11:0

Well maybe I'm lucky when Dapper is out of beta...

Best regards... Peter F.

---

### Post by Peter F. on 2006-05-13
Well Skippy81 , I've tried another distibution named pclinuxos .92 and that worked.
It recognised the Radeon xpress200 chipset without problems.
And...whilst it was booting I saw the same pci problem when the kernel was starting.
BUT....there was a tip (try pci=biosirq)
I've tried to boot with that option but no go. Or do I have to add an irqnumber to that command?

Thanks anyway...  regards Peter F.

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=Peter F.]Great , but the live cd works fine on my son's Dell Inspiron 6000 ! grrrrr... :)
(both breezy and Dapper!)
So...I can still get an impression from Dapper 6.04 and I really like what I see.
Unfortunatly a long as I do not have it working on my PackardBell W3420 I do not want to take the risk of installing it and erasing WinXP....

Regards... Peter F.[/QUOTE]

The Dell Inspiron 6000 might not be a good system to compare installs on, because I have installed breazy on mine, and so far havn't experienced any problems that users of other laptop models report. In fact on this machine in particular it was easier to install than windows. Wireless, ATI video card, function keys worked right out of the box with Breazy.

---

### Post by Peter F. on 2006-05-13
Your right on that one, snowman..
I want to install Dapper on my PackardBell W3420 but do not dare to take the risk.
I tried my son's Dell 6000 to see if the livecd's for breezy and Dapper were working without errors.
And they both worked fine on his laptop, sound, ati etc.... and no! I'm not going to trade laptops with him :) 

Regards... Peter F.

---

### Post by DSn0wMan on 2006-05-13
You might try [http://www.linux-laptop.net/](http://www.linux-laptop.net/) thats how I figured out that Ubuntu was one of the better distros for my laptop. I didn't see a link for PackardBell, but you may be better at poking around for a solution.

Lots of linux users post to linux-laptop with issues specific to their hardware.

good luck!

---

### Post by skippy81 on 2006-05-13
yes "pic=biosirq" is yet another kernel option, definately worth trying it, perhaps the combo 

> noapic nolapic pci=biosirq might work.

---

### Post by 5-HT on 2006-05-13
[quote= Peter F.]BUT....there was a tip (try pci=biosirq)
I've tried to boot with that option but no go. [/quote] 
A little stabbing at the dark...but 'pci=noacpi' helped me get around an IRQ issue with my cd-rom drive that prevented  proper booting (pci=biosirq didn't help me).

Another one to try may be 'irqpoll'.

---

