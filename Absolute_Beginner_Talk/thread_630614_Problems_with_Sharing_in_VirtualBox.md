---
title: "Problems with Sharing in VirtualBox"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by mikebeecham on 2007-12-03
Hey  guys, I wonder if there are any VirtualBox gurus out there...

I am running Gutsy Gibbon, and have a secondary internal hard drive mounted.  Within Linux, I can read and write to all of the shared folders within this second hard drive.

I have installed VirtualBox, in order to run WindowsXP, and have allowed it access to the second hard drive.  When I go into my WindowsXP, I can see and access all those folders on the second hard drive just fine.

However, it wont let me write back to those folders for some reason...it tells me that the disc is either write-protected or I do not have the right permissions.

I dont understand how this could happen, if everything is fine when accessing the same drive and folders within Linux?

Any thoughts?

---

### Post by Nano Geek on 2007-12-04
When you mounted the drive, did you follow the instructions in the VirtualBox user manual?

---

### Post by markharding557 on 2007-12-04
check the permissions on your disk it may need changing

---

### Post by bitumen on 2007-12-05
i used samba to create windows shared folder and printer networking

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server")


Im running Ubuntu 7.10 64 bit and have just finished Vista business guest on virtual box 1.5.0_ose

---

