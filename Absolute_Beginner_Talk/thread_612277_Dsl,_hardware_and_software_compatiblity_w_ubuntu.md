---
title: "Dsl, hardware and software compatiblity w/ ubuntu"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by peterjohn on 2007-11-13
Hi,  I have SBC DSl, I have the external modem that hooks up to the computer, and I have the SBC connection manager program, i'm wondering how will connecting to the internet work on ubuntu if the SBC connection manager cannot be on ubuntu.  It's probably something really obvious but I just don't get how it'll work.

Thanks,

-peter

---

### Post by Bachstelze on 2007-11-13
Is your modem connected to your computer with an Ethernet or USB cable ?

---

### Post by peterjohn on 2007-11-13
with Ethernet

---

### Post by Bachstelze on 2007-11-13
Then I guess you should be fine. Just to be sure, test it with the Live CD before you install.

---

### Post by peterjohn on 2007-11-13
what im asking is how would I start//stop the connection because I do it with the sbc connection manager I don't really know how other wise.

---

### Post by mysticrider92 on 2007-11-13
Most of the programs that come with ISP's are just to make setting it up easier. Once your modem is set up for the first time, any needed settings can be copied from Windows (IP, DNS, gateway, etc..).

If you are not using a router, you might need to use network-manager to set a PPPOE (I think that is right) connection with your username and password from the ISP.

[edit] Oh, you can disable it with the network-manager icon in your system panel. Just right click and the option should be listed.

---

### Post by p_quarles on 2007-11-13
> **peterjohn said:**
> what im asking is how would I start//stop the connection because I do it with the sbc connection manager I don't really know how other wise.
I just leave the connection on all the time, myself, but there are various ways of disabling it in Ubuntu. You can right-click on the network icon and select "disable connection" (something like that), or use the command line:
```
sudo ifup eth0
``` 
will enable the connection, and 
```
sudo ifdown eth0
```
will turn it off.

---

