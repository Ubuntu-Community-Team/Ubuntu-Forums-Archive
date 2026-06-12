---
title: "How to compile 2.6.19 with Promise TX4 SATA2 Support?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-12-15
Hi,

  I'm trying to compile the 2.6.19 kernel with support for my Promise SATA II 300 TX4 card. It is working in my 2.6.17 386 and generic kernel. However now that I'm compiling my own, I'm not sure how to put it in. I know it uses SCSI drivers and the libata library as per this [http://www.kernel.org/pub/linux/kernel/v2.4/ChangeLog-2.4.30]("http://www.kernel.org/pub/linux/kernel/v2.4/ChangeLog-2.4.30").

  I am following this guide [http://www.howtoforge.com/kernel_compilation_ubuntu_p2]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2").

  Where in the "make menuconfig" do I enable libata? Or is this part of the SCSI drivers? I have enable "SCSI device support", "SCSI disc support" and "SCSI generic support" which I think might include libata, however I want to make sure, since brute forcing this kind of thing when compiling takes hours I'm sick of taking that route.

  Any help is much appreciated.

---

### Post by pay on 2006-12-15
It it worked with the generic ubuntu kernel then why can't you just use the same config file that it used?

---

### Post by uriahs on 2006-12-15
I used the config file from both of those, but that still didn't load it in, when I would boot up it would say it's not a ext2 super block. However it works fine here. I'll give it a try with the SCSI libraries loaded in.

---

### Post by uriahs on 2006-12-15
Excellent found it...

Under "Device Drivers" ->
"Serial ATA (prod) and Parallel ATA (experimental) drivers" ->
Select "ATA device support" ->
and Select "Promise SATA TX2/TX4 Support"

We'll see how it turns out.

---

### Post by thor918 on 2007-01-30
hi. I too have that card.
did you get the hotplug functionality working?
I really want:
1.hot plug functonality
or
2. a command to just scan trough the bus for changes...
   so that if I put a sata disk into the computer I can issue a scan and the disk would be detected in /dev/sd*

---

