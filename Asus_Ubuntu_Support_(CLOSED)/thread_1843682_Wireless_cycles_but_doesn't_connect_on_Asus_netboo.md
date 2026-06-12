---
title: "Wireless cycles but doesn't connect on Asus netbook"
date: 2011-09-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by badner on 2011-09-13
My internet on my Asus netbook running Ubuntu 11.04 seems buggy.  I can see all networks but sometimes it just cycles through the connections, asks me to put the pass in but never actually connects.  I don't know if there is a way to reset my wireless card or not.  All other machines in the house (1 mac, one laptop running Windows 7) are able to connect.  Some days the Asus/ubuntu connects, some days it doesn't.  Very confused...

---

### Post by JD8182 on 2011-09-13
Not sure any of the issues at the link I provide will be of any help, however it seems that Wireless adapters in the Asus Model netbooks are buggy, I will continue to see if I can find another solution...[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) ..





> **badner said:**
> My internet on my Asus netbook running Ubuntu 11.04 seems buggy.  I can see all networks but sometimes it just cycles through the connections, asks me to put the pass in but never actually connects.  I don't know if there is a way to reset my wireless card or not.  All other machines in the house (1 mac, one laptop running Windows 7) are able to connect.  Some days the Asus/ubuntu connects, some days it doesn't.  Very confused...

---

### Post by JD8182 on 2011-09-13
I would also suggest that you open the restricted drives in the Synaptic Package Manager and look in there.

Open a terminal and use the code: > lspci, that should tell you what your adapter is.

Start Synaptic and go to Settings-->Repositories-->Ubuntu and enable the "Proprietary Drivers for Devices (Restricted)" item, then search for your adapter... 






> **badner said:**
> My internet on my Asus netbook running Ubuntu 11.04 seems buggy.  I can see all networks but sometimes it just cycles through the connections, asks me to put the pass in but never actually connects.  I don't know if there is a way to reset my wireless card or not.  All other machines in the house (1 mac, one laptop running Windows 7) are able to connect.  Some days the Asus/ubuntu connects, some days it doesn't.  Very confused...

---

### Post by Pariah819 on 2011-09-13
I am running on an ASUS netbook right now and I have to use the restricted drivers for it to work. They should be recognized as the "Broadcom STA wireless driver" (that is of course if you have the same card as I have).  I think my wireless controller is a Broadcom BCM4313.  If you need to install the restricted driver goto, "System->Administration->Additional Drivers"

---

### Post by Gajeel on 2011-09-15
hello,
i have exactly the same problem as you have badner and i have no idea of how to solve it as i am very new to linux: i installed it a few hours ago for the first time ever....
i barely know how to use the terminal and i desperately need assistance!
the proprietary drivers for devices is ON yet but it keeps on connecting and asking the network key again and again without ever being able to connect...
anybody that could help us?

---

### Post by fdrake on 2011-09-15
post the results for
```
lspci 
lshw -c Network
nm-tool
```

---

