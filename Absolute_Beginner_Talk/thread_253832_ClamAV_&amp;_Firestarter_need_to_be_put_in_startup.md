---
title: "ClamAV &amp; Firestarter need to be put in startup"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2006-09-08
I used Automatix to install ClamAV and Firestarter, do I need to put then in the startup programs session or do they start automatically? Second question, Firestarter asked a couple of questions when I started it the first time, nothing with ClamAV, do I need to do any setting up with these two programs that is not obvious?

---

### Post by baldy1324 on 2006-09-08
i dont know but i think you can copy the program binary in /usr/bin or /bin (the thing you type into the terminal), copy the script into the /etc/rc.d directory, not sure but thats what i think

---

### Post by orb9220 on 2006-09-09
Iptaples is the actual firewall that is automatically started already. Firestarter is just the gui frontend for iptables and only needs to be run when you want to make changes.

And why are you running antivi software it is not needed. Unless you are running a mail,file server setup.

It will just eat up more ram and resources and really not give you any  more protection.

---

### Post by BirdZerk on 2006-09-09
Actually, I wasn't running it for Linux self protection, as I was trying to protect the VMware win2k installation and the second XP computer in the house.  If running an anti-virus is not going to help in protecting these other windows installations I would like to know?


This does bring up a question how protected is a Vmware installation of windows, does the iptables firewall protect the windows install or do I have to install all the normal protection software in windows to protect it?

---

### Post by Anduu on 2006-09-09
To actually answer your questions...

ClamAV and Firestarter do their thing automatically.

I would guess the Linux firewall aka iptables would protect your vmware win2k install...you could test the theory by using firestarter to block http ports and see if vmware can access the net.

And good for you for using antivirus....Even though Linux is pretty much immune viruses can still be spread to  Windows pcs.

---

### Post by BirdZerk on 2006-09-09
Thanks for the help, everything seems to be working, but I do have another specific question.  Does ClamAV check the incoming and outgoing e-mails in Thunderbird for viruses?  I am so use to the graphics poping up on a windows system saying, I,m right here doing my job, that not having all that stuff makes me wonder if it is actually turned on and working.

---

