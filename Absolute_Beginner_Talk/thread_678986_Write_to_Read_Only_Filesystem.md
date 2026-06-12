---
title: "Write to Read Only Filesystem?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2008-01-26
I'm dual booting Feisty on a Dell and need to get Internet Explorer working on the XP side.  (i had been trying to be ubuntu only on this machine but have been hobbled by continuing problems with ies4linux...)  Anyway, I don't remember how to set-up 'Net access on windows so I've used firefox and downloaded the installation file from my ISP  (it's an .exe file).    

Trouble is, I'm unable to move it to the XP partition as I think there are some permission problems or limitations I don't understand.  I tried copying to the XP partition using the GUI and get "you don't have permission"  I've tried copying via the command line and get an error about writing to a read only file system...

I'm pretty sure the file system is NTFS...  is there a way to move this file from the ubuntu partition to the windows partition?

---

### Post by Keith Hedger on 2008-01-26
I.ve long since dumped my windows install but i do remember a similar problem and the only folder i could save things to was the "my documents" folder on the windows partition (I think i also had to do as root)

---

### Post by taurus on 2008-01-26
If you want to write to ntfs filesystem, you need to install and use ntfs-3g driver.  NTFS driver would only let you read from it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by zmike1 on 2008-01-26
Thanks.  ... someday, maybe I'll understand what I'm doing...

---

