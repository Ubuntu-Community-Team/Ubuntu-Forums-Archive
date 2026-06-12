---
title: "Problem with PPC 9600"
date: 2005-06-14
forum: Apple PPC Users
---

### Post by Franzmueller on 2005-06-14
Hello.

I've got an old Power MacIntosh 9600. I tried to install Ubuntu on it using BootX to boot the Install CD. I erased MacOS and after the first part of the installation I had to reboot. But this wasn't possible, I just got a grey screen with a cursor.

So I was sayed I had to reinstall MacOS to be able to try it again.

I can easily boot the MacOS install CD but when I try to launch the installer it says that I can't install on the CD and I have to chose an other disc. 

Apparently it doesn't find the hard disk     :? 
Is this because Ubuntu is on it ?

Could anybody help me ?

Franz.

---

### Post by imaputz on 2005-06-15
yeah, MacOS won't recongize the partition scheming. Use the Drive Setup util on your Mac CD and reinitailize the drive. Setup one partition for your MacOS side, and leave one empty for Ubuntu. You may have to reboot. You should be able to reinstall MacOS from there.

The Ubuntu setup will deal with the empty partition and proper recommendations on partitioning to for that one (filesystem and swap).

---

