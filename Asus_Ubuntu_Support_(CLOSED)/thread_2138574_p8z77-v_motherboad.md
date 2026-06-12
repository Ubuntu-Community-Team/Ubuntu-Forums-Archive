---
title: "p8z77-v motherboad"
date: 2013-04-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tony van on 2013-04-24
I have a p8z77-v lx motherboard and I want to dual boot xp x86 (already installed) and Ubuntu 13. Ubuntu is a new install. can I use amd64 ? boot set to IDE. the only reason I want to use AMD64 is I read it is compatable with [UEFI]("https://help.ubuntu.com/community/UEFI?action=fullsearch&value=linkto%3A%22UEFI%22&context=180"). suggestions please. thank you

---

### Post by ajgreeny on 2013-04-24
Go with it!   I have an Asus P8H61-MX USB3/SI: uATX mb with Xubuntu 12.04 64 bit on it, an i5-3570K and 8GB ram, which works like a demon, and I have installed in UEFI mode, though I don't have any M$ windows to dual boot with.  I don't think that should make any difference to you, however, as XP did not and will not have any secure boot problems to worry about as far as I'm aware.

---

### Post by oldfred on 2013-04-24
XP does not see gpt partitioned drives and will not boot from them.

UEFI requires gpt partitioning. 
Windows Vista64 or Windows 7 only boots from gpt partitioned drives with UEFI.

Best if entire system has all drives as either BIOS mode or UEFI mode. 
You can have Ubuntu boot from gpt drive, with XP booting from MBR(msdos) drive as I did that from 10.10 until I installed my new SSD which required AHCI and my XP did not have those drivers.

---

### Post by ajgreeny on 2013-04-26
Sorry!

I didn't know that about XP, but then its a long time since I used windows, and I have no reason to even query whether it would work or not; I just knew Ubuntu would be fine.

---

