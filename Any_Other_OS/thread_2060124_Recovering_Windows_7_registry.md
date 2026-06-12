---
title: "Recovering Windows 7 registry"
date: 2012-09-19
forum: Any Other OS
---

### Post by Spets_Naz on 2012-09-19
Hi there.

I tried to find something similar to my problem by googling but didn't have any luck.

Here is the problem. I have messed my registry after using a program to uninstall and mistakenly removed registry entries that shouldn't have been touched. Now my windows starts however I can't open anything or any folder since it has no associations.

I do have 4 backups in a .reg files. I was trying to restore my registry with those backups but I cannot enter the safe mode neither open registry/cmd prompt and like I said before cannot open anything at all.

My question is if anyone knows if there's a way to "merge" the last .reg file I have with the registry so I can recover it. Using ubuntu of course.

Thanks in advance

---

### Post by howefield on 2012-09-19
Thread moved to "*Other OS/Distro Talk*"

---

### Post by CharlesA on 2012-09-19
Boot a BartPE cd, load the hive offline, import the registry and pray you don't bork it more than it is now.

---

### Post by Spets_Naz on 2012-09-19
> **CharlesA said:**
> Boot a BartPE cd, load the hive offline, import the registry and pray you don't bork it more than it is now.

It shouldn't be since I've done the same mistake before but restoring the registry using one of my backups resulted perfectly.

I'm sorry but I'm new to BartPE but is that some kind of bootable windows? If I use that I can open the .reg file and rewrite the missing reg entries with my .reg file?

---

### Post by CharlesA on 2012-09-19
You might have to rewrite the reg file to point to the path of the loaded hive, but that shouldn't be too bad.

See here:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by Spets_Naz on 2012-09-19
Thanks I'm going to try that. I'll give a feedback.

---

### Post by NormanFLinux on 2012-09-20
> **Spets_Naz said:**
> Thanks I'm going to try that. I'll give a feedback.

You could saved yourself all that trouble with Rollback RX. If you mess something up or your computer crashes, you can restore it at boot to a time when it last worked.

Much better and more granular than Windows Restore.

---

