---
title: "Wireless drivers included in intrepid ibex?"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by mxweas on 2008-11-03
I've been having trouble with my new macbook pro 5,1 and wireless. From what I hear intrepid ibex works with the standard macbooks wifi out of the box. Does anyone know if intrepid ibex has broadcom support built in now?

Thanks,
Max

---

### Post by MichaelSwengel on 2008-11-03
It does. Yes.

You can install the Broadcom driver as you would the nVidia drivers in previous versions - via the Hardware Drivers panel in System > Administration.

How are you liking the 5,1?

---

### Post by ronocdh on 2008-11-03
I haven't been keeping well abreast of changes to the Mac hardware line, but are you sure the MacBook Pros are using Broadcom chipsets now? I know in my MBP (already two years old), I have the Atheros chipset for wireless, so I have use MadWifi drivers. (ndiswrapper is also an option for those that want to go that route.)

Try an **lspci** to check what chipset you have. (Perhaps a **sudo update-pciids** will be necessary to get all the right information out of **lspci**.)

---

### Post by hanzomon4 on 2008-11-03
> **ronocdh said:**
> I haven't been keeping well abreast of changes to the Mac hardware line, but are you sure the MacBook Pros are using Broadcom chipsets now? I know in my MBP (already two years old), I have the Atheros chipset for wireless, so I have use MadWifi drivers. (ndiswrapper is also an option for those that want to go that route.)

Try an **lspci** to check what chipset you have. (Perhaps a **sudo update-pciids** will be necessary to get all the right information out of **lspci**.)

In 8.10 if you have the 802.11n atheros card the foss ath9k driver from Atheros works out of box.

---

### Post by cyberdork33 on 2008-11-03
> **michaelswengel said:**
> you can install the broadcom driver as you would the nvidia drivers in previous versions - via the hardware drivers panel in system > administration.
+1

---

### Post by mxweas on 2008-11-03
I cannot see anything in the Hardware Drivers menu... It says no proprietary drivers are in use... Is a broadcom driver option supposed to show when I put in the intrepid ibex disk?

Thanks,
Max

---

### Post by cyberdork33 on 2008-11-03
> **mxweas said:**
> I cannot see anything in the Hardware Drivers menu... It says no proprietary drivers are in use... Is a broadcom driver option supposed to show when I put in the intrepid ibex disk?
You shouldn't have to put the disc in even...

---

