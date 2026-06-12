---
title: "Grub error 17"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-07-08
I wanted to give some more room for windows from linux partition.

I made linux "/" partition smaller, and when I tryied to format that space to NTFS then I got error that there cant be over 4 primary partitions.

I already had

Win. part.
linux part.
boot part.
and linux swap part.

Now, I deleted boot partition to make .. extension(?) partition, and under extension partition I made linux boot and windows NTFS partition, so it looks like that:

Windows NTFS
Linux ext3
---extension---
extra space for windows NTFS
linux boot ext3
---end extension---
linux swap


now, when I take out gparted liveCD and try to restart, then I get GRUB error 17..

Help please?

---

### Post by Appolusionist on 2006-07-08
> **J-Gaming said:**
> I wanted to give some more room for windows from linux partition.

I made linux "/" partition smaller, and when I tryied to format that space to NTFS then I got error that there cant be over 4 primary partitions.

I already had

Win. part.
linux part.
boot part.
and linux swap part.

Now, I deleted boot partition to make .. extension(?) partition, and under extension partition I made linux boot and windows NTFS partition, so it looks like that:

Windows NTFS
Linux ext3
---extension---
extra space for windows NTFS
linux boot ext3
---end extension---
linux swap


now, when I take out gparted liveCD and try to restart, then I get GRUB error 17..

Help please?

Check out this post:
[http://www.ubuntuforums.org/showpost.php?p=765889&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=765889&postcount=3")

---

### Post by catlett on 2006-07-08
If you erased boot you erased the bootloader. You don't have a bootloader any more.
When you changed the structure and moved boot, did you reinstall Ubuntu? or did you just move them?

---

### Post by J-Gaming on 2006-07-10
> **Appolusionist said:**
> Check out this post:
[http://www.ubuntuforums.org/showpost.php?p=765889&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=765889&postcount=3")
When I set mountpoints and press "install" at end I get "installer crashed" message, and Im still getting error 17


> **catlett said:**
> If you erased boot you erased the bootloader. You don't have a bootloader any more.
When you changed the structure and moved boot, did you reinstall Ubuntu? or did you just move them?

I erased "/boot" partition, and thats what I hoped - that I delete /boot partition, I will lose grub for a second, remake boot partition and then when I boot I will go directly to win/ubuntu, and then re-install grub from there.

unfortunately grub is still there and wont let me to start any OS, so Im stuck.. help still needed

---

### Post by J-Gaming on 2006-07-10
Please help, I need to access my files :(

---

### Post by Crosbie on 2006-07-10
I'm no expert, but I think /boot is all the files you need to load linux/Ubuntu; it's not the same as the bootsector or MBR, where Grub or NTLDR live.

If you just 'need to access your files' yu might try booting into your LiveCD first... and back up any files you really need.

---

### Post by catlett on 2006-07-10
[http://gag.sourceforge.net/](http://gag.sourceforge.net/) This is a link to GAG (it's the initials for "Graphical Boot Manager" in Spanish.)
This should take care of your issue. GAG will install on to your mbr and boot you to any OSs you have installed. Since you have reinstalled Ubuntu, gag should boot you to it.
It may boot you to grub if grub got installed on Ubuntu's partition but it isn't a problem. You will just have to select Ubuntu from the menu like before.
If you still have windows, it can boot you to that as well.
Just go to that site and download gag. It is very small. Then you can load it on a floppy or burn the gag iso to a cd. Either way you boot to it and gag will run

---

