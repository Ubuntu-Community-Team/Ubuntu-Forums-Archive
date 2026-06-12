---
title: "Help again"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-03
Hi.

I posted a thread earlier today, where i needed help to boot into ubuntu. [http://ubuntuforums.org/showthread.php?p=2951767#post2951767]("http://ubuntuforums.org/showthread.php?p=2951767#post2951767")

But now my problem is that i can't get into the CD without installing. How can i get into the live CD so that i can do as the guide says?

---

### Post by orb9220 on 2007-07-03
Your computer must support** Boot from CD** in the bios. That is turning on the computer and hitting the appropriate key to enter **Setup** also know as bios setup screens.

This is usally the **del** key or **F1** or esacape key. Then look thru menus for **Boot Order** which will usually show three devices. The first usually being floppy which you would change to Cdrom or it may say removable device. After cdrom is set as 1st device then save and exit bios with the cd in the drive. It should then boot the cd.

Make sure when you burn the iso that it is burned as a image to cd or burn iso to disc. **Not ** make a bootable cd.

---

### Post by starcraft.man on 2007-07-03
> **orb9220 said:**
> 
This is usally the **del** key or **F1** or esacape key. 

On other BIOS its common (My IBM and Dell were examples) to have a key that takes you to a selective boot loader (you can pick for the one time which device to boot from rather than the boot order, USB, CD or drive). F12 or F10 are the common ones in my experience.

If you don't see these options in the setup or a separate section, the BIOS I guess doesn't support it.

---

### Post by czepluch on 2007-07-03
Thanks, but that much i know. 

The problem is that when i boot the CD i can't choose the LIVE CD. I can only choose to install and i don't need to cause it is already installed.

I need to make the GRUB again. PLease help

---

### Post by corney91 on 2007-07-03
> **czepluch said:**
> Thanks, but that much i know. 

The problem is that when i boot the CD i can't choose the LIVE CD. I can only choose to install and i don't need to cause it is already installed.

I need to make the GRUB again. PLease help

Are you sure you don't have the Alternative Install CD rather than the LiveCD? This will install without loading Ubuntu up first.

---

### Post by czepluch on 2007-07-03
> **corney91 said:**
> Are you sure you don't have the Alternative Install CD rather than the LiveCD? This will install without loading Ubuntu up first.

What du you mean by that ?

---

### Post by starcraft.man on 2007-07-03
> **czepluch said:**
> What du you mean by that ?

I don't follow. If you installed correctly either live or alternate CD, you should have GRUB installed to the MBR and giving you the choice to boot into linux. Remove the CD and boot up what happens? If the GRUB is damaged or wrongly installed, then [restore it from the live CD.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by czepluch on 2007-07-03
> **starcraft.man said:**
> I don't follow. If you installed correctly either live or alternate CD, you should have GRUB installed to the MBR and giving you the choice to boot into linux. Remove the CD and boot up what happens? If the GRUB is damaged or wrongly installed, then [restore it from the live CD.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

As it says : Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

I cant boot in to the live Ubuntu disc. Thats my problem

---

### Post by starcraft.man on 2007-07-03
> **czepluch said:**
> As it says : Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

I cant boot in to the live Ubuntu disc. Thats my problem

If you can boot the CD from the BIOS but your only option is to install then your using the Alternate install Disc (it doesn't support booting Live, its just a text installer). If you could boot into a Live CD before but now you can't from the menu, the media must be scratched/damaged.

Either re run the install from that disc since you have no GRUB (means you can't boot into console to fix it) or download and burn the [Live CD.]("http://www.ubuntu.com/getubuntu/download") Those are the options given what you've told me.

---

