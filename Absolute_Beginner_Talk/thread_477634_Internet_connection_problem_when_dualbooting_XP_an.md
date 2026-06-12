---
title: "Internet connection problem when dualbooting XP and Feisty"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dello on 2007-06-18
I've been an Ubuntu user for 2 months and I have ONE physical hard drive and partition my hard drive manually without any problems at all. I have a wired Realtek NIC. Can someone please explain why the following is a fact on my computer:

1. When I install Windows XP on an NTFS partition and Feisty on an ext3 partition (dualboot with GRUB), I only have Internet connection in XP, NOT in Feisty. No matter what I do. It must have something to do with the partitioning structure/file systems for some odd reason!?

2. When I install ONLY Ubuntu on the entire hard drive (with several different partitions or just one partition, I've tried several different structures) my Internet connection works flawlessly and Internet runs even faster in Feisty than it does when only XP is installed. Strange!!!??? Help, I tear my hair! Thanks and have a great day.

---

### Post by oilchangeguy on 2007-06-18
possibly a different ip address for each os. in that case you'll need to restart your modem each time you switch os's.

---

### Post by dannyboy79 on 2007-06-18
certain NIC cards have a problem with shutting down properly when you dual boot them, to test if this is the cause with yours, do the dual boot again, then when you shutdown from winxp and the computer is totally off, unplug it from the power source completely, wait 5 mins, then plug in power and try to boot to feisty, if your internet works, than the reason is because your NIC isn't shutting down in between winxp and feisty so then feisty thinks it's still being used by another source so it doesn't use it. (obviously this is a very dumbed down explaination and I am not even sure why this happens) otherwise, you could try to troubleshoot it a little. 

what do these return when entereed from command line

sudo ifconfig -a

cat /etc/network/interfaces

cat /etc/resolve.conf

cat /etc/dhcp3/dhclient.conf

lspci -v


Do you own a router? Are you using dhcp or static?

---

### Post by dello on 2007-06-18
This sounds very likely, I'll test it right away. No, I don't have a router. I just plug my LAN cable into the socket in the wall (LAN Internet) and it's DHCP. Thanks! :p

---

### Post by Nessa on 2007-06-18
Release/renew of the ip addresses worked for me. I was told that this is normal when you reboot and use a different OS. Is that right?

---

### Post by dello on 2007-06-18
I waited for 20 minutes and it did NOT work. I was sure it was going to work. My ISP says it's 20 minutes before releasing the old IP. Well, I'll go to work now and if my ISP hasn't released the old IP until I get back (9 hours), I'll give up. Thanks anyway! ;)

---

### Post by dannyboy79 on 2007-06-18
what and you're not going to try to unplug your machine? that will renew your ip for sure!!! there's most likely a way to release your ip before you shut down windows also, under network connections I believe. Plus, it's not only to do with the IP, I have read that windows leaves the NIC card in a certain state unless you unplug power from it.

---

### Post by logos34 on 2007-06-18
dello,

dannyboy79 is right...why don't you try unplugging the computer power cord?  At least try it and rule it out...I tore my hair out for 3-4 days in Suse 10.1 trying to get a connection after switching from windows and finally just unplugged it and it worked! (happily no such issue issue in ubuntu).

---

### Post by dello on 2007-06-18
I'm from Sweden so my English isn't perfect but, of course, I powered off and unplugged everything completely and then waited for over 20 minutes without any results. I'm not stupid, just not pro with Linux yet. ;) Thanks for trying to help me though.

---

