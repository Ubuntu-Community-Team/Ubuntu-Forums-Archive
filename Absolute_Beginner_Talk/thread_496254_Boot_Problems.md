---
title: "Boot Problems"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-08
I downloaded the ISO burned it at 48x and it it stalled after i choose start or install option. Friend told me to re burn it at 4x and it again stalled at the same point. im not sure whatdo to or what could be wrong. 

What kinds or troubleshooting can i do if the installation feezes at the loading point?

---

### Post by phidia on 2007-07-08
Did you check the iso file for corruption before you burned it?
You should check the md5sum of the iso before you burn it.

---

### Post by JasonL on 2007-07-08
First of all I would check the CD for defects, there is an option to under "Start or Install Ubuntu" on the live CD. If that passes fine are you sure it freezes and it is not just loading?

---

### Post by FNDII on 2007-07-09
yea im pretty sure is freezes is not just loading. i left it at that screen for about 5 minutes with no HD or CD rom activity.

Im going to do the cd rom error check now.

---

### Post by FNDII on 2007-07-09
It does not seem to be able to complete the CD-ROM check either, same frozen loading bar.

I have my HD connected to the master one SATA slot and the two DVD bruners daisy chain and connected to the primary raid slot, i have no floppy drive.

Everytime i want to boot off the CD I have to go into bios and change the boot settings options from 1st drive HD and 2nd drive CD, to 1st drive CD and second drive HD.

So when I switch these options to get the computer to boot from the CD I can see the UBUNTU screen (startor install, ect). It feezes in every option except the memory test. Also the boot from HD option wont work. 


I think my problem is somehow related to how my drives are connected to the motherboard?

---

### Post by ramjet_1953 on 2007-07-09
A burn speed of 48 X is way to fast to burn ANY iso.

iso images should be burnt SLOWLY (no faster than 4 X) on high quality media.

Howevr, as you have already tried a burn at 4X, with the same problem, try booting with the no acpi command.

If this fails, dowload the alternate CD and install using this. It is not a graphical installer, but is very intutive, and you shouldn't have any problems. 

Once you have installed, we should then be able to set-up you video properly.

Regards,
Roger 8)

---

### Post by FNDII on 2007-07-09
Beginer questions in the beginer thread, whats an acpi command?

---

### Post by FNDII on 2007-07-09
well im back from work and tried it again. thelive CD still stalls after choosing Start or install option.

---

### Post by dstew on 2007-07-09
At the initial live CD screen, press F6 to get to the boot options line. You just put **noapic** on the line, then press enter. It eliminates the programmable interrupt controller module from loading. This makes the boot and Live CD session slower, but it sometimes is necessary. There are other boot options you can try also. See the Help screen on the Live CD intial page.

---

### Post by FNDII on 2007-07-09
ok i tried the NOAPIC line and still had the same problem.

also the boot from local disc option does not work

isolinux: disk error 01,ax 0201 drive 80

boot failed, press any key

I think my problem is how my actual drives are connected to the mother board?

---

### Post by FNDII on 2007-07-09
i cant think of anyhting else to troubleshoot to try and get the disk running

seems like after I choose the start or install option the CD stops spinning and there is no HD activity.

---

### Post by dstew on 2007-07-09
Go to the boot options line again, and remove **quiet** and **splash** from the line. That should let us see how the boot is failing.

---

### Post by FNDII on 2007-07-09
ok the last line that is come up with is this 

[27.262742] buffer I/O error on device fd0, logical block 0

---

### Post by FNDII on 2007-07-09
i dont know what this error is about, and dont see any help threads on it.

Wish i could just get it to boot im good with software programs just not the booting and bios side of it ><

---

### Post by FNDII on 2007-07-09
Problem Solved

I had my CD-ROM in the raid1 slot. Moved it to the primary IDE slot. When i did that it opend up more options in the Bios boot menu. Dunno if the will ever help anyone one but my problem is  solved

but now i have a new problem, not the same subject though. new thread

---

