---
title: "Apple USB Modem"
date: 2007-04-18
forum: Apple Intel Users
---

### Post by edivad on 2007-04-18
Hello everybody.

I'm about to buy a macbook (13''). But before doing it, I'm seeing for
hardware compatibility. The only one left, and it's a must for me, is
the Apple USB Modem. This because I'm not reached by a xDSL network.

Does someone succeed in installing the modem with ubuntu? If yes, how?
If not, what were the problems? If never tried, please also report :)

Thanks a lot
Davide

---

### Post by cyberdork33 on 2007-04-18
You can run the Live CD and see if it recognizes the modem before installing.

---

### Post by davidzizza on 2007-04-18
Well I installed a Ubuntu VM using Parallels Desktop and the Live CD 6.10. It seems to recognize my printer, wireless card and Apple USB Modem. I don't use the modem much except for caller ID on the OS X portion, but it is in the Network control panel.

---

### Post by edivad on 2007-04-19
> **cyberdork33 said:**
> You can run the Live CD and see if it recognizes the modem before installing.

Yes but actually I still don't have nor the macbook nor the modem. I'm looking for compatibility before shop it :)

---

### Post by cyberdork33 on 2007-04-19
> **edivad said:**
> Yes but actually I still don't have nor the macbook nor the modem. I'm looking for compatibility before shop it :)

Ah well, in that case, the post above ought to be good news!

---

### Post by H264 on 2007-04-19
You could take the live CD to an Apple store and ask them to plug in the modem, I would bet they would let you try it out.

---

### Post by streeturchin on 2007-07-17
I'm using a first gen mac book pro with parallels 3.0 and Ubuntu 6.10. It works fine using the "shared networking"  option in parallels. Installed like a champ. No problems other than me being a Linux noob and forgetting everything is case sensitive.

---

### Post by cyberdork33 on 2007-07-17
> **streeturchin said:**
> I'm using a first gen mac book pro with parallels 3.0 and Ubuntu 6.10. It works fine using the "shared networking"  option in parallels. Installed like a champ. No problems other than me being a Linux noob and forgetting everything is case sensitive.

Your VM is not using the USB modem, it is using a virtual network card.

---

### Post by thully on 2007-07-18
Working in Parallels != working in a native Ubuntu boot.
When you are using Parallels, OS X's drivers are used, and Ubuntu uses those through the virtual machine.  When you are running natively, native Linux drivers are used for everything - and that's where you get into driver issues.

In this case, I'm almost certain that Apple's USB Modem will NOT work in a native Ubuntu boot - as it uses special drivers (i.e. it is a software modem, like a "Winmodem" except it supports Mac OS as well).  You can buy a USB hardware modem (look for one know to work with Linux), and it should work fine.  

However, if you are using Parallels to run Ubuntu, you will be all set - Parallels simulates an Ethernet adapter which uses your default Internet connection (in this case, your modem) as its default gateway.

**Note that if you haven't bought Parallels yet, I'd recommend VMware Fusion over it for the purpose of running Ubuntu.  It works better, and has more features when using Linux (i.e. you can share Mac files with Linux).  It is still in beta (actually Release Candidate now), but you can download that for free and preorder the final release for $40 if you like it.

---

### Post by cyberdork33 on 2007-07-18
> **thully said:**
> Working in Parallels != working in a native Ubuntu boot.

We really should get a FAQ sticky together or something to address these issues.

---

