---
title: "Dell's Offering NTFS or FAT32 - Which One?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by twoseids on 2006-06-23
I'm looking at buying a Dell Latitude (either the D520 or D620). I have one question:

I notice that they offer the option of choosing NTFS for all file systems or FAT32. Considering that I plan on dual-booting, and using Ubuntu 95% of the time, should I go with the FAT32 option? Would that affect any of my files from my current system when I bring them over? Okay, that's two questions.

Thanks in advance for your advice!

---

### Post by aysiu on 2006-06-23
Are your files bigger than 4 GB each?

---

### Post by ssalman on 2006-06-23
With NTFS you will not be able to write to your windows partition from ubuntu, but you can read from windows just fine, that means that you can use your windows files by copying them to Ubuntu's partition, but you can save back the changes to your windows partition.

With FAT32, you can do both read and write... the catch is you are limited to 4GB for your file sizes... if you're not doing any video editing/DVD burning you'll be okay, other wise you'll be better off with NTFS and a small shared partition with FAT32 to save common files.

hope this helps.

---

### Post by trent dillman on 2006-06-23
How about both? Use NTFS for XP system files and FAT32 to share with Linux?

As for transferring your existing files, the file system shouldn't matter if you're using some other media to do the transfer (e.g., net, cd/dvd, usb). If you're adding an old hard drive, use it as a slave, use Linux to transfer files to the FAT32 partition on the new drive (so Windows doesn't get confused, as it likes to do sometimes when it finds system files on other filesystems).

---

### Post by twoseids on 2006-06-23
[QUOTE=ssalman]With FAT32, you can do both read and write... the catch is you are limited to 4GB for your file sizes... if you're not doing any video editing/DVD burning you'll be okay, other wise you'll be better off with NTFS and a small shared partition with FAT32 to save common files.

hope this helps.[/QUOTE]

It does, thanks. I've been working with my NTFS Windows partition for some time now and it's not too much of a hassle. So I think I'll just stick with that on my new Dell just in case I do have some big file in the future. I didn't know about that 4GB limit. Appreciate your tips!

---

### Post by ssalman on 2006-06-23
Glad I could help...

[here ]("http://en.wikipedia.org/wiki/File_systems")is some info on filesystems, in general... just for referance :)

---

