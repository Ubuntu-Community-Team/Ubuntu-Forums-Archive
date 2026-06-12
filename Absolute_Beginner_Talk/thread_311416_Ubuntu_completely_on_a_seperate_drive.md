---
title: "Ubuntu completely on a seperate drive"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Stephen94 on 2006-12-02
Hi

I've only ever played around with live CDs before and I think it's time for my first install of Linux.

I know these are probably really basic questions. While I'm very confident in Windows, anything down at the boot/bios level is completely alien to me.

Because I'm lacking confidence in this respect, I'd like to put put Ubuntu completely on a separate drive from windows - without Linux modifying my Windows drive in any way. So Windows would be on the C drive and Ubuntu on the D.

Is that possible? From what I can gather the usual process is to have the PC ask you at boot which OS to use. But obviously that won't work if C is unmodified?

---

### Post by Shatrat on 2006-12-02
> But obviously that won't work if C is unmodified?
It will work if the drive Ubuntu and Grub are on is first in the BIOS boot order.
You could just unplug the windows drive completely and install Ubuntu.  It's not necessary but it will keep you from getting nervous :)
Then you install ubuntu normally.  Then you plug the windows drive back in but make sure you go into the bios and set it to boot first from the drive with Ubuntu.  Then you have to add windows to Grub since the drive was unplugged when grub was set up during the install, but thats not too hard (although I cant remember how to do it exactly because I havent needed to in years).

Ask of google and ye shall recieve, [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu)

---

### Post by 56phil on 2006-12-02
You're right. The installer will need to alter the MBR (master boot record) so it will load grub which gives you the choice of windows or Ubuntu. This is easily done at install time. Be very careful in the formatting phase. Make sure you don't format the wrong drive.

Welcome to Ubuntu.

---

### Post by confused57 on 2006-12-02
This may be an option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by confused57 on 2006-12-02
Deleted-duplicate post

---

### Post by Stephen94 on 2006-12-02
Great Sounds a lot easier than I thought :)

So the sequence would be the following?
[LIST]
[*]Make sure it's booting from the Ubuntu-to-be drive
[*]Remove Windows drive (not necessary but I'd feel safer)
[*]Install Ubuntu - and one of the install options will be to let it take the entire drive (?)
[*]Put the Windows drive back in
[*]Run Ubuntu and modify the grub using [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu") (not  100% sure about how to modify the Grub but I'm sure I'll figure that out)

[/LIST]

am I getting it right?

---

### Post by 56phil on 2006-12-02
Just make sure you can boot off of the slave drive. Could you please tell us more about your system? What are your boot drive opitions in the BIOS?

---

### Post by Chinkostu on 2006-12-02
you don't have to mess around with unplugging. if you have a physical second drive thats empty, you can select it to install to that. 

the installer will give you the options to manually edit the partitions on the second drive or to let it do it by itself. generally with IDA, the C is hda1 and D is hdb1, without any partitioning.

Grub is fairly easy to modify via the terminal. just run ```
gksudo gedit boot/grub/menu.lst
``` and put it in. you can also set the windows drive to be the default boot device if you so wish.

---

