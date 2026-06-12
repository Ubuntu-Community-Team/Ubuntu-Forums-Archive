---
title: "Need some help in making USB stick bootable"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by Skeeve42 on 2008-05-01
Hi!

I'm working the third night now to get a LiveCD onto a USB stick.

I come up to the "boot:" prompt and when I enter "live-nosplash-powerpc video=ofonly" I end up with a message:
> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I'm stuck here. What can I do now? What do I have to change in my process of getting a bootable Live-USB-stick?

This is what I did so far to make it boot:

[LIST]
[*]Booted LiveCD
[*]Partitioned the stick with mac-fdisk as described [here]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-usb-files.html").
[*]Copied yaboot and made the attrib-changes from /cdrom as Cescribed on the page linked above.
[*]Mounted the Stick to /mnt
[*]Copied the cdrom content using this command line
(cd /cdrom ; tar cBpf - .) | (cd /mnt ; tar xvBpf -)
The only error message was about a not permitted link of '.' to 'ubuntu' (hfs doesn't allow symlins?)
[*]Removed /install/yaboot
[*]Copied everything from /mnt/install to /mnt
[*]Removed /mnt/install
[*]Changes made to /mnt/yaboot.conf 
[LIST]
[*]strings '/cdrom/' removed
[*]changed '/casper/powerpc/' to'/ppc-'
[*]changed '/casper/powerpc64/' to'/p64-'
[/LIST]
[*]copied /casper/powerpc/vmlinux to /ppc-vmlinux
[*]copied /casper/powerpc/initrd.gz to /ppc-initrd.gz
[*]copied /casper/powerpc64/vmlinux to /p64-vmlinux
[*]copied /casper/powerpc64/initrd.gz to /p64-initrd.gz
[*]removed directories /caper/powerpc*
[/LIST]
I think, that's it.

Did I forget something important?

---

### Post by avtolle on 2008-05-01
Which version are you trying to install (7.1, 8.04)?

---

### Post by avtolle on 2008-05-01
I've never tried this; looking at the linked article, I don't see anything obvious that you didn't do.

The reason for my question about which distro release is that under 7.10, IDE drives were not recognized. Thus, the fix, to continue booting, was, at the Busybox prompt such as you got, to type in ```
(prompt) [COLOR=Blue]modprobe ide-core
[/COLOR] (prompt) [COLOR=RoyalBlue]exit[/COLOR]
```which allowed booting to continue, with what you enter designated by the [COLOR=RoyalBlue]colored [/COLOR]text.
Try this, if using 7.10, and see if booting continues.

---

### Post by Skeeve42 on 2008-05-02
It's 8.04 I've tried. I will try what you suggested.

---

### Post by Skeeve42 on 2008-05-02
doesn't help. Doesn't even work: > FATAL: module ide_core not found.Note: I typed ide-core but the message was about ide_core.

---

### Post by Skeeve42 on 2008-05-02
Something more!

When I enter "exit" I get:
> 
cp: unable to open `/root/var/log´: No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

And then the BusyBox again

---

### Post by avtolle on 2008-05-02
I'm wondering if your copying of the files on the .iso using tar was unwise. Have you tried a straight copy (sudo cp) command to copy the .iso to the usb stick? Your latest post got me to thinking (dangerous at best, doubly so on Friday afternoons) that use of tar might have fouled something up. My two cents.

---

### Post by Skeeve42 on 2008-05-02
I didn't copy a .iso but all the from the CDROM. I'll try to copy the .iso later. Yes. I know the page I linked said to copy an iso image. Other source made me think I can copy the files from the CD.

I'll keep you updated.

---

### Post by avtolle on 2008-05-02
FWIW, I've copied an iso from one Cube to another over the LAN just to see if it works. Checked the md5sum, etc., all went well, and burned the copied iso to disk and was able to install that way. So, a long way of saying that based upon that, a direct copy of the iso to the thumb drive should have the same result, and hopefully get you going.

---

### Post by Skeeve42 on 2008-05-02
GOT IT!

I just booted from a LIVE-USB!

Instructions will follow. It's darn easy!

---

### Post by avtolle on 2008-05-03
Great to hear/read. When you have a chance, let us know what to do, so we can try it out as well.

---

### Post by Skeeve42 on 2008-05-03
> **avtolle said:**
> Great to hear/read. When you have a chance, let us know what to do, so we can try it out as well.
Sure! As I promised. But I promised it in another forum first ;-) But [here you have the english translation]("http://ubuntuforums.org/showthread.php?p=4871254#post4871254").

---

