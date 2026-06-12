---
title: "Grub2 menu not showing. Can't select OS :("
date: 2011-06-19
forum: Any Other OS
---

### Post by varunrajan on 2011-06-19
I recently installed Linux Mint 9 (corresponding to Lucid Lynx) on my laptop using an usb stick. And I don't know how but I somehow managed to get grub installed onto the usb, while the OS onto the hard-disk. So now I can't boot into my machine without using the usb drive.

I tried the standard way of reinstalling grub2. The procedure worked without any errors but didn't solve the problem either.

Is there any way that I can resolve this issue without reinstalling the OS? I had put in far too much time into configuring Mint and would very much like to not do a reinstall.

Thanks in advance

---

### Post by cbowman57 on 2011-06-19
Did you try using synaptic to completely remove grub, then reinstall it?

---

### Post by Perfect Storm on 2011-06-19
Moved to Other OS/Distro Talk.

---

### Post by varunrajan on 2011-06-19
Tried reinstalling grub completely to no avail. Also tried using boot-repair options to restore grub.

---

### Post by cbowman57 on 2011-06-19
That is not what I asked.  Did you **completely remove **grub & reinstall it?

---

### Post by varunrajan on 2011-06-19
Yes.

---

### Post by cbowman57 on 2011-06-19
:) Ok, open your terminal & try this **sudo apt-get purge grub-pc **then **sudo grub-install /dev/sda **(assuming you want it on your first hard drive)

Make sure you don't reboot after purging, you won't have a boot loader installed, which you probably already know.  You may have to reinstall it before you can use the grub-install command. 

Here's an article on an application and/or liveCD that might make it easy if you want to use it, or the command line method won't work.

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html#more](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html#more)

---

### Post by varunrajan on 2011-06-19
The command "sudo grub-install /dev/sda" is returning error that grub-install.real is not found. Shouldn't I reinstall grub-pc before using that command?

I have already tried boot-repair, but from my local installation rather than live cd; will do that now.

---

### Post by cbowman57 on 2011-06-19
> **varunrajan said:**
> The command "sudo grub-install /dev/sda" is returning error that grub-install.real is not found. Shouldn't I reinstall grub-pc before using that command?

I have already tried boot-repair, but from my local installation rather than live cd; will do that now.

I'm guessing that you will have to reinstall it before using grub-install.  There is also the grub-install --force /dev/sdx method but if it were me I'd like it to install cleanly.

---

### Post by varunrajan on 2011-06-19
Purged and reinstalled grub, and executed the grub-install command. Also tried running boot-repair from liveusb but still no luck.

---

### Post by cbowman57 on 2011-06-19
:(  I'm out of ideas, seems that should have worked.  Maybe someone will pop in with the solution.

---

### Post by varunrajan on 2011-06-19
> **cbowman57 said:**
> :(  I'm out of ideas, seems that should have worked.  Maybe someone will pop in with the solution.

:( Thanks for your time.

---

### Post by cbowman57 on 2011-06-19
Not a solution really but you could always carve out a 8-10Gb partition and install another linux to it just so you wouldn't have to rely on that usb drive.

If this was a fresh install I guess you could re-install, or use Remastersys to create a backup and re-install with that, that would retain all your settings & changes, but give you the opportunity to install grub to the desired device.

---

### Post by BrokenKingpin on 2011-06-21
I had the same thing happen to me installing Ubuntu from the mini.iso... the system installed fine, but it installed grub to the USB key. I tried for about a day to resolve the issue, but never could get it booting, just an endless black screen.

I eventually gave up and installed Xubuntu. I am pretty sure there is a bug in the installer where if the USB key is recognized as the first disk (over the HDD), grub will get installed to that instead of the drive the OS is being installed on. Hopefully someone can help you with this issue.

---

