---
title: "Windows Explorer not responding"
date: 2011-08-09
forum: Any Other OS
---

### Post by JossyP on 2011-08-09
Hi

Can someone help me please?

I have a Lenovo Thinkpad X100e running Windows 7 Pro. Since a few weeks ago, everytime I click on anything in the system tray, a "Windows Explorer is not responding" window appears. Eventually the systemn will respond.

I tried a system restore to a point before the problem appeared and that appeared to resolve it, but now, about a week later, it has reappeared. I've disabled automatic Windows updates and not installed any since the system restore.

I tried a clean boot and seem to have isolated the problem to two Lenovo apps - AcPrfMgrSvc and AcSvc. Booting with either one enabled on its own, the problem seems to be fixed but a normal boot with both enabled brings it back again. I can't disable them permanently because then I can't use the radio connection.

Any thoughts please?  :(

---

### Post by haqking on 2011-08-09
> **JossyP said:**
> Hi

Can someone help me please?

I have a Lenovo Thinkpad X100e running Windows 7 Pro. Since a few weeks ago, everytime I click on anything in the system tray, a "Windows Explorer is not responding" window appears. Eventually the systemn will respond.

I tried a system restore to a point before the problem appeared and that appeared to resolve it, but now, about a week later, it has reappeared. I've disabled automatic Windows updates and not installed any since the system restore.

I tried a clean boot and seem to have isolated the problem to two Lenovo apps - AcPrfMgrSvc and AcSvc. Booting with either one enabled on its own, the problem seems to be fixed but a normal boot with both enabled brings it back again. I can't disable them permanently because then I can't use the radio connection.

Any thoughts please?  :(


Hi welcome to the forum.  This however is not a windows forum, or at least there is a other OS section available.

However you could run msconfig from the run command and remove the tick from these starting up or from services.

Then start the wireless zero configuration to enable you to manage your wireless with the built in app.

Hope this helps

---

### Post by 3rdalbum on 2011-08-09
Jossy, this forum is for help with Ubuntu, a Linux-based operating system. The best place to get help with Windows is a Windows-specific forum. Many (most?) Ubuntu users don't know enough about Windows to be of help to you.

A good starting place for you would be the Cnet forum: [http://forums.cnet.com](http://forums.cnet.com)

---

### Post by drawkcab on 2011-08-09
Install Firefox or Chrome.

---

### Post by unknownPoster on 2011-08-09
> **drawkcab said:**
> Install Firefox or Chrome.

LOLWUT

Internet Explorer is not Windows Explorer...

Ignore this OP.

---

### Post by drawkcab on 2011-08-09
> **unknownPoster said:**
> LOLWUT

Internet Explorer is not Windows Explorer...

Ignore this OP.

Ah, sorry.  I didn't read carefully and thought that the OP was referring to IE.

My mother's Lenovo will spin down the hdd if the computer is tipped or jolted in order to protect the drive from impact damage.  Perhaps this system is somehow malfunctioning?

---

### Post by JossyP on 2011-08-10
Thanks guys. No wonder I couldn't understand it. I'll try a Windows place. Cheers.

---

### Post by Joebewan on 2011-08-10
sevenforums.com

Seems to have some Windows 7 savvy geeks about.

---

### Post by haqking on 2011-08-10
As i orginally said there seems to be issue with one of ther services you mentioned.

Disable the Acvc and use Windows ZeroConfig for your wireless

None of this is to do with Internet Explorer as one post mentioned.

The AcSvc is a connections manager service so disable it.

The other service is power management for your notebook.

Wireless ZeroConfig should help if you lose radio

---

