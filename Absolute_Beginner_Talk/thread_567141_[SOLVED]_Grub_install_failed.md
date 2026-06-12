---
title: "[SOLVED] Grub install failed"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-10-04
Hello,

I used a freshly-burned 7.10 live CD to create partitions for Ubuntu (2 logical drives, one of them a Swap partition) and since I didn't want Grub to overwrite the disk's MBR I told it to install in hda5, which is my Ubuntu partition. I got an error message though that the installation of Grub had failed so predictably, I can't boot into Ubuntu now. 
What did I do wrong? Should I reinstall?

---

### Post by milton1 on 2007-10-04
you can re-run the install and skip to the "install grub boot loader" step

---

### Post by Niniel on 2007-10-04
Ah, cool, I'll do that. Thanks.

---

### Post by molly_001 on 2007-10-04
You can also use any *buntu Live CD to run a grub module from the terminal which will do that work very quickly.  For this, you need to know which partition contains your *buntu installation -- you clearly know that information.

Read all about it here:
The part which applies to your case starts with this text (about 1/3 way down on page): "Find your Ubuntu Live-CD (other Live discs may also work) and boot it. Then launch a terminal:   >sudo grub ..."
here:  [http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

---

### Post by Niniel on 2007-10-07
Well, none of this worked, Grub just kept on claiming that it couldn't find the hardware.
So I finally deleted the partition/s and re-created them as primary partitions. THEN Grub installed ok during installation of the system.
So now I have Gag as my primary boot menu, and Grub as the secondary one (boots into Ubuntu, but also into Win if I ever change my mind :) )

---

