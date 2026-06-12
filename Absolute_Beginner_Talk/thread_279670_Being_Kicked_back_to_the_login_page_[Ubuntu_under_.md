---
title: "Being Kicked back to the login page [Ubuntu under Vmware]"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ielliott on 2006-10-18
When i try logging in my Ubuntu will try and load Gnome and then kick back to the login page, i've tried this under everything failsafe gnome, failsafe terminal ect.

What would be a cause for this, something i would look into.

It doens't make sense to me. i know there was a power outage well i had Vmware open that may have caused the problem, but i have no idea on a solution

---

### Post by guilag on 2006-10-18
Did you see any error message poping-up ?
What is the version of ubuntu are you running ?

If you have the ubuntu_installation_cd iso files. You can change your configuration in the your vmx file to load the cd on start-up of the virtual machine. The live-cd will then start and you'll be back in gnome.

Next you will be able to mount your drive, then chroot on it to perform an upgrade via "sudo apt-get update", "sudo apt-get upgrade". This should install new packages with fix, security patch, etc if any of these are available.

Then, you exit chroot, unmount the drive, close the virtual-machine, back-up your vmx file to its original state and then see if it has correct the problem.

---

### Post by ielliott on 2006-10-18
No error messages, Dapper Drake so 6.06.

I do still have Ubuntu installation Cd isos.

I also can boot it under recovery mode also would that be a better way to try and fix it then running the Live CD?

---

### Post by tatimmer on 2006-10-18
The last time I had login problems and was kicked back, it was because the file permissions on my /home directory had changed.

see tomslogintips.

---

### Post by ielliott on 2006-10-18
> **tatimmer said:**
> The last time I had login problems and was kicked back, it was because the file permissions on my /home directory had changed.

see tomslogintips.

Where would that be? i did a search for tomslogintips and didn't find any threads.

---

### Post by ielliott on 2006-10-18
> **guilag said:**
> Did you see any error message poping-up ?
What is the version of ubuntu are you running ?

If you have the ubuntu_installation_cd iso files. You can change your configuration in the your vmx file to load the cd on start-up of the virtual machine. The live-cd will then start and you'll be back in gnome.

Next you will be able to mount your drive, then chroot on it to perform an upgrade via "sudo apt-get update", "sudo apt-get upgrade". This should install new packages with fix, security patch, etc if any of these are available.

Then, you exit chroot, unmount the drive, close the virtual-machine, back-up your vmx file to its original state and then see if it has correct the problem.


I don't entirly understand what you mean with Chrooting or how to do it so can you point me to some sort of information. :)

---

### Post by ielliott on 2006-10-18
> **tatimmer said:**
> The last time I had login problems and was kicked back, it was because the file permissions on my /home directory had changed.

see tomslogintips.

Used your tomslogintips and no results, the permissions are already set correctly.

---

