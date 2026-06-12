---
title: "How do I install my MIFI"
date: 2011-09-01
forum: Any Other OS
---

### Post by AWCJR on 2011-09-01
Can someone Please tell me how to get the drivers and firmware in for my MIFI.I am running a dual boot system Vista home premium/mint 11.04,both are 64 bit.Since I have 3 computers on this net running windows I don't want to change any formats in my MIFI.I woud like to not have to move from one system to another to use the internet. Is their a way to make it work in Mint with out doing this.Also need help in installing it in Mint.

---

### Post by Redmage913 on 2011-09-01
Are you using it in Wifi or USB mode? in Wifi mode there shouldn't be a problem connecting - it should work like any other wireless connection. As far as USB mode goes, I'm not sure if your MiFi device has any drivers in Linux. Please try it in WiFi mode, and let us know if you can connect.

---

### Post by AWCJR on 2011-09-01
Thanks,I'll try this now and let you know whats up.I didn't say but this is on my lap top all 3 of the others are desk tops.

---

### Post by Redmage913 on 2011-09-01
In this case, I don't really think it matters. Ubuntu's driver base is generally the same across the board, part of their attempt to let it "Just Work".

---

### Post by Perfect Storm on 2011-09-01
Moved to Other OS/Distro Talk.

---

### Post by haqking on 2011-09-01
are you referring to MIFI asin the box you which gives off WIFI ?

There should be no specific drivers or software for it, it should just be seen as a wireless connection or at least it is here in the UK with 3 MIFI

---

### Post by AWCJR on 2011-09-01
yes it is just a small box, now mint won't show my wireless card,how do I get it to show up and turn it on.

---

### Post by haqking on 2011-09-01
> **AWCJR said:**
> yes it is just a small box, now mint won't show my wireless card,how do I get it to show up and turn it on.

Your OS wireless issues should not be anything to do with MIFI.

Does your OS wifi usually work ? or you mean since trying to use the MIFI.

is it PCI, PCMCIA, USB ?

have you just added it ?

more information.

shos us output of 

lspci

or

lsusb

depending on what adapter you have

---

### Post by AWCJR on 2011-09-01
Not a new install,has been on windows for over a year,it is a stand alone device no cables to computer,also mint will not detect my wireless card that's in the system,it's a Dell 1737 Studio dual core with wireless card and Bluetooth,mint won't detect either one.
What do I need to do so it will detect them?

---

### Post by haqking on 2011-09-01
> **AWCJR said:**
> Not a new install,has been on windows for over a year,it is a stand alone device no cables to computer,also mint will not detect my wireless card that's in the system,it's a Dell 1737 Studio dual core with wireless card and Bluetooth,mint won't detect either one.
What do I need to do so it will detect them?


mmm well i have seen a few threads about mint get referred to the mint forums lately, have you tried there ?

The thread is misleading as it says installing MIFI which is not the issue.

I am aware there is no cables as i stated it is a standalone box which gives WIFI.

So back to what i already said we need more information to help.

Having windows on it is irrelevant, i mean a fresh install of linux which it seems it is.

So can you do as i said above so we can see if the adapater is listed

lspci

---

### Post by AWCJR on 2011-09-03
Thanks for the help I have figured it out and now up and running or is that up and stumbling,anyway it works for now.Again thanks.

---

