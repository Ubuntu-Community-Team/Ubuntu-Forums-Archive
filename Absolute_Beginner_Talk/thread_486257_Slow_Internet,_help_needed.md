---
title: "Slow Internet, help needed"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-06-27
Until about a week ago, my Internet Connection was working fine, However, one time last week my internet complelety went of, when it finally came back on, my interent had slowed down to a crawl. I am using Ubuntu 6.06 (still :P) and connect to the internet via a netgear router that is connected through my computer through the NIC card. I use AOL (ha ha, parents pay, Good enough reason to use it for me :P) Anyone suggest anything I can try, I have tried the usual lol, deleting temp files, cookies, scans etc. Thanks in advance
Dan

---

### Post by FleetAdmiral74 on 2007-06-27
Do a quick search for a guide on disabling IPv6, might do the trick.

---

### Post by AriciU on 2007-06-27
sudo gedit /etc/modprobe.d/aliases

Replace "alias net-pf-10 ipv6" to "alias net-pf-10 off".

Save changes, reboot and type "sudo lsmod | grep ipv6" in the console and report back what is says.

---

