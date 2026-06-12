---
title: "dual booting on macbook"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by SeveringGecko on 2007-10-21
okay well i have upgraded to a MacBook Pro and want to use my old macbook as a dual Ubuntu and Mac OS computer.

how would i partition and install ubuntu? 

and can i remove the ubuntu side should i give the macbook to my girlfriend?

---

### Post by cyberdork33 on 2007-10-21
> **SeveringGecko said:**
> how would i partition and install ubuntu? probably easiest to use bootcamp, then in the ubuntu installer, delete the windows partition,  and tell it to use the free space. 

> and can i remove the ubuntu side should i give the macbook to my girlfriend?
why would you want to do that? She can use Ubunu too! Ok, but in the reality, yes you can. You can either reinsall OSX altogether (might be better option at that point) or you can delete the ubuntu partion(s), use boot camp to "create" a new partition, then tell it to restore the partition to one piece, and it will combine all the unused space... Kind of a workaround, but  it works.

---

### Post by DGortze380 on 2007-10-21
gparted will work for partitioning as well.

---

### Post by MichaelSwengel on 2007-10-21
I use BootCamp on my MacBook Pro. It works AMAZINGLY. All you need to do is install Bootcamp in OSX and partition your disk there. Then, when it asks for a Windows CD/DVD, kill the Bootcamp Assistant. Put your Ubuntu disk in the drive and reboot. As you hear the chime and see the white/grey screen, hold down the option key. You'll have an option to start from the Macintosh HD or a CD. The CD may just say "Windows" as a label. Ignore that error and click the CD. Wait for Ubuntu to load, click on "install" on the desktop, and choose the partition that you created in OSX. It should be in NTFS format. Make sure NOT to pick a partition that says EFI or Macintosh HD. If you do that, you will overwrite your OSX installation.

---

