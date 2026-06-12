---
title: "I think my NIC is not recognised..."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Vistavenger on 2006-08-08
Installed Ubuntu on an older PIII computer. Seems like it did not recognise the NIC. Maybe it is too old? When I go to Device Manager I do not see the NIC there. ShouldnI just try to install a newer NIC?
Thanks! :D

---

### Post by bensexson on 2006-08-08
post the output from dmesg | grep eth

---

### Post by Fondor1 on 2006-08-08
If you have another NIC card laying around, just throw it in and see if Ubuntu will recognize it.  If not, you're where you are now, if yes, then you have a working NIC.

---

### Post by Vistavenger on 2006-08-09
OK, I can buy a 3com 3C905CX-TXM - PCI 10/100Mbit. But before I buy it I would like to know if there's an Ubuntu driver? So I checked out 3com.com and I noticed there seem to be drivers for Linux (Red Hat, SuSe, etc.) but I don't see Ubuntu in the list ([http://support.3com.com/infodeli/tools/nic/linuxdownload.htm](http://support.3com.com/infodeli/tools/nic/linuxdownload.htm)) so it it safe to buy it? Is it normal when it says a Linux driver it should work on all distro's?

---

### Post by Vistavenger on 2006-08-16
Well, my problem is solved: my NIC was just too old so I just bought a new Longshine NIC which uses the Realtek chipset (so I was told). Everything works fine now and there is now 1 extra Ubuntu user on the planet: moi. :-)

---

