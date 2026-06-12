---
title: "Trouble booting from Live CD"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by don skoog on 2007-01-09
Hi guys,

I have a Thinkpad 600.  I burned an "ubuntu-6.10-desktop-i386.iso" CD on my Mac (Thinkpad has no burner) and transfered it.

The Cd boots to the first page but when I click "Install" or "Test" I get this:

[56.3110351] invalid compressed format (err=2)
[56.3160041]Kernel panic-not syncing:VFS:unable to mount root fs on unknown-block (1,0)
[56.316071]_

The cursor is unresponsive so I can't type anything in.

Any ideas? 

Don

---

### Post by jvc26 on 2007-01-09
My advice would be carry out an md5 checksum on the .iso you downloaded, and run a disk check on your live cd - it sounds like either there is an error with your download (download again/use a torrent to download it) or you have got a burn error.
Il

---

### Post by larryd85 on 2007-01-15
i have this exact laptop and i get the exact same error.

i downloaded the image off of ubuntu's website

---

### Post by lilicalf on 2007-02-09
I am using the same laptop and the same CD and getting the same error messages. I checked the CD on a HP pavilion, which booted and loaded the live system. I checked the CD from there; it is ok.

I looked at the boot options, via F6. They are:
"file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- "

I removed the "quiet" from the boot options. I got a much longer list of messages, not all of which could I follow; Ctrl-s does not seem to work.
Between the "invalid compressed format (err-2)" line and the "Kernel panic ..." line there is "No filesystem could mount root, tried:  cramfs"

I tried looking at the initrd.gz file with 7-zip. It says the compressed image is ok.

I will keep looking elsewhere and check back here.

---

### Post by taithson on 2007-02-26
Hello, I just had this same problem, in a 600x machine, and was fixed with Bios update.
Go to IBM/Lenovo site and update the Bios of your machine to last level.
[http://www-304.ibm.com/jct01004c/systems/support/pc/](http://www-304.ibm.com/jct01004c/systems/support/pc/)
It will fix the problem.
:)

---

