---
title: "Pre-install."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by McMagic on 2008-03-12
Ok, so this is my first time working with Linux, so im trying to play around with it through virtualbox for a while to get the hang of it. I have 2 HDD's, one 60G with my windows vista partition on it, and one 80G with some media and lots of free space. My intention is to put the virtual machine file on the 80G drive, but my concern is that Virtualbox, since it must be installed in the program files of windows, will require the machine file be local. Is this right?

If it is not possible to run a virtual machine from the other drive, perhaps there is a way i could just reformat the second drive, install ubuntu on it legitimately, and just switch between MBR's on startup?

Any help is very appreciated!

---

### Post by wolfen69 on 2008-03-12
if you install ubuntu on the second drive, it will see your windows drive and give you a choice of OS's to boot from at startup. or, you could unplug your windows drive during ubuntu install, replug it after, and then choose quick boot menu to choose which drive to boot to.

---

### Post by McMagic on 2008-03-12
So if I understand you correctly, with the Ubuntu partition set as my master boot, ubuntu will detect the windows installation and prompt me to choose OS on each startup?

Can it be this easy?

---

### Post by thisiam on 2008-03-12
You should be able to run your "virtual Disk Image" or .vdi file from the second drive. 
when you click on save as from the menu you should be able to go to the other drive and save it there, when you open it back up it should go to that location but if it doesn't you should be able to change the location to where you saved the file.

---

### Post by sciencectn on 2008-03-12
If the program isn't hard coded to install on drive C, then you can install a program pretty much anywhere as long as it is readable and writable with windows. Then the .vdi is saved on the 80 gig drive. If you want to actually install ubuntu on that drive and be able to boot it up with a virtual machine in Vista, that requires a dual boot setup.

There's plenty of tutorials on how to dual boot Ubuntu and Vista out there that are somewhat easy to follow. If you have two hard drives and Windows installed first, it shouldn't be too hard.

Linux is easy to install second in a dual boot because Linux is very well built and actually conforms to the partition you told it to install to.

---

### Post by handydan918 on 2008-03-12
> If it is not possible to run a virtual machine from the other drive, perhaps there is a way i could just reformat the second drive, install ubuntu on it legitimately, and just switch between MBR's on startup?

I'm not really clear on what you're trying to do with the virtual machine thing, but I'll address the multi-boot query.
If you install Ubuntu to the second drive, it will "automagically" install the bootloader (grub) such that it recognizes the Windows partition and makes provision to select it at boot time. Hardly anything to it.

---

### Post by glennric on 2008-03-12
You could also try ubuntu with wubi.  Do a google search for it.

---

### Post by McMagic on 2008-03-12
The virual machine idea was basically because i was trying to decide if I wanted to take the plunge, but screw it, i've got the space, and if it is as easy as installing on the second HDD and selecting the OS on startup, im pretty sure i'm going to go for it. Im moving all the media off of the 80G to an external as we speak, hopefully i'll be installing tonight!

---

