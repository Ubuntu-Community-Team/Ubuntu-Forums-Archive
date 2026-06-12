---
title: "Email and Browser connection"
date: 2008-01-04
forum: Beginner Team
---

### Post by nemonic on 2008-01-04
OK, so I have successfully installed Ubuntu 7.10 and have 3.3 Gb for data. I still have Windows on the major partition, as at present my interest in Ubuntu and Linux is mainly curiosity and brain stimulation.

But I have met a snag. I cannot setup Evolution email, and myFirefox browser will not open URLs.
On Windows I use Thunderbird and Firefox, so Evolution's setup window is a bit stranger for me, but I have filled in the forms to the best of my ability and experience. I have also talked to  my ISP for my Broadband connection. They do not support Linux but could not understand why my Broadband connection was not operating my Firefox. After all, the password and username are already set in the Siemens Speedstream Broadband modem.
What to do? Help will be greatly appreciated.

nemonic

---

### Post by icheyne on 2008-01-04
Are you connected via your USB port? If so, change to the ethernet port.

After googling, I found out that the problem might be with DHCP, the way your compuer gets an automatic dynamic IP address. Try a static IP.

"Go to System -> Admin -> Network. Click on the wired connection and change the properties from DHCP to Static IP. 
Your IP address should be 10.1.1.2 
Your subnet mask should be 255.255.255.0
Your gateway address should be 10.1.1.1"

---

### Post by jaz.spb on 2008-01-05
why only ethernet? Some USB ADSL modems such as Arris CM450BB works in ubuntu. May be dhcp will help you?

---

### Post by nemonic on 2008-01-05
REPLY Thanks for your comments, but before I do the DHCP to Static IP, will this affect only Ubuntu or my Windows XP also, which is operating OK on email and browser.


> **icheyne said:**
> Are you connected via your USB port? If so, change to the ethernet port.

After googling, I found out that the problem might be with DHCP, the way your compuer gets an automatic dynamic IP address. Try a static IP.

"Go to System -> Admin -> Network. Click on the wired connection and change the properties from DHCP to Static IP. 
Your IP address should be 10.1.1.2 
Your subnet mask should be 255.255.255.0
Your gateway address should be 10.1.1.1"

---

### Post by nemonic on 2008-01-05
REPLY: Thanks for your reply.
But as email and browser work fine on USB I wiill stay with it in the meantime. Anyway I seem to recall when I first went Broadband that after no luck with Ethernet, it was assumed my Network card was not working.
I will try your Admin, etc suggestion.

nemonic

> **icheyne said:**
> Are you connected via your USB port? If so, change to the ethernet port.

After googling, I found out that the problem might be with DHCP, the way your compuer gets an automatic dynamic IP address. Try a static IP.

"Go to System -> Admin -> Network. Click on the wired connection and change the properties from DHCP to Static IP. 
Your IP address should be 10.1.1.2 
Your subnet mask should be 255.255.255.0
Your gateway address should be 10.1.1.1"

---

