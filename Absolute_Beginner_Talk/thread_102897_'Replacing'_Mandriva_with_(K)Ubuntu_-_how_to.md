---
title: "'Replacing' Mandriva with (K)Ubuntu - how to?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by nmatheis on 2005-12-13
Hello
I've loaded up Mandriva on my old desktop box (P3 500mHz, 256k, 80GB HD) at home and also have Kubuntu on an old laptop.  Kubuntu seems to be a nicer package so far (except for my Plug N Play mounting woes: [http://ubuntuforums.org/showthread.php?t=102891]("http://ubuntuforums.org/showthread.php?t=102891")) and I'm wondering how to easily dump Mandriva and replace it with (K)Ubuntu if I should so desire in the near future.  Right now, my HD is ~60GB NTFS with Win2k and ~20GB auto-partitioned during the Mandriva install.  Any help provided would be greatly appreciated!
Thanks!
Nikolaus

---

### Post by linbetwin on 2005-12-13
You can install Kubuntu on the Mandriva partition (formatting it during the installation) and put GRUB on the MBR. Any particular issues?

---

### Post by nmatheis on 2005-12-13
[QUOTE=linbetwin]You can install Kubuntu on the Mandriva partition (formatting it during the installation) and put GRUB on the MBR. Any particular issues?[/QUOTE]
Thanks for the reply!  Sounds about like I thought it'd be - throw in the install cd, tel it where to reformat/install, and let it go.  I remember reading over how to install dual-boot with Windows and will probably look that up again.  There will be a clear, easy to understand part of the install where I choose to override the Windows boot with the dual-boot option?
Thanks!
Nikolaus

---

### Post by linbetwin on 2005-12-13
The only difficulty with dual booting is shrinking the Windows partition. But since you already have a Mandriva partition (and want to replace that distro) you don't have to worry about partitioning. Just make sure you format and use the right partition (not the NTFS one) and choose yes when asked whether to install GRUB to the MBR.

---

