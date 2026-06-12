---
title: "Wireless card not detected!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-12
Hey I've got a Intel Next-Gen Wireless-N card, ; Intel(R) Wireless WiFi Link 4965AGN, DHCP enabled and everytime i boot into ubuntu the card isn`t found.  What steps must i take in order to get the card recognized and be able to connect to a wireless connection.  I`m new to ubuntu and am still a little shaky with therminal commands and stuff so if u could provide as many steps as possible that would be great!  

Thanks, Alain

---

### Post by DonnieP on 2007-06-12
Take a look at this page.  It might help:

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty]("https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty")

---

### Post by stchman on 2007-06-12
> **S15_88 said:**
> Hey I've got a Intel Next-Gen Wireless-N card, ; Intel(R) Wireless WiFi Link 4965AGN, DHCP enabled and everytime i boot into ubuntu the card isn`t found.  What steps must i take in order to get the card recognized and be able to connect to a wireless connection.  I`m new to ubuntu and am still a little shaky with therminal commands and stuff so if u could provide as many steps as possible that would be great!  

Thanks, Alain

The 4965 card is not supported by Ubuntu at the moment.  You can use ndiswrapper to enable it.  You can get a 3945 and swap it out.  The 3945 is fully supported by Ubuntu.

---

