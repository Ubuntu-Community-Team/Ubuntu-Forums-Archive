---
title: "ubuntu installed on laptop boot problems"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by maestrodelux on 2008-03-09
after trying several different versions of linux - ubuntu 7.10 alternate amd64
finally worked.
but only after 3 power down and reboots
then i installed updates and restricted drivers-tried to reboot-then locked up.
had to power down -- after about 10 tries system will boot-up 
i am using the system now to send this message.
what can be the boot problem?

hp pavilion laptop-turion 64-nvidia graphics-2g of ram
i am using a spare hd sata 100g

---

### Post by 1010011010 on 2008-03-09
I had the same problem.  The best solution that I found was to install the regular cd (i.e. not alternate) and install using 'safe graphics mode.'  Then once it is installed, download [Envy]("http://www.albertomilone.com"), and run it for the nVidia drivers.  For the wireless card, use ndiswrapper or madwifi (madwifi if you plan on using kismet or anything like that).

---

