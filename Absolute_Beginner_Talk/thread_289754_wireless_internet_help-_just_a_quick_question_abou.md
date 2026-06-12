---
title: "wireless internet help- just a quick question about that broadcom thing?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by darthseth on 2006-10-31
still using dapper drake 6.06
I used [this]("http://www.ubuntuforums.org/showthread.php?t=190967") guide to get Wi-fi working in Ubuntu 6.06 i386 once, and I didn't actually do anything, but learn to update the computer using synaptec, which was great because I learned.  
But then I decided I wanted xubuntu on my laptop, and also ubuntu 64 on my desktop, and it looks like I need to start entering in commands since synaptec didn't resolve the issues this time. But before I get started I wanted to know more about the removing and disabling of broadcom (refer to the link above).  Even though I usually prefer to use the wireless adapter in my desktop, but sometimes I want a hardline.  Also the same thing with my laptop running xubuntu, I want to be able to use my NIC still.  Will removing the broadcom destroy the NIC driver? 

What does the line do? (as it is in [This context]("http://www.ubuntuforums.org/showthread.php?t=190967"))

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper

Specifically will "disabling broadcom" disable regular ethernet? because I don't want to do that. 

Thanks again for all the help! 

-Seth-

---

