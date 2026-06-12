---
title: "Already installed, wont boot"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by pwrntspd on 2007-02-16
Ok, so i downloaded the iso, burned it to cd using infra and loaded it on my old powerspec pc- pIII 256mb ram.  Has a brand new hardrive.  Everything was working fine till till i took the cd out and rebooted it like it said to.  When i did, i just get a message saying that its not finding a bootable CD.  I checked the bios and made sure it wouldnt just boot from CD but it didnt fix the problem.  Is it hardware? or Bios?  Can someone help please?

---

### Post by pwrntspd on 2007-02-16
O yeah almost forgot this is version 6.06.  I kept having problems installing 6.10 so i tried this

---

### Post by panti19 on 2007-02-16
ubuntu doesn't need a cd to boot.
bios is to blame

---

### Post by mikewhatever on 2007-02-16
The boot order you set in BIOS should include your hard drive. It is customary to set the first booting device as CD-ROM or floppy, and the second as hard drive, so make sure your hard drive is there.

---

### Post by pwrntspd on 2007-02-16
Yeah, wierd thing is i tried that, every single boot order still wont work...im thinking it may have something to do with how i set the hardrive...cuz im not sure the bios is reading it.

---

### Post by igknighted on 2007-02-16
during the POST it should list your hardware, mine shows all my IDE drives and my SATA drive, my memory, and any USB filesystems connected.  Is your HD listed here?

Also, which disk did Ubuntu install grub to, do you remember?

---

### Post by pwrntspd on 2007-02-16
Yeah...its not showing my HD....and no i dont know which disk

---

### Post by pwrntspd on 2007-02-16
Ok so I tried repairing it by reinstalling GRUB on the HD, but im not sure i did it correctly and i  got a error "Code 20"

---

