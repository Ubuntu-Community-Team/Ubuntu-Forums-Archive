---
title: "vbox error"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-06-29
[COLOR=DarkOrange]**im trying to get windows running in ubuntu but everytime i try to i get this error **[/COLOR]
 
A problem has been detected and Windows has been shut down to prevent damage to your computer.  
 
TRAP_CAUSE_UNKNOWN 
 
If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps: 
 
Check to make sure any new hardware or software is properly installed. If this is a new installation ask your hardware or software manufacturer for any Windows updates you might need. 
 
If problems continue, disable or remove any newly installed hardware or software. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode. 
 
Technical information: 
 
*** STOP: 0x00000012 (0x00000001,0x00000000,0x00000000,0x00000000) 
 
I believe it may be related to a bios error i get every time i start up ubuntu 
 
MP-BIOS bug: 8254 timer not connected to IO-APIC 
(though its missing a couple number at the beggining in [ ]) 
 
[COLOR=DarkOrange][B]i've managed to get it to install by pressing e when grub boots up and e on kernel and appending noapic nolapic acpi=off pci=noacpi
but the problem with that is that my computer doesn't recognise any of by usbs, very annoying for an external + wireless keyboard which both run off usb.

I've narrowed it down to needing noapic to get rid of the error but if i just use noapic then ubuntu won't boot.
[/B][/COLOR]

---

### Post by starcraft.man on 2007-06-29
I'm not sure I understand. Your getting this error in VBox or when trying to install windows as a dual boot on the physical partition?

You shouldn't be trying to dual boot in an install of VBox, I hope your not doing that. Every OS has a separate install inside a separate Machine of the VM.

[This guy had same trouble I think, not sure if it helps.]("http://www.cybertechhelp.com/forums/archive/index.php/t-3514.html") It seems to be some sort of hardware issue. What do you mean by 5 GB, any install of Windows needs more than that to run...

---

### Post by Nigmah on 2007-06-29
[COLOR=DarkOrange][B]I get the first error as i try to run windows inside of vbox.

THe other error is the one i get during bootup of ubuntu, its the root cause of my problem because if i "fix" it i can then boot up the vm.

and nevermind on the five gig thing i've deleting the vm for right now
[/B][/COLOR]

---

