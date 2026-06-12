---
title: "Enable encryption on linksys WRT54G"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by zkaufman on 2007-09-24
I have a linksys wrt54g router. My ubuntu 7.10 desktop is WIRED to the router and is getting internet connection just fine. However, the router is broadcasting so all those nearby can get a wireless signal. How do I use my ubuntu system to set up encryption on the router so that not every passerby can connect to it? Nothing fancy please... just some basic, easy setup security will do fine for me. Thanks.

---

### Post by illumeo on 2007-09-24
Do you need the Wifi bit? or do you just want to turn if off?

---

### Post by be4truth on 2007-09-24
If you want to switch the wifi completely off there is a function inside the Linksys as far as I remember.
No broadcasting at all. If you don't use it is healthier.
Login to the linksys typing ```
192.168.1.1
``` in your browser.
user is "admin", passwd is either none or "admin".
But if you want to use it you need to define a key. Come back for that.

---

### Post by zkaufman on 2007-09-24
I dont want to swith it off... i just want to set it up with a password,.

---

### Post by crossedout on 2007-09-24
Open up your router settings using the method explained by be4truth.

Within the router menu is an option to set the password.  The password will lock the router but you should setup a key as well, also located in the router menu.  If your router was bought new, it should have a manual that explains what those terms are and why they are important.

-Xout

---

### Post by be4truth on 2007-09-24
login your router
go to WIRELESS/WIRELESS SECURITY
Choose WEP
Write any passphrase. This is your password (human readable). Then press GENERATE.

T\In the first field you see your encryption key. Note it down and copy it somewhere on your desktop (kwrite)

This is the number you have to enter everywhere as the key.
You need an SSID too. This is a word which your router sends out (or not) to identify your network.

---

### Post by Austin_KW on 2007-09-24
Choose WPA not WEP, WEP is useless.

---

