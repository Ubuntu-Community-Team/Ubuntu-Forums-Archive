---
title: "what is the hdparm service?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-11
What is the hdparm service and would it be wise to disable it?

---

### Post by anaconda on 2007-02-11
With hdparm you can set parameters for IDE CD/DVD drives, and IDE hard-disks, and it is useful. For example in Dapper (6.06) CD-drives didn't dave DMA enabled by default. Enabling it made the drive a lot faster.

In Edgy you can adjust the hdparm settings and make CD/DVD:s faster.

I wouldn't remove it

try man hdparm to get info of the command. I think the hdparm service just keeps the selected settings..

---

