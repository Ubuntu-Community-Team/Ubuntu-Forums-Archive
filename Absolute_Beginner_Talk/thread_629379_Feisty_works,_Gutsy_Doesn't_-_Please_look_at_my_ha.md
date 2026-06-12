---
title: "Feisty works, Gutsy Doesn't - Please look at my hardware"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2007-12-02
Well - this is the second time that I have attempted to upgrade to Gutsy.  All goes well.  The install is fine.  I am amazed b/c Gutsy even fineds my second hard drive and allows me to boot into XP.  

Once the install finishes it tells me that I have 93 packages that can be upgraded.  I tell it to upgrade the packages, and it downloads everything fine.  Every single time it crashes saying that the .tar is corrupted...  I tried installing Envy w/o any of the updates, and that say that the file is corrupted.

I ruled out the onboard NIC - I plugged a NIC card in and re-installed.  Same prob.  I burnt a new CD - same problem.  Basically - last time this happened I had to revert to Feisty...  I can run Cedega, surf, burn cd's all on Feisty.  Gutsy will simply not allow me to install anything that is not off of the CD...

I know that my hardware is good - as it runs XP and Feisty - so this has to be a Gutsy issue...  Maybe soemone else has experienced similar issues.  Here is my hardware:  Any thoughts??  Remember - this ONLY happens of GUTSY!

ASUS MN2-E NFORCE 570 ULTRA
2 GIG OCZ PLATINUM DDR
#2 LITE-ON SATA CD/DVD BURNERS
SEAGATE 500 GIG SATA HD
SEAGATE 160 GIG SATA HD (XP OS ON 2ND DRIVE)
NVIDIA 7600GT

---

### Post by mahiyar on 2007-12-02
What about trying a fresh install.

---

### Post by jeepfreak2002 on 2007-12-02
I did 4 completely clean installs.  I nuke my partition and install on a completely clean partition.

---

### Post by mahiyar on 2007-12-02
Sorry, what I meant by fresh install is download the iso again, 93 packages to upgrade means a pretty old iso.

---

### Post by jeepfreak2002 on 2007-12-02
downloaded the .iso last night from Ubuntu's site.

---

### Post by mahiyar on 2007-12-02
Thats staring at a blank wall. From edgy to gutsy there might be some issues that need a little tweaking but none so serious enough that you describe. What about live cd? can you run gutsy on live cd?

---

### Post by jeepfreak2002 on 2007-12-02
Yeah - I can run the OS just fine.  That is the weird thing.  The OS INSTALLS just fine.  It's just when you to run package updates, or install something like Envy which is downloaded, and no coming from the install CD.  I even replaced the NIC and network cable!!!  I downloaded the .iso on a different PC to rule out a bad image too!  

This is so damn weird, and it is repeatable.  This happened a couple of months back when Gutsy first came out, I tried and experienced the same problem.  I had to reinstall Feisty.  

I know that the system is fine b/c on Feisty I can run Guild Wars on Cedega and there is no download/install corruption AT ALL!!!

---

### Post by srt4play on 2007-12-02
Can you post the exact error about .tar being corrupted?  Maybe it would help to know what package is being installed when it fails.  Also do some testing with your tar utilities (create and extract some test archives), if you can't create/extract a test archive maybe you need to reinstall tar.

---

### Post by jeepfreak2002 on 2007-12-02
the prob is that it is whatever .tar is being used at any given time...  not a specific one.  It just give the directory /usr/xxx/xx  .tar is corrupted.  I can post an example later - I am at work on a different PC right now,

---

### Post by mahiyar on 2007-12-02
Well the obvious answer would be to uninstall and reinstall the tar package through synaptic, you can try that, but faulty tar package does not explain things like how come each time you have landed up with a faulty tar package only. The attention next turns to your downloading process.

---

### Post by mahiyar on 2007-12-02
On second thoughts can you download some tar package like from your office and see if it opens on your gutsy, then downloading the same in gutsy to see what happens?

---

### Post by jeepfreak2002 on 2007-12-02
> **mahiyar said:**
> Well the obvious answer would be to uninstall and reinstall the tar package through synaptic, you can try that, but faulty tar package does not explain things like how come each time you have landed up with a faulty tar package only. The attention next turns to your downloading process.

except for the fact that the "downloading process" is being conducted through Synaptic...  There is a problem with either the hardware and the OS, or the OS itself...

---

### Post by jeepfreak2002 on 2007-12-02
> **mahiyar said:**
> On second thoughts can you download some tar package like from your office and see if it opens on your gutsy, then downloading the same in gutsy to see what happens?

I can try.  Suggest a program file or shoot me a link and I can do that right now.

---

### Post by jeepfreak2002 on 2007-12-02
E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: corrupted filesystem tarfile - corrupted package archive

blammo - now this was on a clean install...  I am now going to flash the mobo's BIOS...

---

### Post by deadgobby on 2007-12-02
Are you installing the 32 bit or 64 bit Ubie?

---

### Post by jhetrick62 on 2007-12-02
I would suggest a non-graphic install and see if this problem errupts without the nvidia drivers being loaded or any xorg running. If you can install and boot into runlevel 1, then update all packages, you can set xorg.conf to boot into vesa and then manaully apply the latest Nvidia settings.

Just a guess though, but video issues seem to be the biggest install issues that I see.

Jeff

---

### Post by jeepfreak2002 on 2007-12-02
E: /var/cache/apt/archives/openoffice.org-help-en-us_1%3a2.3.0-1ubuntu2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/help/en/scalc.idx/DOCS')


more errors - This time I am trying "LinuxMint" a tweaked distro of Ubuntu...  same prob...

---

### Post by mahiyar on 2007-12-03
The 64 bit question was a valid one. Another thought is have you disabled swap by any chance? Are you sure your swap is ok?

---

### Post by jeepfreak2002 on 2007-12-03
Here are crashes right out of a clean install.

E: /var/cache/apt/archives/openoffice.org-help-en-us_1%3a2.3.0-1ubuntu2_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/openoffice.org-l10n-en-gb_1%3a2.3.0-1ubuntu2_all.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/openoffice.org-l10n-en-za_1%3a2.3.0-1ubuntu2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/resource/rptui680en-ZA.res')


I have no idea how to disable swap.  I use a guided install that creates brand new partitions on a new HD.  This is on an AM2 Athlon X2 system...  I would have assumed that it was a 32 bit install.  I did not specifically install/download a 64 bit version, although the CPU is capable of 64 bit.

Oh, and I realized last night 
- Feisty never worked either...  I have not been able to get anything newer than Edgy to work...  I put off updating until Gutsy thinking that there was a prob with Feisty when I tried 6 months ago.  I just updated my MOBO BIOS and that did not fix anything either...  Looking at firmware for the DVD burners now

---

### Post by crjackson on 2007-12-03
how much HD space do you have on that partition after the install?

---

### Post by jeepfreak2002 on 2007-12-03
It is on a 500 gig hard drive.  Plenty of room

---

### Post by jeepfreak2002 on 2007-12-05
So the culprit was my RAM...

I am running #2, DDR2 800 OCZ Platinum 1 Gig sticks in my machine...  I decided to remove 1 stick and run in single channel mode - BLAMMO - everything runs fine.  So then I lower the clock speed of the RAM to DDR2 667, with both sticks in Dual Channel - It Worked!  Somehow After Edgy the Kernel must be using the Dual Channel more extensively and the memory just did not play happily w/ my MOBO at stock speed.

Weird thing is that my Windows always ran stable at stock speed, but hey, whatever.  Gutsy is happy, I am playing Guild Wars, and I am happy.  

NOTE: nForce 5 series is RAM picky - slow it down a notch or pull a stick out and see if that fixes your probs!!!

---

