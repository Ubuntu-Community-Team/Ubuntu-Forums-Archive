---
title: "How to make Ubuntu run faster"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by chewit on 2007-12-29
Hi

I have been using Ubuntu now for exactly a week. I'm starting to see some speed issues, its starting to becoming slower.

I'm using 7.10, Could you tell me ways to spped up Ubuntu, nothing too technical please.

---

### Post by chewearn on 2007-12-29
> **chewit said:**
> Hi

I have been using Ubuntu now for exactly a week. I'm starting to see some speed issues, its starting to becoming slower.

I'm using 7.10, Could you tell me ways to spped up Ubuntu, nothing too technical please.

Quick questions:
1. What hardware have you got?
2. What are the exact speed issues you have?

---

### Post by chewit on 2007-12-29
Well, My PC was running fine when I first started. Its 800Mhz and 256mb RAM PC. Its starting to be a bit slow loading Apps and even pressing the shutown button to bring up the shutdown menu is now slow.

---

### Post by RomeReactor on 2007-12-29
Hi. You can start by disabling some services that you don't need in "System->Preferences->Sessions"; such as "Print Queue Applet" if you don't have a printer, "Bluetooth Manager" if you don't have any bluetooth devices, "Tracker" if you don't use the Deskbar Applet search function, "Evolution Alarm Notifier" if you don't use Evolution. If you have 256 MB of memory or less, you could try the Xubuntu desktop, which is less resource intensive than Gnome.

Obviously if you use desktop effects that in itself is a performance hit.

---

### Post by sailor2001 on 2007-12-29
gutsy should have 512 ram+   add a stick

---

### Post by Sef on 2007-12-29
Ubuntu can run on 256, but it will not be fast.   To speed it up, do as sailor2001 suggests - get more ram.  I had a PIII (1.3 GHz) and 512 ram and it ran fine.

---

### Post by oldb0y on 2007-12-29
Ram is quite cheap these days, so if you have the funds to it, do a little upgrade. If you do not have any spare change lying around, you could try Xubuntu, which will be lighter on your system. Good luck!

---

### Post by chewit on 2007-12-29
I have disabled startup apps already. I have tried Xubuntu, i don't really like, doesn't have all the features uBuntu has. And I have maxed out my motherboard

---

### Post by roaldz on 2007-12-29
> **chewit said:**
> I have disabled startup apps already. I have tried Xubuntu, i don't really like, doesn't have all the features uBuntu has. And I have maxed out my motherboard

Than maybe you could replace some memsticks?

---

### Post by chewit on 2007-12-29
This is coming from the Windows in me. But when I had a slow Windows PC. I used ScanDisk and DeFrag the Hard Drive. I also used CCleaner to clean out all the junk. Is there anything out there for Linux like that,

---

### Post by Sef on 2007-12-29
> I used ScanDisk and DeFrag the Hard Drive. I also used CCleaner to clean out all the junk. Is there anything out there for Linux like that,

Ext3 automatically defrags about every 25-30 times.

---

### Post by oldb0y on 2007-12-29
Perhaps a stupid question, but have you disabled all the Visual Effects?

---

### Post by bwtranch on 2007-12-29
Don't have any specs on your hardware, but it's sounding like you have an older machine. You're just not going to get the performance with 256K. Someone said 512K, but I wouldn't go for anything less than a Gig. Graphics card? CPU clock speed? If money is tight you can build a really nice machine for $500. Order the parts from the US, dollars are cheap these days. :) Seriously, you can do all the tweaks mentioned above, but it's not going to make that much difference until you upgrade the hardware. Cheers!

---

### Post by chewit on 2007-12-29
All the visual effects are off. My PC is maxed out. I don't really want to upgrade. I have a work PC which runs Ubuntu. A gaming PC which uses Windows.

---

### Post by philinux on 2007-12-29
Have you checked the indexing prefs under System>Prefs>Indexing.

trackerd can slow things down.

also from terminal use the command 

top

to see what consuming most cpu resources.

---

### Post by chewit on 2007-12-29
What would you suggest to change in Indexing. I havn't got a clue what it is or what to change,

---

