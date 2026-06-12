---
title: "[SOLVED] Boot order"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-01-11
Hi all,I installed ubuntu last night.The boot order is still"boot from CD".I once changed it to HDD0.But i got only a black screen.When The boot from CD is restored,The system boots normally.I never faced this problem with Xp.Also opera beta is crashing like crazy.It crashes every 4 seconds or so.Can i solve these problems?

---

### Post by Joeb454 on 2008-01-11
Are you sure you've removed the CD from your drive? I know it sounds stupid, but it's the 1st question I have to ask

---

### Post by linux phreak on 2008-01-11
Yes.I have finished installing.The CD is back in the shelf.

---

### Post by Joeb454 on 2008-01-11
Are you referring to the boot order on when the GRUB menu comes up?

Or your BIOS? check the BIOS settings for the boot options (often under advanced or something) and make sure the first option is set to hard drive.

---

### Post by linux phreak on 2008-01-11
The BIOS.I usually do this after installing xp.I am not that well experienced regarding GRUB.So any help would be great.I went to bios and reverted it but that black screen comes up.The problem is that even though there is no CD,Ubuntu wants me to keep this order to boot

---

### Post by Joeb454 on 2008-01-11
What black screen? I'm trying to figure out what screen you're talking about and why your PC wants a CD to boot

---

### Post by bumanie on 2008-01-11
Could you possibly let us know how your computer is setup ie, provide information regarding the number of hard drives and partitions on each drive and where you believe each OS is situated on the hard drive/s etc.

---

### Post by linux phreak on 2008-01-11
Ok when i reset the order (first boot device)to HDD0 which is where ubuntu is installed the system boots and gets to the splash screen and the orange bar loads fully and after that i get this stupid black screen.Not even the mouse pointer.Then i have to restart using the restart button and go to bios and select the Boot form CD.After which the system boots perfectly.Hope you understands this.Thanks

---

### Post by linux phreak on 2008-01-11
I have two hard drives 40 and 160 ATA drives and ubuntu is installed on the 40 gb(primary) disk(three partitons /,/home/swap).The 160(slave) is for storage and is formatted in ext3 and is an extended partition.

---

### Post by Joeb454 on 2008-01-11
Try reinstalling Ubuntu and see what happens

---

### Post by linux phreak on 2008-01-11
THis is my third install.The thing we do to make the Live CD running(and to install ubuntu) is the problem i believe.Can editing GRUB work?

---

### Post by bumanie on 2008-01-11
What is your computer system, ie, processor ram etc.
Can you explain your bios setup. 
There is no harm in having the bios set to boot from cd if your second boot device is the hard drive with the / partition on it (as you seem to have an ubuntu only install). In fact this is a common bios configuration for those who like to use live cd's or for those who use windows and need to reinstall regularly. If there is no cd to boot, booting is passed to the next device in the bios boot order.
If everything works when bios is set to boot from cd, why not leave the bios setup that way?

---

### Post by linux phreak on 2008-01-11
Ok if there is no harm in this way,I think i will leave it like it is.Thankyou

---

