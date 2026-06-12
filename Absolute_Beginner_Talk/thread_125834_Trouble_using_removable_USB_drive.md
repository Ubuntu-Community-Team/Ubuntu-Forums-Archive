---
title: "Trouble using removable USB drive"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by NewGroove on 2006-02-04
Hi, hoping someone can shed some light on my problem... right after I installed Ubuntu and rebooted, I inserted a Sandisk Cruzer Mini USB drive and an icon appeared on the desktop. Wonderful!

Ever since then however, when I insert it nothing happens. I can mount the drive to something such as /mnt/removable using this command:

[FONT="Courier New"][SIZE="3"]sudo mount /dev/hda2 /mnt/removable -t vfat -o iocharset=utf8,umask=000[/SIZE][/FONT]

It was much more convenient the other way however. Now, if I click on Places > Computer, I can see the drive sitting there next to the CDRom drives and filesystem. Clicking on the USB drive icon gives me the message "Unable to mount the selected volume. Error: given UDI is not a mountable volume." Right-clicking on the drive and then the permissions tab tells me that it's owned by root, but neither the owner, group or others can write/execute anything with it. It says at the bottom of the permissions tab that I'm not the owner, so I can't change these permissions.

Can anyone help me know what's wrong? Does this have to do with why the drive won't appear on the Desktop anymore? How do I change permissions on something like this. Thanks so much for your awesome help!

Mike

---

