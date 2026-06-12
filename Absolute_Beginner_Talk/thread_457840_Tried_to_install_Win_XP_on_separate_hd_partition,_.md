---
title: "Tried to install Win XP on separate hd partition, now can't access Ubuntu"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-05-29
I had an unused partition on an hd that I just recently tried installing Windows XP on. I was able to copy files to the hd, but when the installer reset the computer, I was greeted with the following error:

"TRAP 0000000D ======================= General Protection Fault ==================

tr=0028 cr0=00000011 cr2=00000000 cr3=00000000
gdt limit=03FF base=00017000 idt limit=07FF base=00017400
..."

I removed windows from the unused partition and I still receive this error when I try booting into Ubuntu. When I was installing, I made certain I was installing to the unused partition and not the Ubuntu partition.

Is there any way I can recover my Ubuntu setup from this or am I pretty much out of luck?

---

### Post by cbilljones on 2007-05-29
Im pretty new to linux, myself; however it sounds to me like you need to repair your grub boot loader. I'm sure there are good guides here to help you along;), i recommend doing it with your install disc in a terminal, or with a knoppix distro - as ive had good results with that in the past.

All said i suggest waiting for a more knowledgeable peer to help you further:)

---

### Post by blackened on 2007-05-29
Windows likes to take over the master boot record when you install it. That's why it's customary, in a dual boot setup, to install Windows first and Ubuntu (or any other OS) second. I don't think it's possible to recover from this short of using the live cd to work some magic by (re?)installing grub.

---

