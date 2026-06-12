---
title: "Partitioning problem"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-25
So I have an extra internal hard drive that I wanted to use w/ PartImage to make a backup of my system, but the the thing is when I try to format it to ext3, the thing mounts halfway through and then gives me an error saying its mounted and cannot complete the operation. What can I do?

---

### Post by overdrank on 2007-07-25
> **FleetAdmiral74 said:**
> So I have an extra internal hard drive that I wanted to use w/ PartImage to make a backup of my system, but the the thing is when I try to format it to ext3, the thing mounts halfway through and then gives me an error saying its mounted and cannot complete the operation. What can I do?

Hi are you running gparted from the live cd?

---

### Post by FleetAdmiral74 on 2007-07-25
Nope, but since I am not running Ubuntu from that HD I didn't think there would be a problem with it being mounted or anything. Am I in error?

---

### Post by sad_iq on 2007-07-25
If ti's in the desktop right click it and select umount...if it's not there look in /media !!!

---

### Post by overdrank on 2007-07-25
> **FleetAdmiral74 said:**
> Nope, but since I am not running Ubuntu from that HD I didn't think there would be a problem with it being mounted or anything. Am I in error?

No, I was just asking because I had that happen i ubuntu and had to use the live cd to stop if from mounting the drive. Just a suggestion.

---

### Post by e6626550w on 2007-07-25
> **FleetAdmiral74 said:**
> So I have an extra internal hard drive that I wanted to use w/ PartImage to make a backup of my system, but the the thing is when I try to format it to ext3, the thing mounts halfway through and then gives me an error saying its mounted and cannot complete the operation. What can I do?

Shot in the dark, but you might try a different version of Gparted.  ( I assume you're using it). All version aren't equal and the very new ones 'always' error out for me. Version 2.5 works on this computer,  both the live Gparted cd and the one included in the live cd for ubuntu 6.10. 

eileen...

---

