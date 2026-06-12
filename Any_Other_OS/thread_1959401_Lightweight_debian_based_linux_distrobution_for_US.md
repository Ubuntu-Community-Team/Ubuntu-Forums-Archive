---
title: "Lightweight debian based linux distrobution for USB"
date: 2012-04-15
forum: Any Other OS
---

### Post by Fwission on 2012-04-15
Is there a linux distribution out there that can run on a USB quickly (like live CD speeds) that supports actual installing?

Right now I have puppy linux on my USB and it runs great but I wish it was debian based so it had more familiar software and easier to learn.

I tried installing ubuntu on USB but it ran slowly and lagged clearly. I realize I can use a USB creator tool but it limits the size to 4gigs and doesn't allow clean system upgrades.

---

### Post by oldfred on 2012-04-15
Puppy runs well since it is all in RAM once loaded.

How large is flash drive. I installed the full Ubuntu 12.04 to a 8GB partition to test on my laptop. Works ok, not really speedy loading larger applications or writing, but functional.

Many suggest Lubuntu as it is more lightweight. But you also need to modify settings on the flash drive to reduce writes.

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

this was Ubuntu but the procedure would be essentially the same for Lubuntu:
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by Plumtreed on 2012-04-16
Google Slitaz for a complete, effective OS that is very fast and installs to small USB 'pendrives'.

Works in ram from live CD or Live USB.

---

### Post by Peripheral Visionary on 2012-04-16
[Knoppix]("http://knoppix.net/") is *meant* to be run from a CD or pen drive rather than installed. It's Debian-based and really fast. LXDE interface, too, for simplicity and speed.

---

### Post by Fwission on 2012-04-16
> **oldfred said:**
> Puppy runs well since it is all in RAM once loaded.

How large is flash drive. I installed the full Ubuntu 12.04 to a 8GB partition to test on my laptop. Works ok, not really speedy loading larger applications or writing, but functional.

Many suggest Lubuntu as it is more lightweight. But you also need to modify settings on the flash drive to reduce writes.

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

this was Ubuntu but the procedure would be essentially the same for Lubuntu:
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

I used both ubuntu 11.10 and Linux mint debian xfce and they both had clear menu lag, like mouse getting stuck and freezing on certain menus. 

I'll check knoppix out since its Debian based, I liked puppy but it just seemed a little confusing which I prefer to avoid

---

### Post by Peripheral Visionary on 2012-04-16
I'm going to have a look at SalineOS if the next Xubu LTS is too heavy for my hardware. It's "almost pure" Debian with Xfce and simplified for casual users like me. *Very* lightweight, so I hear. Intended for installation on a HDD, unlike Knoppix. Just say'n.

---

### Post by wojox on 2012-04-16
[Dreamlinux 5]("http://www.dreamlinux.info/")

---

### Post by futura84 on 2012-04-17
[www.peppermintos.com]("http://www.peppermintos.com") 
 
Based on Lubuntu --> Ubuntu --> Debian
 
Very low on bloatware

---

