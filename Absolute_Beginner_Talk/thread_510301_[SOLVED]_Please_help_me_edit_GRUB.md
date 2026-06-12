---
title: "[SOLVED] Please help me edit GRUB"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ron999 on 2007-07-26
Hi
I've got Ubuntu 7.04 and Windows 2000 installed independently on separate hard drives.
By default my PC boots to the Ubuntu drive.
But if I hit F8 during boot up I can instruct the PC to boot from the other drive to run Windows.
What I want to know is, how can I add Windows to Ubuntu's GRUB.
According to gParted, Ubuntu is installed at /dev/hda1 and Windows is installed at /dev/hdb1.
I've looked at the examples on the menu.lst but I can't get Windows to boot.
Please will someone advise me what extra lines to add to my menu.lst.
I've attached it.

---

### Post by Ek0nomik on 2007-07-26
> **ron999 said:**
> Hi
I've got Ubuntu 7.04 and Windows 2000 installed independently on separate hard drives.
By default my PC boots to the Ubuntu drive.
But if I hit F8 during boot up I can instruct the PC to boot from the other drive to run Windows.
What I want to know is, how can I add Windows to Ubuntu's GRUB.
According to gParted, Ubuntu is installed at /dev/hda1 and Windows is installed at /dev/hdb1.
I've looked at the examples on the menu.lst but I can't get Windows to boot.
Please will someone advise me what extra lines to add to my menu.lst.
I've attached it.

You didn't attach it.  :)

---

### Post by ron999 on 2007-07-26
sorry about that, I'll try again
:redface::redface:

---

### Post by Steve1961 on 2007-07-26
Something like this:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

---

### Post by ron999 on 2007-07-26
Trying

---

### Post by Ek0nomik on 2007-07-26
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

This will get you started.

---

### Post by ron999 on 2007-07-26
Thanks both of you.
Ekonomik, I will try your version using (hd1,0)
But please will you explain what **savedefault, makeactive and chainloader +1 ** are for. To educate me.

---

### Post by ron999 on 2007-07-26
No, I will use this one from your link

title           Windows 2000
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by ron999 on 2007-07-26
Great.
That works. But I'm not really sure why.
I've also got Zenwalk linux installed on a third drive which I have to boot using LILO on a floppy disk.
Is it possible to add Zenwalk to Ubuntu's GRUB too.
gParted says Zenwalk is installed at /dev/hdd1.
I've attached fdisk output this time.

---

### Post by Steve1961 on 2007-07-26
> **ron999 said:**
> Thanks both of you.
Ekonomik, I will try your version using (hd1,0)
But please will you explain what **savedefault, makeactive and chainloader +1 ** are for. To educate me.

Heres a link for the meaning of the commands:

[http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands)

---

### Post by ron999 on 2007-07-26
Well, I did a lot of Googling and found a solution. This is it:-

[B]title		Zenwalk
root		(hd2,0)
kernel	      /boot/vmlinuz root=/dev/sdc1 ro quiet splash
initrd 		/boot/initrd.splash
[/B]

This is good to know.
I think that in future, when I want to try another Linux distro, I will just carve out a 10GB partition for it. Then add some extra lines to GRUB. When I've finished with it I can delete the partition and delete the extra GRUB lines.
:guitar:8)

---

