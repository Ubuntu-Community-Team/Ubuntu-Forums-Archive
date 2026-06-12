---
title: "Reverting to Windows, file transfer &amp; format help"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by theknave on 2007-01-18
Hello everyone.

Regretfully, Ubuntu is not for me. I gave it fair opportunity, but I had too many problems which were not fixable, and I need to have Windows on my machine for work and I'm not a fan of running a dual-boot system. It IS a very good OS, just not for me.

That said, I'd like to transfer some files to my NTFS drive and format the drive so I can put Windows XP files on it. Now here's the biggest issue: I formatted my NTFS drive, and Ubuntu was not a fan of that decision. Grub was annihilated, and I was not able to reinstate it, possibly because I didn't care enough to sort through the issues I faced doing it.

This said, it would be preferable if there were a way to mount my Ubuntu drive from Win XP for easy copying to the XP drive, and then a simple way to format the drive and un-partition it.

Is this all possible? Or am I just SOL for the important files and the space that is offered by that hard drive?

Thanks a lot,
Brett

---

### Post by KuriKai on 2007-01-18
What format is you ubuntu instalation on? ext3, reiserfs?

You coul always burn the files to a dvd and copy them to the ntfs

---

### Post by theknave on 2007-01-18
I don't know. It's Dapper Drake, and I didn't change anything from the defaults in my installation. =/

As far as burning the files to DVD, I'd like a solution that doesn't require me going into the Ubuntu thing, because then I have to fix the Grub problem first.

---

### Post by qamelian on 2007-01-18
Probably the easiest option is to go to: [http://www.fs-driver.org/](http://www.fs-driver.org/) and download the ext2 driver for Windows. Once it's installed, you'll be able to see the contents of your Ubuntu partitions from Windows and copy the files you want back to your Windows drive.

---

### Post by theknave on 2007-01-18
Thank you, Qamelian. Sounds like exactly what I was looking for.

---

### Post by qamelian on 2007-01-18
> **theknave said:**
> Thank you, Qamelian. Sounds like exactly what I was looking for.

No problem. Sorry to hear that Ubuntu wasn't your cup of tea.

---

