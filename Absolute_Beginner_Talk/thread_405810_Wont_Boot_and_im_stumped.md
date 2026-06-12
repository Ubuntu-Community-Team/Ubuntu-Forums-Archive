---
title: "Wont Boot and im stumped"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by RedGretsch18 on 2007-04-10
OK so here are my specs 
MSI w6738 
nvidia 128mb geforce videocard
Amd Athlon 1.1 ghz
384 ddr2 Ram
I feel like luke skywalker lol stepping in to techy adolescence and building my own machine from scavenged parts. This is my first time installing an OS and im very very new to linux here's the story
      So, i installed ubuntu edgy eft on my machine then, when it restarted the OS wouldnt load and i would be forced to boot from the live cd. so i tried to boot from the hard disk off the live cd and got this error isolinux: disk error 05, AX = 0000, drive 80. i have no idea what to do and i would love for ubuntu to work. why wont it load whats going on eeeak. btw i tried using ubuntu 6.06 to no avail.

---

### Post by wpshooter on 2007-04-10
Can you put the Edgy CD in the drive and boot to the initial Ubuntu/Edgy boot menu ?

Does this machine have any other O/Ss on it ?

---

### Post by HereInOz on 2007-04-10
Not my area of expertise, and the only reference that I can find by googling that error is a post on the Ubuntu forums in German, which does not translate very well.

forum.ubuntuusers.de/topic/79130/

From what I can gather it appears to be a hardware problem, possibly related to the HDD but it could be IDE cable, motherboard issues, all sorts of stuff.

Sounds like you may have a bit of a headache there, if you don't know what the cause is, although, if the live CD runs, but the install fails, then it looks a little like the Hard disk may be the source of the problem.

Can you put that hard disk in a known good machine, even just hang it off the side while disconnecting the installed drive, and see if you can install to it?  Often this is the only way, to put the suspect part in a known good machine, and see what happens, because at the moment, you could be chasing your tail not knowing what bit is causing the problem.

---

### Post by RedGretsch18 on 2007-04-10
yeah i can boot from the live cd but without it i cant get past this prompt
Boot Cd:

---

### Post by wpshooter on 2007-04-10
Did you have any problems during the installation to your hard drive ?

Does this computer have any M/S windows O/S on it ?

---

### Post by RedGretsch18 on 2007-04-10
No other systems were on it and install went very smoothly

---

### Post by dstew on 2007-04-10
What happens when you try to boot the hard disk directly? Do you get the grub menu? Have you made your hard disk bootable in your BIOS?

---

### Post by RedGretsch18 on 2007-04-10
i get something that looks like this
 phoenix award bios energy star

base mem 360k + 24k
detecting ide...

primary master hdd 120
primary slave...
secondary master 48x12
secondary slave...

Then that page goes away
followed by some more specs with
update escd success
Verifying dmi data 
Boot Cd: 
i get this message no matter how the boot sequence is changed even if hd0 is first

---

### Post by dstew on 2007-04-10
So it stops at the Boot Cd: message? Do you still get the isolinux error message? Maybe it trys to boot the hard drive, then gives up and defaults to try to boot the Cd.

Sounds like you have no booter in your hd0 MBR. Did you install grub?

---

### Post by RedGretsch18 on 2007-04-10
Not that i know of where do you get it because the hd was completely blank do  can i download grub i though it would be on the ubuntu cd

---

### Post by dstew on 2007-04-10
Yes, it is on the Ubuntu CD. It usually installs itself, unless there was some error, or you told it not to. What Ubuntu did you install? Was it the 64 bit or 32 bit?

It would be good to see how the live CD linux system sees your disks. That may give us a clue as to why the hard disk will not boot. To do this, boot the live CD, open a terminal window (in Applications menu I think) and enter the command

**sudo fdisk -l**

That will list your disks and partitions. Post the result on this forum.

---

### Post by RedGretsch18 on 2007-04-10
i booted the 32 bit and ill fdiskas soon as i can would it be a good idea to get the super grub disk

---

### Post by RedGretsch18 on 2007-04-11
k here it is

Disk /dev/hda: 120 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
unit = cylinders of 16065 * 512 = 8225280 bytes
      

           Device Boot   start         end             blocks                 Id         system

/dev/ hda1     *        1              14465          116190081        83          linux
/dev/ hda2               14466       14593          1028160            5           ext   
/dev/ hda5               14466       14593          1028128           82          linux swap/ solaris

---

### Post by dstew on 2007-04-11
Your disk partitions look OK. I think for some reason you have no booter installed. I recommend that you install grub. You can do it from a live CD session, or from a SuperGrub bootable disk (CD or floppy). From a live CD, open a terminal and enter grub at the command line. If you have a bootable SuperGrub disk, get a grub command line by entering 'c' at the menu.

Once you have the grub command line, make sure you have the grub files on your hard drive by entering **find /boot/grub/stage1**. It will return with the name of the partition on your hard disk where this file lies, in grub form. In your case this will almost certainly be (hd0,0).

Then, make this partition grub's root by entering **root (hd0,0)**. Last, set up the grub boot loader by the command **setup (hd0)**. After this, remove the grub disk and enter **reboot**.

---

### Post by RedGretsch18 on 2007-04-11
if the bios is broken would it not boot the system because i ran a firmware check and it failed on just about everything

---

### Post by dstew on 2007-04-12
Yes, an intact BIOS is needed for the boot process. Grub uses the BIOS to access disks. Did you try to install grub yet as I posted earlier? The responses of the grub program will give us more clues about the problems you are having. That is, if the BIOS is bad, we might see some grub messages that tells us that. However, since you were able to partition, format, and install linux, I think the BIOS that deals with your disks is probably OK. Let's try to install grub.

---

### Post by RedGretsch18 on 2007-04-12
I Installed opensuse 10.2 and the same thing happened

---

### Post by RedGretsch18 on 2007-04-28
Well Everyone Im Very Glad to say the the problem was a mere Hard drive issue when i bought a new one everything got fixed proud linux user yeehaw

---

