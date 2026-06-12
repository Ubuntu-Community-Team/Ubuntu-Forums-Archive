---
title: "black screen"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2008-04-07
Hi guys

I have some problems after the update of my Ubuntu 7.10 about one and half month ago. My screen after 10 minutes of inactivity goes to be black. The screen saver is turned off and i don't have any other ideas. Any suggestion?

thx in advance

---

### Post by conjur3r on 2008-04-07
Is it in your power options?

---

### Post by mikeyphi on 2008-04-07
> **antonio_ing said:**
> Hi guys

I have some problems after the update of my Ubuntu 7.10 about one and half month ago. My screen after 10 minutes of inactivity goes to be black. The screen saver is turned off and i don't have any other ideas. Any suggestion?

thx in advance

Open System/Preferences/Screen Saver - look under the Power management box, there's a section about putting the screen to sleep when inactive.

---

### Post by antonio_ing on 2008-04-07
it was setted to never.

---

### Post by mikeyphi on 2008-04-07
The only other thing - Does your monitor have a sleep mode?

---

### Post by antonio_ing on 2008-04-07
how can I check it?

---

### Post by mikeyphi on 2008-04-07
> **antonio_ing said:**
> how can I check it?

Is there a set up program or a hard key menu option on the monitor?
Often there is set up software for windows provided with the monitor.

---

### Post by antonio_ing on 2008-04-07
It is strange expecially because it worked fine with ubuntu 7.10 until 2 months ago. i don't know exactly where to find the hard key option

---

### Post by antonio_ing on 2008-04-07
Should I change the acpi options in the menu.lst??

---

### Post by antonio_ing on 2008-04-07
This are my options:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3f87f426-411a-44a8-bdb2-6edaa552a3df ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---

