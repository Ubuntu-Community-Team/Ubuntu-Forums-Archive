---
title: "completly new to me... please help"
date: 2006-11-30
forum: Apple PPC Users
---

### Post by johnwillis on 2006-11-30
i have recently bought a used powermac g4 - it's a beast of a machine, I have upped the memory to 1gb and installed a dvdrw drive as well as 2 x 40 gb hard drives.

my question is that i have just done a fresh install of OS X on the first drive and i want to dual boot linux on the second, how do i go about it and if i want to remove linux how do i sort that out?

i have used linux of i386 hardware, using grub as my bootloader, but i am unsure of how it works on a mac.

many thanks

john

---

### Post by Tilex on 2006-12-01
MAC or i386, i don't think it really matters; what matters is your filesystem here, not your CPU architecture.  If you have a free partition, install Linux on that partition and during the installation, it *should* detect the other OS X so it will automatically install GRUB on your filesystem in order to dual boot.

---

### Post by tubasoldier on 2006-12-01
The processor architecture does matter on a G4. It should be using a PowerPC processor. That means that it is NOT an i386. It is PPC.

---

### Post by Tilex on 2006-12-01
Of course, but this is not the filesystem.

He's asking if it's going to be the same to install GRUB on PPC than it was for i386 because he did that before.  I am replying: installing Ubuntu on PPC with GRUB (of course he's got to have the right version for his ppc architecture) should be the same as when he did it with his i386.

---

### Post by APU on 2006-12-01
tubasoldier is right!

There is a difference when it comes to PPC. 

Modern PPCs use OpenFirmware to kick-off the system startup (no BIOS) so grub does not work. Therefore you use yaboot instead which handles the choosing of which OS should boot. 

Nevertheless I would suggest to just install Ubuntu on the second partition (after havin installed OS X on the first) and then see if yaboot detects the other OS. If not it is not to hard to "tell" yaboot where to boot from for OS X

---

### Post by Tilex on 2006-12-01
Ok, so it is not GRUB, it is yaboot.  It is a different name, but still, the procedure is the same.  Dual booting with another OS does not depend on the architecture, as long as your Linux installation disk is the right for your processor architecture.  No?

---

### Post by stream303 on 2006-12-01
> **johnwillis said:**
> my question is that i have just done a fresh install of OS X on the first drive and i want to dual boot linux on the second, how do i go about it and if i want to remove linux how do i sort that out?


I'd start simple, just install Ubuntu to the second hard drive during the install.  Afterwards, just hold down the option key when booting and your mac should give you the option of which disk to boot from.

I've never dual-booted OSX and Linux on the *same* drive so I can't offer help there, but I have seen references to it here in the forums.

With all the new hardware getting installed, you might want to refresh the pram (ctrl-option-p-r) keys held down while powering up until you hear a chime or three.

---

