---
title: "IR Remote and Battery Life on 5,1 Macbook"
date: 2013-08-01
forum: Apple Hardware Users
---

### Post by Jeff_Spitzer on 2013-08-01
Hello I am brand new to Linux and Ubuntu 13.04 is the first version I've ever used.  So far almost everything is going great and I love it.  There are two things I am having minor issues with, my battery life and getting my IR remote to work.  I can't seem to find drivers for the remote, so if anyone can help me find them that would be greaaat.  Also my battery life is absolute crap.  The battery jumps from 100% to 90% in less than a minute with nothing in between.  Are there any extra drivers I should get or any tweaks I can do?

---

### Post by r3dbeard on 2013-08-06
Going all the way back to version 10.04 Lucid Lynx, there have been reported differences in battery life when running Ubuntu on Macbook 5,1's (I have this model too and am running 13.04 as well and love it.) Take a look at the link below and consider making some of the adjustments, particularly under 'Fans' and 'EFI Mode'. Note that these changes *could* help with battery life; however, results will likely still not be the same as with OS X. Good luck and welcome to the community!

Note: the below link is for a previous version however the commands for laptop-mode-tools and macfanctld are still valid as far as I can tell in my own system.
[https://help.ubuntu.com/community/MacBook5-1/Natty](https://help.ubuntu.com/community/MacBook5-1/Natty)

---

### Post by Jeff_Spitzer on 2013-08-15
Hi thanks for the response!  I went to install laptop-mode-tools and lost power during the install.  I have finally returned things to normal, but I am definitely not bothering with that again.  Thanks for the response though.

---

### Post by gregory-gutierez on 2013-08-20
Hi guys,

I run Ubuntu 13.04 on a Macbook 5,3, do you have troubles with your touchpad too? On my system, it's too sensitive when I'm typing stuff the cursor jumps few lines each time I touch it with my thumbs accidentally. When I try to use syndaemon to tweak it, it just stops working. It's really annoying as use a lot my keyboard for my job, typind long reports with LibreOffice... 

Another trouble is with the ACPI management. I must add the parameter maxcpus=1 to the GRUB config file in order to have ACPI managment (hence, battery management). 

By the way, you can enhance the battery life by installing the TLP utility, check this link: [http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter](http://askubuntu.com/questions/285434/is-there-a-power-saving-application-similar-to-jupiter)

Regards,

Greg

---

