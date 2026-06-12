---
title: "Identify Ubuntu Partitions from Windows 7"
date: 2013-10-10
forum: Any Other OS
---

### Post by Jonathan_Dodi on 2013-10-10
I am attempting to overwrite Ubuntu with Mint 15. My computer is dual-loaded with Windows 7 and Ubuntu. Ubuntu is having boot issues (tried running boot repair, and it didn't fix it), so I was wondering how I can identify which partitions are being used by Ubuntu FROM WITHIN WINDOWS 7. That way I can install Mint over the Ubuntu partitions.

---

### Post by oldfred on 2013-10-10
Moved to other OS.

You cannot, Windows does not properly see Linux partitions. But you should not need to. Just install.
Is Windows in UEFI or BIOS boot mode? Or is drive MBR(msdos) or gpt(GUID)?

You can use gparted from liveDVD or flash drive or use gparted liveCD. Do not know if Mint has gparted on its live version or not, but would guess it does.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

