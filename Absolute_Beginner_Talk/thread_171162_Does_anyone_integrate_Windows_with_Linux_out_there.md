---
title: "Does anyone integrate Windows with Linux out there?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by tstrowd on 2006-05-06
Has anyone ever heard of this? In Win XP ,click on Network Neighborhood,Click on Ubuntu client it says Path not found..you might not have permissions..etc
Then Ping hostname of Ubunto client..replies ok
Go back into Network Neighborhood click on client ..i can now get into and see directories
What is going on with this?

---

### Post by manicka on 2006-05-06
[QUOTE=tstrowd] ..i can now get into and see directories
What is going on with this?[/QUOTE]

One of the many joys of Windows.

---

### Post by professor_chaos on 2006-05-06
I never tried this. It this because of the linux filesystem not readable by XP???

---

### Post by tstrowd on 2006-05-06
[QUOTE=professor_chaos]I never tried this. It this because of the linux filesystem not readable by XP???[/QUOTE
I usually can see all directories and files on the Ubuntu machine from a winxp and win2000 computer.. it almost seems like the NIC has to waken for the Ubuntu machine to respond????

---

### Post by tstrowd on 2006-05-06
DUHH!! It was because of a mistake i made earlier. 

I enabled DHCP on the Ubuntu client and rebooted the machine. When it came back up Win2k server assigned it 192.168.0.16
I have an TCP/IP enabled industrial computer on the same subnet that is static assigned the same IP. 
So that is what happens when you have a IP address conflict.

---

