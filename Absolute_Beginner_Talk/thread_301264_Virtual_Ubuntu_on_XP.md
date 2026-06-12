---
title: "Virtual Ubuntu on XP?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-11-16
Hi

I have no idea whether VMWare or some other software can help me.

I have a Win XP machine at work and I'm unable to remove it (or I would in a flash). Can I use a cost-free virtualisation program to run Ubuntu? Is VMWare Server what I should be looking for?

Thanks
Seine

---

### Post by unbuntu kid on 2006-11-16
Can you partition the hdd?
If you can you should be fine!
If your machine @ work is on XP, I recommend talking to the IT guy to make sure other operating systems work on the network, or if it is considered vandlism to install another os.
Better safe than sued!

---

### Post by Seine on 2006-11-16
Thanks ubuntu_kid. Are you suggesting I could install on a separate partition and GRUB up my OS choice upon reboot? I could partition the HDD, but I don't think that would be considered a fair use of my admin rights for this box. 

I'm looking for a virtual solution to run an Ubuntu session from within my XP login. Then I wont have to make any changes to my system that fall outside of my 'charter' as an employee.

The network is host to other NT, Linux and Solaris servers. Consultants have plugged in their fancy Mac Books without any problems. I'm guessing its a hetero environment. (Not that there's anything wrong with that).

---

### Post by cwaldbieser on 2006-11-17
> **Seine said:**
> Thanks ubuntu_kid. Are you suggesting I could install on a separate partition and GRUB up my OS choice upon reboot? I could partition the HDD, but I don't think that would be considered a fair use of my admin rights for this box. 

I'm looking for a virtual solution to run an Ubuntu session from within my XP login. Then I wont have to make any changes to my system that fall outside of my 'charter' as an employee.

The network is host to other NT, Linux and Solaris servers. Consultants have plugged in their fancy Mac Books without any problems. I'm guessing its a hetero environment. (Not that there's anything wrong with that).

I have successfully installed kubuntu under Virtual PC.  I heard that VMWare is superior, but I have not actually tried it.

---

### Post by Seine on 2006-11-17
I installed the VMWare server and created a virtual Ubuntu installation. I couldn't boot it up though as it tried to connect to our CCM server (software updates) and complained of unknown client.

However, for others who might care, the process was easy... if just a little bit CPU and HDD hungry. (150 MB download, 100MB install and + VM space for each O/S you want).

---

