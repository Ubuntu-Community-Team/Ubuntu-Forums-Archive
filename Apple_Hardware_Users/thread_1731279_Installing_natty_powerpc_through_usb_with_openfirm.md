---
title: "Installing natty powerpc through usb with openfirmware"
date: 2011-04-17
forum: Apple Hardware Users
---

### Post by doobidoobida on 2011-04-17
Ok, my problem is this; I have a first gen mac mini g4 with a non-functioning cdrom drive and no mac os installation in place. I'm attempting to install natty (really any ubuntu OS that will work) through an external usb drive. The only functional machine at my disposal for preparing and partitioning the external usb drive is a seperate intel ubuntu box. I understand that I need to create an Apple_Bootstrap partition with  yaboot installed inside so openfirmware can recognize the usb drive as  bootable.

my question is; how do I create an Apple_Bootstrap partition on my external usb drive through a regular x86 ubuntu box? is "mac-disk" or pdisk commands available for x86 machines if not how or where could I find software to do the job?

as always all help is greatly appreciated

---

### Post by linuxopjemac on 2011-04-17
Intall MintPPC and follow the USB installation instructions.

---

### Post by doobidoobida on 2011-04-17
wow,
it seems as though you and the "dd if= of=" commands saved my skin.
it booted straight to the usb drive and it looks to be installing with no problems.

thank you so much.

---

### Post by linuxopjemac on 2011-04-17
very wise that that you followed my recipe

---

### Post by cfr42 on 2011-04-17
Does that mean you booted a ppc over usb? I thought that was supposed to be impossible?

---

### Post by linuxopjemac on 2011-04-18
I told you guys a million times before that booting a PPC based Mac off a USB stick is possible. How many times do I need to say this?

---

### Post by flatlined on 2011-04-19
Can MintPPC also be Install on and then Boot off of a Flash Drive?

---

### Post by cfr42 on 2011-04-20
Since I've only been here two minutes, I'm afraid I probably missed your earlier announcements. (I should have searched before commenting - I was just surprised having read everywhere else you-can't-boot-a-ppc-over-usb time and again.) I'll have to search for a guide :).

---

