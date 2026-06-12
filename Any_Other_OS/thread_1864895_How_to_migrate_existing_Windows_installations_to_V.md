---
title: "How to migrate existing Windows installations to VirtualBox"
date: 2011-10-19
forum: Any Other OS
---

### Post by azertyfred on 2011-10-19
hello everybody!

I just bought myself a HP DV6-3160be laptop with Windows 7 and I'm trying to migrate this windows OS to Virtualbox in Linux Mint. Therefore I made a disk image (which is aprox. 36 GB) on an external Lacie 1TB USB Drive with the program Clonezilla. But I have a problem...

Every time I try to restore the disk image I get an error message which says that Clonezilla can't find the disk image in \home\partimag. I checked the disk image in Clonezilla and it's restorable. Also I used Clonezilla to restore the disk image (boot from dvd), but I read on the virtual box forum [https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows) that you can also use an app with commands (vboxmanage or st. like that) so that vbox can 'see' the disk image. Unfortunately this don't work..

I'm new to ubuntu.. is there anybody who can help me?
thx
fred

---

### Post by azertyfred on 2011-10-19
the strange thing is (I just tried it again) that clonezilla asks me at a certain point to select the disk image to restore, and the filename of the disk image appears. When I select it to restore it, clonezilla says 'unable to mount disk image...'.

---

### Post by mrhobbeys on 2011-10-20
I have done this and the reverse of this a couple of times but I have to admit unless I am doing, it is hard for me to remember all of the steps. So here goes my best shot let me know what you run into.

Copy your disk image to your machines hard drive or make sure virtual box is using its location as shared folder it is 100% easier than trying to load USBs, assuming you have the space, make sure it has full permissions I could be wrong but I think the code would be chmod /location/of/image 777 in the terminal. 

Next load up your VB and run clonezilla if I didn't forget anything or make it too confusing you should have no problem.

EDIT Rewrite for clarity:

1. Set the location of the disk image to be a shared folder. (if needed put it into a folder) - this is much easier than trying to deal with USBs when it comes to Virtualbox.
1a. if you have the space I would just move the file to your machine's hard drive.

2. Run clonezilla (try the normal process)

3. If that doesn't work change the file(s) properties to have full access by chmod to 777 - This may be total BS I think I use this when I go from Virtual Box to a real machine.

---

### Post by azertyfred on 2011-10-26
hello 
thx for the reply!
I just tried what you said, but unfortunately it doesn't work.. Clonezilla can't find the image in my shared folder because it doesn't know where to search it (it's in my shared folder). Clonezilla would look for local devices, but there's no option to let it search the image in local maps.

fred

---

### Post by Perfect Storm on 2011-10-26
Moved to Other OS/Distro Talk.

---

