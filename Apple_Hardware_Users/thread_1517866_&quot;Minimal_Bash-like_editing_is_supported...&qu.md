---
title: "&quot;Minimal Bash-like editing is supported...&quot; (MacBook, early 2008)"
date: 2010-06-25
forum: Apple Hardware Users
---

### Post by rogueofmv on 2010-06-25
I was triple-booting on a MacBook 13" (early 2008) for a while, but never really used Linux. I recently did away with the Kubuntu partition of my hard drive, as well as the swap partition, and reintegrated the free space back into Macintosh HD, which really needed the extra space. But now I can't access Windows, because the GRUB bootloader is broken! When I select Windows, whether from rEFIt or from Apple's bootloader, it goes to a blank GRUB command prompt with the "Minimal Bash-like editing is supported" message at the top.

Can someone help me access Windows again? I'm in desperate need!

---

### Post by linux-hack on 2010-06-25
where did you had your grub installed ? I meen on witch partition?

try reinstalling the grub.. and how did you do actually to give the space for the mac OS.. give a little more info please... partitions etc..

---

### Post by rogueofmv on 2010-06-25
> **boogy9 said:**
> where did you had your grub installed ? I meen on witch partition?

try reinstalling the grub.. and how did you do actually to give the space for the mac OS.. give a little more info please... partitions etc..

I'm not sure which partition it's installed on... I haven't paid attention to that for quite some time.

To reintegrate the space, I booted a Live CD of Ubuntu and used gparted to erase the Linux partition (disk0s3) and the swap (disk0s5), then used Disk Utility in OSX to extend Macintosh HD to fit all that free space. Windows was on (disk0s4), but looking at it in Disk Utility, it seems to be on (disk0s3) now.

---

### Post by rogueofmv on 2010-06-26
EDIT: I solved it myself. Apparently all I needed was a simple fdisk -u. Thanks again!

---

### Post by linux-hack on 2010-06-26
Well glad I helped you LOL HAHA..

---

