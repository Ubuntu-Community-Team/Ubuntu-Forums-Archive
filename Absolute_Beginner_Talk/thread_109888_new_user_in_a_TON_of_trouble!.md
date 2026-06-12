---
title: "new user in a TON of trouble!"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by marcusk on 2005-12-29
Hi, i'm new to ubuntu. In short, I've managed to mess up my computer so that i can no longer windows at all. :confused: The ONLY way i'm able to use my computer is by loading the ubuntu 5.1 live disk. I'll explain what i've did in detail so that perhaps someone can provide me with a solution.

I have a pentium IV 1.5GHz processor, 80 Gb HD, SBC yahoo dsl connection
I have run windows ME for several years with no major modification to partitions, bios, ect...
Recently I downloades Boot magic 8.0 partion utility to make better use of my HD space.
I succesfully created a new partion: C was the original, and the new one is the D drive. This worked fine, so I decided to try out a new OS (because windows me is horrible), requiring me to create a new partition.
I would like to mention here that everyting worked fine untill this point, and upon starting the compution, I was prompted with a screen that gave me an option of which OS to load (I only had one at this point.) 
The following steps have created a major problem. 
I created a new partion with boot magic 8.0 to install a linux OS on. It was 2.7 gigs.
Boot magic did it's thing succesfully, and from there I was promped to insert the new OS cd-rom. 
I put the ubuntu 5.1 install cd in, and everything started to go smoothly.
It went through most of the intall steps but something went wrong when it started to unpack the remaing files (???) {i think the partition was not big enought and just ran out of space, I started with 2.7 gigs and there was only 4 mb left when the installation failed.
The installation failed! and I was left with and incomplete and non working ubuntu os on my computer. 
Ok, so when I started my computer, I the Grub (boot  thing with the os's) and it gave me the choice of loading Ubunu, ubuntu recovery, some other option (i've forgotten), and Windows ME (my original OS). 
Selection Ubuntu obviously didn't work because it didn't install completly. 
Selection Windows ME also failed to work!!! Some file apparently disapeared?
At this point I could not get any os to work (except from the ubuntu live cd).
Earlier, I had created emergency disks from boot magic 8.0. These disks allowed me to edit the partitions.
What I ended up doing was deleting the new linux partition completly (in hopes that I would be left with the boot magic start screen when booting up.)
That may have created a bigger problem because upon starting the computer, the grub thing tries to load, but obviously there's nothing there because I erased the linux partition. 
With some research I've determined that I might have some problem with the master boot records (MBR) perhaps. From what I understand: Grub and boot magic are both multi boot platforms. Grub doesn't work, but perhaps I can still rescue the bootmagic start window. How do I configure the master boot records? Would this solve my problem.

Anybody that can provide help will be greatly appriciated!

Also note that I tried use the windows backup disks, but I got an error message.
A lot of files on the c drive are not backed up, so reformation is a last resort.

---

### Post by harty83 on 2005-12-29
Boot up from your windows install cd and go into the recovery console.  There type fixmbr and that should fix your master boot record so that you can boot into windows.  If that doesn't work, let us know.

---

### Post by ibook-linux on 2005-12-29
Remember to defrag your hard drive in windows before you try to set up a duel boot or you might accendently load over bits that windows need.

---

### Post by beast2k on 2005-12-29
You speak of files on your windows partition and thats aparently why you won't reformat and start again right? So the way to get around this is simply use the ubuntu live CD to backup your files from the windows partition, reformat both partitions, and at this point you may want to try to give ubuntu some more breathing room (ie:bigger partition) then install windows first followed by ubuntu you shoulden't need any third party boot loader of any kind grub will do the job.
or 
What error does windows give you when you try to boot? If you allready killed the ubuntu install then boot with your windows setup floppy and at the prompt type   fdisk /mbr   this should on boot restore the boot record in windows and enable you to boot into windows like before.

---

### Post by marcusk on 2005-12-29
Thanks for the response guys! 
I have a couple more question...
I have decided to back up my files from the windows partition. I have a dvd burner and i've got it to work with ubuntu live. I just need to know where to find the files from the windows partition. 
Your resoponse is greatly appriciated

---

