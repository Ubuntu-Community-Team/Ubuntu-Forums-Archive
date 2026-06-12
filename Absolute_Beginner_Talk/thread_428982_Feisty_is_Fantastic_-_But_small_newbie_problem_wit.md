---
title: "Feisty is Fantastic - But small newbie problem with ntfs-config"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-04-30
Hi all, this is my first post to this or any forum so please forgive any mistakes in etiquette (I will improve)

I have just installed Feisty on my AMD64 (Dual boot with XP).  I have attempted various distros and versions over the years, but this one to date has convinced me to jump ship to open source - great job to all those who have contributed.  Its fast, neat, different, highly configurable, does everything I want now and with the amount of software available, everything I might do in the future (even things I haven't thought of yet)

The problem - I have installed ntfs-config in an attempt to make the windows partitions accessible to Linux in read/write mode rather than the default read only.  This works fine, but now I seem to have broken the neat gnome automounting of partitions in read only mode, and can only open and close through the terminal window using superuser access.  Not a big deal, but I would prefer to restore it to where it was before if possible.  

I noticed that I have 2 versions of fstab now, one labelled fstab-pre-ntfs.config.  Would overwriting the existing fstab file with fstab-pre-ntfs.config restore the automount functionality in Gnome?  Any other ideas are greatly welcomed.

Regards.

---

### Post by scrooge_74 on 2007-04-30
if you use the pre-ntfs you will probably go back to your original setting.

For the read/write i went with the manual versionon how to get NTFS read/write support and worked very good for me

---

### Post by Drifter on 2007-04-30
In automatix there is a program for NTFS file conversion etc. I don't know it that will help you or not for what you want to do look it over.

---

### Post by neotasic1 on 2007-04-30
I have used the manual setup several years ago in a different version of Linux, and it worked fine - guess I got lazy and looked for a fast and gui fix.

---

### Post by neotasic1 on 2007-04-30
> **scrooge_** said:**
> if you use the pre-ntfs you will probably go back to your original setting.

For the read/write i went with the manual versionon how to get NTFS read/write support and worked very good for me

I have tried restoring the pre ntfs fstab file to etc/fstab, but it hasn't fixed the problem. I can only presume that other configuration changes have been made, but i don't know where to look for them.  Any other suggestions as to where I might start?

---

### Post by neotasic1 on 2007-04-30
Thanks for the help guys, but I have fixed it.  Turns out the pre-ntfs-config version of fstab was the same as the modified one, (for reasons unknown)  but fortunately I had a copy of a clean Feisty install on a separate partition that had the original fstab intact.  Copy and paste - hey presto.

---

