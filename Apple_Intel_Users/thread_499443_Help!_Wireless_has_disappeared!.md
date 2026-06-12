---
title: "Help! Wireless has disappeared!"
date: 2007-07-12
forum: Apple Intel Users
---

### Post by Torajima on 2007-07-12
Wireless had disappeared from Network Manager. When I right-click on it, "Enable Wireless" isn't there anymore.

I don't know where to start troubleshooting this... please help!

---

### Post by cyberdork33 on 2007-07-12
how did you setup wireless previously? What card do you have? What type of Mac?

At the commandline:

lspci will show your hardware

ifconfig will show all your network interfaces.

---

### Post by Torajima on 2007-07-12
> **cyberdork33 said:**
> how did you setup wireless previously? What card do you have? What type of Mac?

At the commandline:

lspci will show your hardware

ifconfig will show all your network interfaces.

I didn't set it up. It worked out of the box (well, I did have to enter my WEP password in NetworkManager).

It is a Macbook. My Network controller is listed as Atheros Communications, Inc. Unknown device.

If I type "sudo iwconfig" it says "no wireless extensions". Is this normal!?

---

### Post by Torajima on 2007-07-13
Any ideas? My laptop is next to useless without wifi access...

---

### Post by cyberdork33 on 2007-07-13
check the restricted driver manager. it should have an entry for atheros

---

### Post by Torajima on 2007-07-13
I get an error message saying "Your hardware does not need any restricted drivers."

---

### Post by Wittiga on 2007-07-13
I have the same problem, with the only difference that wireless has never worked (macbook c2d and feisty kubuntu). Ive tried installing the madwifi drivers with no success yet. You could try with the guide on this forums.

---

