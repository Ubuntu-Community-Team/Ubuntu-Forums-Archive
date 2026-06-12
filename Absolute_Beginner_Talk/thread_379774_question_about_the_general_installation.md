---
title: "question about the general installation"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-03-08
HI

  I  am going to make this short and sweet. I want to install Linux, and I looked through the Graphicalinstall, and it seems pretty simple, and clears things up for me. but i still have a couple questions. the first question is, does the installer automatically install GRUBS? or do I have to manually install/setup myself? Another question is regarding the partitioning, if I were to use a fresh hdd, do i have to do any manual partitioning, and also, I m still a little confused abou the partitioning. in the graphicinstall, it says to choose the amount of space for the partitions, so what would I do for that? 
thanks for the help'



-sewercake

---

### Post by taurus on 2007-03-08
The installer will install GRUB to MBR or wherever else you choose.  The default is MBR.

You don't need to do anything to that harddrive.  Just tell the installer to use the whole disk and it knows how to handle it from there.  It will create two partitions for you: / (/dev/hda1) and swap (/dev/hda5).

---

### Post by pjones0404 on 2007-03-08
the instaler will set up grub for you.

in regards to the partitioning, if u have a new hdd, then all u will need to do is a create a swap partition and make all the remaining space for the install.

i normally crete an extra partition when i am doing it to store stuff on in case i ever need to reinstall i dont lose everything.

---

### Post by sewercake on 2007-03-08
> **pjones0404 said:**
> the instaler will set up grub for you.

in regards to the partitioning, if u have a new hdd, then all u will need to do is a create a swap partition and make all the remaining space for the install.

how big should I make the swap partition, and thank you guys, this clears things up, it seems A LOT more easy than what I thought at first

so just to clarify again, all I need to do, is have the extra hdd, then run the installer from the live desktop???
thankyou very much



-sewercake

---

### Post by taurus on 2007-03-08
How much RAM do you have?  You probably don't need anything more than 512MB but 1GB of swap should be good.

---

### Post by sewercake on 2007-03-08
I have 512mb of RAM on my machine, will this be a problem?

---

### Post by rusty4r on 2007-03-08
No, 512mb is just fine. swap files are generally 2 x ram (1 Gig max)

---

