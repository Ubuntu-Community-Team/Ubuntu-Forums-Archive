---
title: "Wireless Help Needed"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by chopper81 on 2006-08-08
I am currently trying to set up a wireless network on my Dual Bootable laptop using Linux as the primary OS. The wireless network will work with the other OS but not with Linux. Any help would be great. If I could just get the wireless to work, I think I just might drop the other OS all together!!
Thank you,choper81

---

### Post by Fondor1 on 2006-08-08
Can you give us more details about your setup?  What sort of wireless card are you using?  Do you have encryption enabled on your router?

---

### Post by Epperly on 2006-08-08
hah yeah I gave up on Linux on my Laptop =\
oh also I have the BCM4306 also

---

### Post by chopper81 on 2006-08-08
The wireless card is a BCM4306 802.11b/g and I do not have the encryption going on the router at this time.
chopper81

---

### Post by davebgimp on 2006-08-08
Is your network using WPA encryption? If so, you need to make a few tweaks.

Maybe there's a better thread, but following this has me up in 5 minutes with my wpa wireless.

[http://ubuntuforums.org/showthread.php?t=179643](http://ubuntuforums.org/showthread.php?t=179643)

---

### Post by davebgimp on 2006-08-08
> **chopper81 said:**
> The wireless card is a BCM4306 802.11b/g and I do not have the encryption going on the router at this time.
chopper81

Check for your card's support status here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by chopper81 on 2006-08-08
I checked the list and did not see Broadcom listed there. Any other ideas please.
chopper81

---

### Post by bensexson on 2006-08-08
Look at these guides.  I am using ndiswrapper with my bcm4306 because the bcm43xx driver would only support 802.11b.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by davebgimp on 2006-08-08
> **chopper81 said:**
> I checked the list and did not see Broadcom listed there. Any other ideas please.
chopper81

Search your model on that page. I found several references to your model number.

---

### Post by chopper81 on 2006-08-08
To be honest with you I do not know what ndiswrapper is! Does the version of Linux matter for this. I noticed that the pages that I just went to were for Dapper 6.06 not Breezy Badger.
chopper81

---

### Post by davebgimp on 2006-08-08
> **chopper81 said:**
> To be honest with you I do not know what ndiswrapper is! Does the version of Linux matter for this. I noticed that the pages that I just went to were for Dapper 6.06 not Breezy Badger.
chopper81

Would you consider updating to Dapper?

---

### Post by chopper81 on 2006-08-08
thank you. Idid not scroll down through thw whole page.

---

### Post by chopper81 on 2006-08-08
I am using this laptop for school (Clemson Univ.) and they are using only one version. So, I really don't have the ption of changing that.
Chopper81

---

### Post by chopper81 on 2006-08-08
Would it be easier to get this working if I first had this hardlined to my network. Right now I have no internet acces on that Laptop at home when I do at school. I know that the stuff is there for the wireless to work at school, IT JUST DOES nOt WORK AT HOME!!
Chopper81

---

