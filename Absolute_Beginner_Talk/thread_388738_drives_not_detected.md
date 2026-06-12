---
title: "drives not detected"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Coldfrontt on 2007-03-19
during install, partion manager does not detect sataII drive. drive was already partioned and formatted using Gparted.(ext3)
drive is on an Asus P5B motherboard. Device manager shows Sata controller, but no hard drive.
Any ideas...I haven't found a solution on the forum

---

### Post by Coldfrontt on 2007-03-19
anybody?

---

### Post by nudnik on 2007-03-19
> **Coldfrontt said:**
> during install, partion manager does not detect sataII drive. drive was already partioned and formatted using Gparted.(ext3)
drive is on an Asus P5B motherboard. Device manager shows Sata controller, but no hard drive.
Any ideas...I haven't found a solution on the forum

This board has a component in the IDE channel that hates Linux. The "Jmicron" controller appears to be the culprit. I am told there might be kernel patches available, but install them at your own risk. May not be worth bothering with, perhaps best to get another board for a Linux install. There might be a BIOS update to fix this, but I wouldnt hold my breath. Remember the mascot....see below.

---

### Post by Coldfrontt on 2007-03-19
thanks....I'm very familiar with the mascot!

---

