---
title: "Help with Firewall and Anti-Virus"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-07-30
I know that there aren't many viruses and things for linux, but I'm alittle paranoid when it comes to network security (I have my Desktop and Laptop on the same network) I hope to have more computers than that up and running on my network here in the near future. However, I did have a couple of questions I wanted to ask:


1. Where can I find a good easy to use firewall?
2. Where can I find a good easy to use Anti-Virus program?
3. How do I go about setting up and configuring these programs for optimum performance on my Xubuntu 7.04 (Feisty Fawn) system?
4. Is there anything I should be aware of and look for when choosing said programs?
5. I would also like to know if there are some good simple to use network auditing tools and anti-spyware applications out there?


Can someone help me?

---

### Post by shearn89 on 2007-07-30
I know how it feels - it is a little unnerving when moving to linux, what with the distinct lack of AV/ASpyware type stuff, but you really don't need it - i think the main reason is that because you're always running as a user and not and admin, you can't write to the system files without putting in a password, and also there's no registry (not sure how that changes things, but i know it makes it less prone to viruses...). I'm not sure about the network auditing though...

---

### Post by misfitpierce on 2007-07-30
AV is not needed and as said can be weird at first breakin windows habits maybe of looking for those to stay secure. However a firewall is always a good idea regardless of OS choice. Altho if you have a router with a firewall on it you do not really need a firewall program especially on linux. But if you want to be sure or lack firewall on router firestarter is a great firewall and easy to setup.

---

### Post by silent1643 on 2007-07-30
if you must:
firewall - firestarter
anti virus - avast, or clamav

related [artle]("http://smallbusiness.yahoo.com/ecommerce/")

---

### Post by palintheus on 2007-07-30
Firestarter is a frontend config utility for iptables, which is the firewall that is built into linux.

ClamAV is a anti-virus, but I don't think you need one unless it is running as a file/mail server for a windows machine.

---

### Post by Acglaphotis on 2007-07-30
1: Firewall is built into the kernel. if you want a GUI for it try downloading firestarter (its in the repos)
2:You dont need one. What you have heard about not many viruses existing for linux is because the ones that exist are proof-of-concept.
3:N/A
4:There isnt any kind of spyware. But you may wanna install adblock and noscript in Firefo.

---

### Post by dpar on 2007-07-30
Good read!

[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)

---

### Post by Sbarton on 2007-07-30
1. Firestarter is available In Xubuntu/Ubuntu
2. CalmAV and it's frontend,ClamTK and avscan is also available.
3. Read a little of the documentation.
Regards

---

### Post by diatribe on 2007-07-30
I never understood even the paranoia arguement for viruses on linux; you are wasting system resources running something that 98% of the time is completely unnecessary, but hey whatever gets you off.

---

### Post by palintheus on 2007-07-30
> **diatribe said:**
> I never understood even the paranoia arguement for viruses on linux; you are wasting system resources running something that 98% of the time is completely unnecessary, but hey whatever gets you off.

If he's not running Ubuntu exclusively on his network, and is running it as a server to the rest of the computers, it could infect a win machine, if he has one, other than that, I agree with you.

---

