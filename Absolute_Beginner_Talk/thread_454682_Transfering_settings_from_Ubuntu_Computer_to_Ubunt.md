---
title: "Transfering settings from Ubuntu Computer to Ubuntu Computer"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-05-25
I have several computers, and basically I really want to know how I might be able to transfer all of my settings from my original Ubuntu computer to other computers in an efficient way. I do not want to have to re-install Ubuntu on each computer and then have to re-configure GNOME and other things every time and have to re-download the upgrades. I have checked out MigrationAssistance but it only seems to help migration from other operating systems. I ideally would like to be able to make an install CD or DVD from my original Ubuntu computer with all of my settings, and then install it on all my other computers. I do not care about my personal files, just the settings of the Operating system and the software I have installed. I would greatly appreciate any help you can give. Thank you
:popcorn:

---

### Post by init1 on 2007-05-25
Ok, one of the best ways to do this is with hard drive images. With Partimage, you could make hard drive images with the maximum size of 690 so that you could burn them to CD's. Hard drive images are exact copies of your hard drive that Partimage can assemble and copy to a partition. It would not matter what OS was one the target computer. I recommend using RIP linux to do this, since it has Partimage already with it.
Steps:
Make images of source partition with Partimage
Burn images to CD's
Put images on target computer (in another partition)
Boot RIP linux and use Partimage to copy images from their partition to the target partition. Remove the extra partition that you created for the images
Reboot
The OS of you target computer should look exactly like the OS of your source computer

---

