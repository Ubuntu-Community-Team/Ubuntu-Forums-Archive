---
title: "loosing IP address"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
Everytime i boot my ubuntu machine the ip address is gone . How do i make sure that i have a IP address associated with my ethernet .

I presume there must be a text file that i have to edit or a command that sets the Ip address.

Thanks in advance

---

### Post by Iarwain ben-adar on 2006-12-15
Hiya,
how do you mean?

Have you tried ```
sudo dhclient
``` ?


Iarwain

---

### Post by zugvogel on 2006-12-15
You shouldn't need to edit a text-file by hand.

Try, under "network settings", make sure the IP is set through "properties" of the "ethernet connection". Make sure you press OK for the "interface properties" box, and then you could even save the settings as a "location" in the "network settings" window. Then, above all, make sure you press OK when closing that window.

Does this work?

---

