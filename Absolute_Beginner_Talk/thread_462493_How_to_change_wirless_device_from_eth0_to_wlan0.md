---
title: "How to change wirless device from eth0 to wlan0??"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-06-02
Hi.  I have wpc54gs wireless card with broadcom v3 card.  Installed driver using bcm43xx cutter approach and everything works great.  Using this method, the wireless card is assigned to eth0.  Is there anyway to change this from eth0 to wlan0?

Thanks.

---

### Post by Bachstelze on 2007-06-02
ifrename is what you're looking for.

---

### Post by kevdog on 2007-06-02
Sounds like the right tool, but were to I find it -- ifrename???

---

### Post by Mazen on 2007-06-02
May i ask why would you want to change it? because i was curious about it too...thanks

---

### Post by kevdog on 2007-06-02
Ok, I found out how to do it, thanks to the helpful (not too helpful) post above.

Here is what you do (assuming using sudo or admin mode to edit all files listed below);
1. Edit the /etc/iftab file
     Change the name of the interface to anything you want
     For example I changed eth0 to wlan0 to make it more appropriate to describe my connection
2. Edit /etc/network/interfaces file
     Change name of old interface to new interface
     For me, everywhere eth0 was listed, I changed it to wlan0
3.  Reboot

Done -- problem solved
Hope this helps someone!!

---

