---
title: "real begining Ubuntu"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by macfo on 2007-07-21
I am new to Ubuntu and all posts talk about after booting stage of starting

I have problems with booting Ubuntu for the firts time  after instaling it. I installed CD and when asked to remove CD and reboot the system, the computer after reboot tells me Error 17  while loading GRUB. I can not type anything at all. Can somebody help me with it.General spec of my PC: RAM over 500MB, HD 160GD, Processor speed 600Mhc.

After it I changed my HD and tried to install Xubuntu and I can not even install th CD because it says the same.
I have not got any other OS on this comp.



Please help/

---

### Post by nichipet on 2007-07-21
Let's start with this. When you formatted the HD during installation (assuming you reformatted it), what filesystem type did you select? Was it ext2, ext3, or something else? GRUB error 17, from what I've read, can mean you have the system installed, but GRUB cannot read it because of the filesystem type.

---

### Post by macfo on 2007-07-21
Thanks for the prompt reply

#3  ext3
#6   swap

It was suggested so I confirmed it.


macfo

---

### Post by louieb on 2007-07-21
Hum this should be an easy install something is going on.
Which CD live or text? Which version of Ubuntu 7.04 I'm guessing.
IF using the live cd do you have an internet connection? Did you run the check CD for defects option?   
If you have the live CD and the internet works with it.
open applications>accessories>terminal and run ```
sudo fdisk -l
``` (lowercase L) and lets have a look at your partition table. cut and paste the output here.

---

### Post by macfo on 2007-07-21
I tried both

the error 17 is on the install version

on the live version at the end of the instalation process user authorisation fails (so I amnot even able to see wther internet works) probably not as network hardwae is not recognised (failed too)

Ubuntu 5.0 version ( when I want to install the latest it is the same error before it even starts reading CD

Waiting for saving my life

regards
macfo

---

### Post by armandh on 2007-07-21
be sure that the cd boots first and you select it [if needed]
that you see the same error with the cd in or out causes me to think you are booting from the Hdd first

---

### Post by macfo on 2007-07-21
llive version fails at the user uthorisation and nothing can be done 

and instal version  is GRUB error 17.

CD is selected just after floppy flopy slot is empty enyway,

Any more advice or suggestions  please??


Do you think that using super grub will helps (I found it somewhere however don't know what to do with it)
regards
macfo

---

### Post by louieb on 2007-07-21
Your not being very clear about what you have done or what the installer did. 
I'm going to go slow. 1st question: When you  boot with the Live CD do you get a desktop with an icon that has install under it?

---

### Post by macfo on 2007-07-21
Sorry for being not clear (but I am un clear for myself too) I will explain from the begining:

I did 2 things and ether of these worked


1.   I tried live CD. It failed at the stage of user authorisation (or autantification I am not sure) therefore I didn't even get the desktop with icons (to answer your question)

2.   I tried install CD (during this process I reformatted the HD living 100GB for Ububtu)  I managed to installed it and removed CD from the slot and rebooted the system.The system stopped with the message:

GRUB loading please wait
error 17 

I was not able to do anything at this stage.

Regards
macfo

---

### Post by louieb on 2007-07-21
So you never got a desktop with the live CD. Is this a Shippit CD or did you burn it? If  you burned it how did you do it? If you did not run the media check option stop and do it now.  [BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto")

The Grub error 17 makes me think Ubuntu is installed but for some reason the GRUB boot loader install failed.  The easiest way to fix that is to use the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/"). You burn it to a CD. Use the how to above. Then after you've got a Super Grub CD. Go to [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) Herman has an excellent writeup on how to use it. In fact cruse his how to install Ubuntu with the alternate CD I think you will find it helpful.

---

### Post by macfo on 2007-07-21
Hi
You are right I never sw the desktop with the live CD

CD was shipped

I also burned super GRUB CD but the system didn't even read CD with the super GFUB and gave the same message:  Error 17 without even looking what I had prepared for it on the CD.

I thought about floppy but in my other comp (the one that works on Windows and internet connected, there is no floppy slot at all)


regards
macfo

---

### Post by louieb on 2007-07-21
You have to get that computer to boot a CD.  Please check the boot order in BIOS and make sure the CD drive is 1st  in the boot order. Then  try the Super Grub or for that matter any boot able CD you may have.

---

### Post by macfo on 2007-07-21
Thanks

I have tried it again as per your advice and it shows me  similar message: error 18 now but stage 1.5 againin GRUB loading (in other order)

CD is set as the bootable first but the screen with the nessage appears as if ready very promptly just after detecting HDs?

I am not sure how to make the somp slow down to read CD and install super grub, BIOS seems points for sure CD

Any sygestions?
regards
macfo

---

### Post by louieb on 2007-07-21
Grub error 18 is bad news. It means the BIOS can't boot  to program that is outside the 1st 1,000 cylinders (about 8 gig) from the start of drive. Your looking at reinstalling using manual partitioning and setting up a /boot partition at the start of the hard drive.    

Its not that hard, but **until you get it booting to a CD your stuck.**  

1st check you BIOS if you don't know how to get into the BIOS setup try the things listed here [PuppyLinuxWiki: BootingFromCD]("http://puppylinux.org/wikka/BootingFromCD")
2nd read up on partitioning  here are two places to start.
 [Disk partitioning - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Partition_%28computing%29")
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by macfo on 2007-07-22
Hi many thanks for your help.

Somehow I managed to start up instalation disk and reformatted partitions tolook at the begining cylinders only (first 8 Gb) It bootd and is instaling the Ubuntu as we speak.

Question?  If I resied partitions after instalation to  use more space (160 Gb) would the Grub work properly or it will start the game again. I mean would it be able to read large disk.

By the way I think that my BIOS is not working well as the booiable devices didn't work as I set it tp.

Please advice if I should resize the partitions later on?

thanks again
regards
mavfo

---

