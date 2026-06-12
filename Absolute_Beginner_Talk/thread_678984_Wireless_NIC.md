---
title: "Wireless NIC"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2008-01-26
I have a BroadCom wireless NIC in my machine. It is a dual boot machine. O/S's are XP and Ubuntu 7.10. The wireless nic works in XP not in Gutsy. It appears that the driver for the nic is not loaded in Gutsy. My question is: how do I load the driver in Gutsy? How can I tell if the driver is loaded? I have run wifi-radar with no joy. I can see the hardware when I do a "lspci". As I mentioned, I don't think I have a driver loaded. Can someone give me a little direction? The nic is a wmp300n with an external antenna. Thanks in advance.

---

### Post by CCNA_student on 2008-01-26
Go to System>Administration>Restricted Drivers Manager. I believe that is where you are supposed to look for the driver at. You can connect using your wired Ethernet port, correct?
You will have to download this restricted driver.

---

### Post by nkingcade on 2008-01-26
The driver is present. It is BCM43XG. However, when I do a lshw -C network, the information for the hardware shows a "*-network UNCLAIMED. Let me add this information which I suspect has some bearing on this little adventure. I am running x64 Gutsy. I have a dual processor asus board. Is there a driver for this architecture??

---

### Post by CCNA_student on 2008-01-27
I would ask for help in the 64-bit area of the forum but I am guessing that the 64-bit driver does not exist. My suggestion would be to either use the x86 version of Ubuntu or buy a wireless NIC from Intel.

---

