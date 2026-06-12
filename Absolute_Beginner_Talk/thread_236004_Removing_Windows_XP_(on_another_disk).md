---
title: "Removing Windows XP (on another disk)"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-08-14
I had a dual boot system with Windows XP (on sda) and Ubuntu (on sdb). To get rid off Windows XP and not having trouble with the MBR which was on the Windows XP disk I thought of installing (another) Ubuntu over the Windows XP disk (sda, also made it ext3) using the live-cd. After that I copied everything from the 'old' ubuntu (on sdb) to the new installation on sda (cp * -R -f)
I manually edited the fstab and menus.lst to point the right disk  (these were overridden during the copy process).
 
After a reboot I was glad to see the logon screen appear correctly but after a login attempt I get these messages:

"User's $HOME /.dmrc file is being ignored. This prevents the default session and language from being saved. Fle should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

"GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator."

Can I fix this?

---

### Post by rdd on 2006-08-14
OK, you have 2 choices. I would recommend the first one. 

1. Install grub on the second disk and swap the disks.  

check out this howto, for installing it: [https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

Afterwards change all the necessary stuff, fstab, etc.

2. Do the copying again with

```
cp -ax
```

a is the archive option. It preserves permissions. These seem to have been mixed up in your previous attempt. 

Regards

rdd

---

### Post by lorre on 2006-08-14
Thnx for the quick reply! I'll give it a go tonight.

---

### Post by lorre on 2006-08-14
I gave the cp (this time with -ax) another try and all is well! Thnx again.

---

