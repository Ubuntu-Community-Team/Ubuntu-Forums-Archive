---
title: "Firewire Card and External Raid Cage"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by starke1120 on 2006-08-27
I am a new user to Linux and Ubuntu.  So far I have Ubuntu desktop 64 bit 6.06 installed and loving it.  Im running a LAMP server and need to install a firewire card and external Hardware RAID enclosure SATA II and wondering which Firewire card to purchase along with the enclosure (not sure if it matters which enclosure, im sure if the card works it will work).  

Any help would be appreciated.  Im not very Linux Command line savvy so I was hoping if I get the right one Ubuntu will reconize it and Ill be able to get the raid up and going with few to no problems.

Thanks!

Dave

---

### Post by b_martinez on 2006-08-27
I tried to google linux hardware compapability to get you some sites that might help. Found nothing very useful, but if you can find a Firewire card, look on the box to see if it is Unix compatable. If so, it may work for you. 

 There is the ieee1394 (ohci) driver avaolable for the kernel, and it was autoconfigured for my onboard firewire port, so it should be safe for an add-in card.

If the card works, the cage should/could be any that you have.
hth
Bill

---

