---
title: "Backtrack 5, Persistence, Grub"
date: 2013-06-12
forum: Any Other OS
---

### Post by CrazZziK on 2013-06-12
Hello everyone,

This is not your regular DUAL BOOT thread.

I've got a netbook that has Win 7 as main system and only 32 gigs of NAND storage. This is why keeping linux on different media is a better solution for me. I've also installed Backtrack 5 r2 on an 8 gig class 10 sd card, works fairly well.

My booting process looks like this:
POST -> GRUB menu on SD card -> Persistence mode Backtrack.

What I need (I would like Win 7 to load by default):
POST -> GRUB menu on SD card -> Windows 7 (boot from first HDD)

Technically, all I need to do is to change GRUB_DEFAULT to X (7 in my case) and run "sudo update-grub" but I get an error message:

```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

SD card created with unetbootin.

```
sudo mount
aufs on / type aufs (rw)
```

Looking for any advice

---

### Post by sandyd on 2013-06-13
moved to other os support

---

### Post by BubuXP on 2013-06-13
some advice:
- Kali Linux has replaced BackTrack
- try posting the whole config file, or at least the windows menuentry section, and possibly more details
- isn't better removing the sd card to boot directly in windows? The card probably have no use under windows and being not connected can make it live longer perhaps.
- maybe it's unetbootin fault. I remember that some years ago a writable device with ubuntu live on it (using ubuntu tool and not unetbootin) can save user data. Being backtrack based on ubuntu, have it the same behavior?

---

### Post by CrazZziK on 2013-06-13
> **BubuXP said:**
> some advice:
- Kali Linux has replaced BackTrack
Will check it out.
> - try posting the whole config file, or at least the windows menuentry section, and possibly more details
```
root@bt:/# cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 
GRUB_DEFAULT=7
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text splash vga=791"
GRUB_CMDLINE_LINUX=""
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"
 
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
> - isn't better removing the sd card to boot directly in windows? The card probably have no use under windows and being not connected can make it live longer perhaps.
Not in my case.
> - maybe it's unetbootin fault. I remember that some years ago a writable device with ubuntu live on it (using ubuntu tool and not unetbootin) can save user data. Being backtrack based on ubuntu, have it the same behavior?
I've tried LILI. That one is even worse because it does not handle rebooting at all.

---

