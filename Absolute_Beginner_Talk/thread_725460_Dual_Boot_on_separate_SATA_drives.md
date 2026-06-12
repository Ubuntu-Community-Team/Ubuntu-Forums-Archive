---
title: "Dual Boot on separate SATA drives"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by tfewald on 2008-03-15
I have no IDE drives on my system. I have two SATA drives with Windows XP Pro on one and data files on the other. I installed a third SATA drive specifically to use for Ubuntu. However, when I install to it, and then remove the CD as instructed, I go directly to Windows on the reboot. I've tried changing the boot order in the BIOS so the Ubuntu drive goes first, but then the system hangs at the "Boot from CD?" prompt.

I would appreciate help with this. Thank you.

Tom Ewald
Detroit area
[email]tewald@wowway.com[/email]

---

### Post by Duck2006 on 2008-03-15
This may help with install grub to the boot drive.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by drubin on 2008-03-15
This looks like the boot order in your bios is set to boot off of the windows drive first.

Try changing it to Ubuntu drive, it should load up grub automatically. As it is not even looking that the ubuntu drive- because it tries to boot on the windows drive, (it then boots into windows).

On the ubuntu drive. It loads up grub that gives you the options..

Hope this helps. (I have this set up running currently works very well).

---

### Post by drubin on 2008-03-15
I just re-read, Not sure what this issue is, please ignore my post.

---

### Post by tfewald on 2008-03-16
Duck2006,

Thanks for the URL, but I can't even get to the Ubuntu drive. I can boot off the CD, of course, and then tell it to install onto the new SATA drive, but when I reboot I can't get to it.

---

### Post by bsharp on 2008-03-16
rubinboy is somewhat correct, it sounds like your bios is set to boot off of the windows drive first.  What you can do is load a livecd and
```
(assuming your ubuntu drive is sda3) sudo mkdir/mnt/sda3
sudo mount /dev/sda3 /mnt/sda3
(assuming your windows drive is sda1)sudo mkdir /mnt/sda1 
sudo mount /dev/sda1 /mnt/sda1
sudo chroot /mnt/sda1
grub-install --root=/dev/sda3 /dev/sda1
```

which should install GRUB to your windows drive's MBR.

---

### Post by gorf 99 on 2008-03-16
Try putting the Ubuntu drive 1st and the Windows drive 2nd.  Your mother wants to boot from the 1st drive and Grub will install on your first drive.  When you defrag the Windows drive this will move Grub and you get an error.  It cann't find Grub.

 If you are using the whole drive for Ubuntu use the ext3 file format.  You can still use the ntfs file from Windows using the NTFS Config tool.

Hope this helps

---

