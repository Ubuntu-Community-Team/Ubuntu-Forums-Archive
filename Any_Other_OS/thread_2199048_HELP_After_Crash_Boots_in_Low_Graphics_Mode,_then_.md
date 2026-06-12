---
title: "HELP After Crash Boots in Low Graphics Mode, then Stalls - Hardware Issue?"
date: 2014-01-11
forum: Any Other OS
---

### Post by bookrt on 2014-01-11
I could use some help folks. Here is what has happened. I was surfing using Chrome, got an error that I have gotten many times regarding keyring password. I went to password settings and set login keyring to empty. Came back to computer and screen was locked. Moved mouse and system was frozen.

Tried to reboot. Boots in low graphics mode but freezes with "Ubuntu 13.10" on the screen along with two errors: 

kvm disabled by bios
failed to execute /lib/udev/mto-probe mtp-probe /sys/deveices/pci00000:00/0000:00:ia.0/usb1/1-1/1-1.2 1.3 no such file or directory

I press ESC and boot readout indicates "fail" at the following lines: 

starting reload cups, upon starting avahi-daemon to make sure remote queues are populated 
starting MDM Display Manager

Checking my other system, the missing file seems to be a graphics driver. I can get into BIOS to enable virtualization. That clears the kvm error but I am still getting mtp-probe error and failure to start MDM.

Also tried using VGA output with old monitor and get same thing. Tried booting with LM16 and XUbuntu 12.04 LTS on USB sticks, still get same errors. Also tried editing GRUB to nomodeset but does not make a difference.

I can get into terminal using ALT-F6.

What have I done?

Running LM16 Cinnamon, Celeron g540, Biostar H77MU3.

---

### Post by QIII on 2014-01-11
*Moved to **Other OS/Distro Support***

---

### Post by bookrt on 2014-01-11
UPDATE Swapped CPUs with another computer with same result. Would this indicate failed MB?

---

### Post by bookrt on 2014-02-09
Problem was corrupted sector on boot drive. Replaced HDD and working fine now.

---

### Post by mips on 2014-02-10
> **bookrt said:**
> Problem was corrupted sector on boot drive. Replaced HDD and working fine now.

How many bad sectors does the drive have and are they increasing?

Might only need to reallocate the sector.

---

