---
title: "Can't see some files on NTFS windows partition"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by jimbouzouf on 2007-09-13
Hello,

I got Ubuntu on dual-boot with windows XP

I use ntfs-g3 and I have successfully mounted the NTFS partition I want. Now I can see it, read and write on it with no problem however all files name containing characters such as éèà etc... are invisible on linux... 

According to ntfs-3g Q&A :

> Missing, disappeared files or directories?
or
Why can't I see all filenames with national characters?
or
Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?
    This means that your Operating System (OS) doesn't have the correct language specific settings (locale, LANG variable, etc) thus some filenames can't be converted to your language and won't be visible. The reason can be that the setting wasn't configured during installation, or not the correct value was set, or the set value doesn't exist on your system. The most common explanation is when the OS configures this setting in a too late stage during the boot process, after the NTFS volume was already mounted. This is why unmounting then mounting such volumes after boot often makes all filenames visible.

    Solution: The OS vendor should move the language specific configuration to an earlier phase to precede the mounts of the NTFS volumes in time.

    Workaround: ntfs-3g supports the 'locale' mount option which can be used to set the correct language value. You can see what locales you have on your system by using the following command:

    locale -a

    If you can't find the preferred setting then you must generate it, which is fairly distribution dependent. To do so, a package like glibc-i18ndata (openSUSE, Mandriva, ...) or locales (Debian, Ubuntu, ...) must be installed then enter the below command as root to generate for example the Brazilian locale:

    localedef -i pt_BR -f UTF-8 pt_BR.UTF-8

    Then you can use the "locale=pt_BR.UTF-8" option during mount.

    If some of your softwares are not UTF8 ready then they will not show correctly the UTF8 filenames. Please consult your distribution documentation about how to enable full UTF8 support.

    Status: Not ntfs-3g problem. Please ask your OS vendor to fix the boot time configuration problem.



I did the locale -a and I do have all I want which is en_US.utf8 and fr_FR.utf8

I tried to edit fstab with both of them but it won't work, so my guess is it's the boot process.

I am also experiencing some difficulties to unmount the mount again to see if it work that way....

If anyone has a solution for me I would gladly take it coz I am going crazy here.

---

### Post by chuckyp on 2007-09-14
What sort of problems are you having trying to umount the drive?  Have you tried sudo umount /<mountpoint>

---

