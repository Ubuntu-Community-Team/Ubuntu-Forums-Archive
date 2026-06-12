---
title: "Problems booting with rEFIt"
date: 2007-02-22
forum: Apple Intel Users
---

### Post by yg17 on 2007-02-22
I have a 24" C2D iMac. I installed Vista with BootCamp awhile ago, and wanted to install Ubuntu as well (6.10). I'm trying to install Ubuntu to a USB 2.0 drive. I first installed rEFIt, and it wroks great. I then booted off the live cd, and installed to the drive. That went fine too. 

It came time to install GRUB, and not knowing what I was really doing, I installed it to /dev/sdc which is the name of the USB drive. I then rebooted, and rEFIt recognized the new partition. But when I try to boot Linux, I get this error:

Starting legacy loader
Using load options USB
Error not found returned from legacy loader
Error not found from locate device path


What did I do wrong here? Thanks

---

### Post by cocoia on 2007-02-25
What worked for me when I was testing OSX86 and Leopard on an external USB was unblessing rEFIt on my OS X partition (so it's no longer booting) and using the bootcamp bootloader to select the USB icon. From there, it worked for me. If it doesn't, you can always boot up from startup disk (OS X) and rebless rEFIt to try something else. My 2 cents.

---

### Post by neutrino15 on 2007-02-26
Yeah,

I installed ubuntu on a 20gb partition of my external FW harddisk. It all went fine untill it tried to install GRUB. It failed with a "Fatal Error"...... Good news is that mac is still there, bad news is that nothing can see that 20GB except for the install cd. Refit can't even see it!

Whats going on?


Sombody needs to post a definitive guide on installing ubuntu as a 2nd OS on a mac.. rEFIt and Bootx..

---

### Post by Chrisj303 on 2007-03-11
You need to re-sync your MBR/GPT tables DURING installation of ubuntu, via refit : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Read steps 6 + 7, you can't really go wrong.

---

