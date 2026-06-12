---
title: "add to yaboot.conf 3rd distro?"
date: 2006-06-26
forum: Apple PPC Users
---

### Post by Uta on 2006-06-26
My iBook G4 is a dual boot, Dapper and Tiger. At boot I get a menu where I enter "L" for Linux or "X" for MacOS or "C" CD  what I want to do is install a different distro on an external firewire drive connected to the iBook. I would of course need to edit the yaboot.conf to add this new distro on the FW HD.
Has anyone done this and if so I would like to know what you did when you got to the boot loader part of the installation. Any howtos or tips would be appreciated. Thank You.

---

### Post by digs on 2006-06-27
I recall someone had sucess with simple copying the 3rd OS's yaboot config info into the 2nd OS's yaboot config - you press "L" for linux and then yaboot would provide another menu to select which linux os you wanted to boot into. Or you can change the mac-boot variable in nvram to multi-boot and you can then select which OS you want to boot into  - I know this works as I've tried it.

---

### Post by Uta on 2006-06-27
I do not know how I lost my dual boot setup.
All I did once I was booted in Linux was to look at the yaboot.conf file and print it and saved a copy to my desktop. I "thought" I did a "save as"?
I have lost the capacity to get a OF prompt where I can type "L" or "X" for mac os. It now boots directly into Mac OS. I tried  changing it to: setenv auto-boot? false reset-all but all that does is give me an OF prompt but no options to boot from.

How do I get back my boot options. Thanks!

OK-I have my dual boot back by zapping PRAM.
My question is:

If you load a 3rd distro on a firewire drive, where exactly are the boot parameters that need to be written into the yaboot.conf file? If the mutlit-boot is the way to go, are there HowTos where? Thanks.

---

### Post by Uta on 2006-06-27
I have had great success with adding a 3rd distro on to a firewire drive and having all 3 boot options placed in yaboot.conf
This is thanks to the great developers of Ubuntu/Kubuntu for PPC. 
Thank you. 
I had wondered if after I installed Kubuntu on the firewire drive that when it wrote the bootloader that my Ubuntu distro would not be added and I would have to edit yaboot.conf but the brilliant litter installer did all the work. At start up I have a prompt for "L" or "X"  or "C"
If I choose "L" I get a boot prompt, if I do nothing or hit enter it defaults to Kubuntu on the FW HD but if I enter "hda4-Linux" I get my Ubuntu distro.
I am truly amazed.
My install order was Mac OS, then I resized the HD and installed Ubuntu, which I lived with for about a month and then decided to take the "install to an external drive" challenge and it was painless.
This was all done on an iBook G4 with wireless card.
Again thanks to all the developers for their great work!

---

### Post by digs on 2006-06-28
You're not saying you installed ubuntu & kubuntu on separate partitions, are you? That is a waste of space and time. ubuntu/kubuntu allows multiple desktop environments, ie, you can install the kde desktop onto ubuntu and vice versa (just run "sudo apt-get install kubuntu-desktop"). You can select which desktop you want on the GDM login screen/panel.

---

### Post by Uta on 2006-06-28
It was not a waste of space or 'my time', it was a lesson in learning to install a linux distro to a firewire drive.

---

