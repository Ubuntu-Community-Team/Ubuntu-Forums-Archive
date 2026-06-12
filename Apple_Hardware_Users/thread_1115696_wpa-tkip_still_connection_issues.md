---
title: "wpa-tkip still connection issues"
date: 2009-04-04
forum: Apple Hardware Users
---

### Post by mkgkg on 2009-04-04
Hi,
i have a macbook 3,1 with os-x ubuntu 8.10 and 9.04 . I need to connect to my university wifi net using a wpa-enterprise tkip ecnryption thought two certificates, with  extensions .cer and .p12 .
I tried to connect  with Network-manager but it doesnt support tkip encryption and so i tried using the eap with tls encryption but without success. So i installed wicd  but i had the same problem. 
finally i used a script in order to connect with wpa_supplicant but i was still not able to connect .
i tested  all these tentatives   under  8.10 and 9.04 ubuntu os.
i'm using the default Broadcom sta driver .
Before installing 8.10 i was able to connect to this net under ubuntu 7.10 with the network manager that was able to support tkip encryption and with other ndiswrapper driver (not broadcom).
the Passwd and the certificates i used for connect work  because are the same under os-x and connection works!
i think the problem is Broadcom driver and i searched in the forum a solution but i found nothing except a patch in this link [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) but i didnt try it. 
I posted my lspci and my wpa_supplicant.conf .
Thanks in advance.

---

### Post by mkgkg on 2009-04-04
i post the result of #iwlist eth1 scan
i would connect to the  hidden net ' '.
also i post the tentative of connection thought the script that turns on the eth1 interface, sets the right ESSID name and uses wpa_supplicant.conf linked before.

---

### Post by hajk on 2009-04-04
> **mkgkg said:**
> ...i think the problem is Broadcom driver and i searched in the forum a solution but i found nothing except a patch in this link [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) but i didnt try it.The patch is described at the Broadcom site as being applicable to enterprise security, so why haven't you tried it? Have a look at [http://forums.debian.net/viewtopic.php?t=35562](http://forums.debian.net/viewtopic.php?t=35562) for an example of enterprise security in wicd.

---

### Post by mkgkg on 2009-04-05
hi, thanks for the aswer.
i didn't try the patch because i don't know how use /install it! u're welcome if you know how use it!
i tried to use wicd other times but didn't work.

---

### Post by hajk on 2009-04-05
How to use the patch for the Broadcom driver is described in [http://forums.debian.net/viewtopic.php?t=30648](http://forums.debian.net/viewtopic.php?t=30648), and how to add a new enterprise security template for wicd is described in the reference I already gave you, [http://forums.debian.net/viewtopic.php?t=35562](http://forums.debian.net/viewtopic.php?t=35562). Note: I wrote those howtos myself, no sense in copying/repeating them here... besides, the big guy himself (M.S.) has repeatedly said that Ubuntu is Debian.;)

---

### Post by mkgkg on 2009-04-05
i looked into the debian tutorial... Should i have  to remove my Broadcom STA driver in order to apply the patch or i can maintain it and in this case to which folder i have to apply it? sorry but i m not so skilled with drivers.

---

### Post by mkgkg on 2009-04-05
i found this guide [http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+patch](http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+patch).
tomorrow i 'll reinstall the broadcom driver and i ll hope it works ! thanks!

---

### Post by hajk on 2009-04-05
Look, I feel a little hesitant to get you started on patching/compiling your own drivers... because that may be needed here. I say "may be", because that patch has been out for a few weeks now, and may find its way into the "wl" driver to be included in Jaunty (or may have done so already in Jaunty Beta). You should check for yourself in the Jaunty development forum and in Launchpad.

But, supposing that you need that patch and that it is not going to be included in Jaunty, then you would need to patch/compile the wl-driver yourself. And, yes, the Ubuntu-supplied wl-driver would have to be removed. What you should then do: download the archive with the source code of the driver from Broadcom, also download the patch, and then get a print of the README.txt file. The README.txt file has precise instructions as to how to untar the driver source to a temporary directory (or folder, as you call it), make this in your home directory. The Howto on the Broadcom driver that I referred you to should then be followed, including getting a proper compiling environment set up for your kernel with the "sudo m-a prepare" command (from the module-assistant package). The Howto mentions the 2.6.26-amd64 kernel, but you should substitute for your own kernel.

Good luck!

---

### Post by cyberdork33 on 2009-04-06
Just a suggestion... If using ndiswrapper worked for you, then why don't you just use that until Broadcom updates their driver?

---

