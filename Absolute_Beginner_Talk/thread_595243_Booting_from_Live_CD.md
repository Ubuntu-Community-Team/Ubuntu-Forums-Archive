---
title: "Booting from Live CD"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by castep_nut on 2007-10-28
I have been running ubuntu for some time on a virtual machine. However, I wish to change my partition sizes, and therefore am trying to boot from CD rather than hard drive. 

At the moment, the CD is recognised by the system, but the system will not boot from the CD first.

Having read through various forums, suggestions seem to relate to changing the BIOS, but I am not sure about this.

Has anyone any advice as to how I can solve this problem? Thanks, CN.

---

### Post by mikeyphi on 2007-10-28
BIOS - Yes!!
You need to go into your BIOS - usually accessible during the start-up sequence (possibly by pressing the Del key) Go the boot option and set CDROM as the first option - don't worry, if there is no CDROM in the drive the next boot option is selected! Remember to save your settings!!

---

### Post by Pumalite on 2007-10-28
At boot you have to get into BIOS. Different for different computers: 'Del', 'Esc', 'F2' are some of the keys. Consult your motherboard Manual. Once in BIOS, go to 'Boot' and there change CD to first in boot order.

---

### Post by castep_nut on 2007-10-28
I wonder if the problem is that I am using a virtual machine. Upon starting there is the option to enter the GRUB menu but this is just to start recovery mode or a memory test. Is there perhaps an option within ubuntu itself (or VMware) to force boot from CD drive first.

---

### Post by Pumalite on 2007-10-28
You have to reboot your computer, then during boot hit the appropriate key to get into BIOS.

---

### Post by castep_nut on 2007-10-28
Thanks, that's that part of the problem solved

---

