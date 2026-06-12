---
title: "help a gnu luser"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by sambo. on 2006-01-10
heya, is there an "idiots guide to installing ubuntu" anywhere, my search foo hath failed me.

so far, i have downloaded the Ubuntu 510 i386 iso and burnt it to disc.

disc is in the cd drive of a celeron 1.4g


what now? how do i actually "get" it onto the box? the "release notes" and FAQ seem to assume one has gotten past this stage, but alas, i have failed.

cheers and thanx in advance your help.

sambo.

---

### Post by Sef on 2006-01-10
A) For installation help, this is great:

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

B) When u downloaded Breezy, did you do an md5sum check on it to make sure it downloaded correctly?  (If you used Bit torrent, it would do it automatically.)

C) Did you set your BIOS so it boots from your CD-ROM or CD-Writer before it boots from your hard disk?

---

### Post by hashimoto on 2006-01-10
Did you burn the downloaded iso-file to a cdrom as a image? It won't boot if you burned it as a normal data file.

---

### Post by az on 2006-01-10
You need to tell your computer to boot from the cdrom first.  Look for "boot sequence" or "boot order" "boot device" in your bios and change that to make it look to the cdrom before looking at the hard drive. To acess your bios, it depends on the machine.  While booting you need to press "del" or "F1" or some other key - it is usually displayed for a few seconds just as you power on yourcomputer.
If there is no cdrom in the drive or if the cdrom is not bootable, it will look to the next device on the list.  So, you do not neccessarily have to switch it back once you have installed.

---

