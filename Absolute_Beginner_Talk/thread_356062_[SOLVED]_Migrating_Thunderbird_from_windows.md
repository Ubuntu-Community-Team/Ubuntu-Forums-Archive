---
title: "[SOLVED] Migrating Thunderbird from windows"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-02-08
How do you migrate your mail and address books from Windows?

I can see the files on the Windows version, but I haven't been able to find where the comparable data belongs on Linux.

Thunderbird seems to be kind of obtuse about importing data from earlier versions wen the new version is not installed over the old.

Thanks!

---

### Post by aysiu on 2007-02-08
Copy the C:\Documents and Settings\jrlii\Application Data\Thunderbird folder in Windows to /home/jrlii/.mozilla-thunderbird in Ubuntu

---

### Post by jrlii on 2007-02-08
Thanks!

Wow, that was fast!

---

### Post by aysiu on 2007-02-08
One qualification:

It's /home/jrlii/.mozilla-thunderbird if you're using Ubuntu's Thunderbird (the one from the repositories/Synaptic/Adept/Add-Remove Programs)

But it's /home/jrlii/.thunderbird if you're using Mozilla's Thunderbird (the .tar.gz from the Mozilla website).

---

