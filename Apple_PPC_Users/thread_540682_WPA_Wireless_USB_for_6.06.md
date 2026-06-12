---
title: "WPA Wireless USB for 6.06?"
date: 2007-09-01
forum: Apple PPC Users
---

### Post by ivan09193 on 2007-09-01
I have a 12" Apple iBook G3 700 Mhz that I recently installed Dapper Drake on.  Since my iBook does not support AirPort Extreme with its WPA encryption, I was wondering whether there are any 802.11g USB wireless cards on the market that support WPA encryption on Dapper Drake and where I can find instructions on how to install them.  Thank you for your time.

---

### Post by stmiller on 2007-09-02
Check out this post:

[http://ubuntuforums.org/showpost.php?p=3246288&postcount=10](http://ubuntuforums.org/showpost.php?p=3246288&postcount=10)

Anything that has an intel chipset is good under Linux. As well as prism and orinoco.

Good luck!

---

### Post by ivan09193 on 2007-09-02
Will those chipsets work under Dapper Drake or just Feisty?  I'm a bit scared to upgrade.

---

### Post by stmiller on 2007-09-02
Most of the newer Linux drivers for 802.11g hardware and WPA stuff requires a newer kernel than what Edgy or Dapper provides (2.6.17 ?). You can always compile your own kernel from kernel.org, though I understand some people would rather not go there.

---

### Post by APU on 2007-09-02
> **ivan09193 said:**
> I have a 12" Apple iBook G3 700 Mhz that I recently installed Dapper Drake on.  Since my iBook does not support AirPort Extreme with its WPA encryption.

If your iBook has an internal Airport Card (not the Extreme, the old 802.11b one) it does also support WPA - you dont need Airport Extreme for that. If you have no WLAN integrated in your iBook than you should go the USB route since you can only get used Airport cards from ebay and they are VERY expensive!

good luck
APU

---

### Post by jboeke on 2007-11-17
> **APU said:**
> If your iBook has an internal Airport Card (not the Extreme, the old 802.11b one) it does also support WPA...

Are there good instructions for doing this somewhere?  I've been able to see my network OK, but can't get WPA working.  

Thanks!

JB

---

