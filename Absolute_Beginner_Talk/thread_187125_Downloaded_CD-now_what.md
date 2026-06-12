---
title: "Downloaded CD-now what?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by kkkkk on 2006-06-02
I downloaded the live CD and restarted my computer. Then clicked on the stored CD on my desktop to start it. CD will not start. Can anyone guide me what to do? In addition, I am wondering if there are any users in the Ann Arbor/ Detroit region. Replies appreciated.

---

### Post by carlosqueso on 2006-06-02
Not anywhere around there, but you must burn the live CD image to a CD first.  Follow the directions here [https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29)

Then restart your computer and you'll be set to go.

---

### Post by mscman on 2006-06-02
You need to burn the downloaded CD image to a disc.  Nero does this (just select "burn image to CD") or if you want a free program to burn disc images in Windows, try searching for DeepBurner.  You then have to restart your computer with the CD in the CDROM drive to start it.

---

### Post by blackjack6.21.91 on 2006-06-02
Ok.  Your supposed to burn the .iso to a CD (that's what you downloaded, right?).  After that, pop the CD in to your computer and restart.  When you are at the beginning menu right when your computer turns on, press F12 to configure what is booting.  Choose your CD drive.  You should then be greeted with a menu of options below an ubuntu logo.  Press enter on load the live CD

---

### Post by kkkkk on 2006-06-02
Thank you for your fast replies. I do not know how to "dual boot". What do I do after I press F12 to configure what is booting?
Sorry guys, but I am no geek. Pretty new to Ubuntu.  I appreciate your help guys.

---

### Post by lapsey on 2006-06-02
it varies from computer to computer: when your machine powers up there is usually a message telling you to hit F12, Alt-F1 or Shift-Delete (or similar) to go into BIOS. 
Your BIOS settings control what the hardware does on its own - this includes the devices it goes through looking to boot from.

Most people have the boot-up sequence to go in some order like
CD-ROM
Hard Drive
Network
so that if there is no bootable cd in the drive it will boot from hard drive, if no system is in the HD it will look on the network and so on. So, it needs to be set so the system boots from cd rom first.

Once the BIOS is correctly configured and the machine restarted, the system should boot from the CD, and if all goes well, once you're in the live CD environment you can use the graphical installer to automatically create a seperate section on your HD for ubuntu and it will install to that.

Dual-boot means that there is a piece of software at the 'start' of the HD so when the machine boots into the HD the software (grub) allows you to choose between Ubuntu and the other operating systems on the HD. :)

---

### Post by r4ik on 2006-06-02
You could give this one a read it's all there,

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

Good luck !

Edit: just use the parts you need and save the rest for (perhaps) later :)

---

