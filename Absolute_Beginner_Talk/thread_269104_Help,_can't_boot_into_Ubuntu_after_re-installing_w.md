---
title: "Help, can't boot into Ubuntu after re-installing windows..."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by BuRn_sLuG on 2006-10-01
Hey guys,

Well I've got Ubuntu all set up and installed fine on one partition, with Windows on the other, so it looks like this...

Hard Drive 1;

Partition 1: Windows (Primary) **NTFS**
*Partition 2: Extended (Primary)*
 - Partition 3: Ubuntu (Logical) **ext3**
 - Partition 4: Swap (Logical) **linux swap**

Hard Drive 2;

Partition 1; Ubuntu Media (Primary) **ext3**

After moving to Ubuntu from Windows XP yesterday, I now use Ubuntu as my primary OS, now with Windows XP for gaming. Because of this, I decided to reformat and re-install the Windows Partition (Partition 1, Disk 1, NTFS), removing the old files/folders, and suceeded in doing so.

HOWEVER, when my computer boots now, it no longer gives me the option of booting into Ubuntu, and goes straight into Windows. I think this has something to do with the GRUB (some boot thing?) becoming corrupted/replaced/deleted (could someone please explain this to me further). 

Would I be able to boot up off my Ubuntu live CD and repair the boot files from there? 

Help with this would be much appreciated, as I miss Ubuntu, and would rather not stay in Windows permanently, and REALLY don't want to reformat Ubuntu (as I have got everything set up now).

Cheers once again guys.

Brendan

---

### Post by bollix47 on 2006-10-01
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by petit.padavoine on 2006-10-01
What you're missing is the GRUB Bootloader, Windows writes over it... You can download it and then reinstall it using a Live CD. Here is a [guide]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/") to doing this.

---

### Post by SirShaggy on 2006-10-01
What I did to fix mine was.......
Put the live CD into my computer and rebooted.
I let Ubuntu fully load to the desktop on the live cd.
Then, I opened a terminal. I typed sudo grub then enter.
I typed find /boot/grub/stage1 and then hit enter.
It returned a location to me of (hd0,5) yours will tell you where your stage1 is. Keep it for the next command.
then I typed root (hd0,5) enter. (Type you correct info here)
then I typed setup (hd0) enter
then I typed quit, closed the terminal and rebooted. 
Pop out the cd when you are asked to, then hit enter.
You should see the PC reboot and get the grub screen with Ubuntu and Windows again.
Hope that helps,
SirShaggy

---

### Post by BuRn_sLuG on 2006-10-01
Cheers, SirShagy, it worked.

You guys are great, thanks as per usual. :mrgreen:

---

### Post by SirShaggy on 2006-10-01
No problem. I only knew how to fix it because I too broke it and somebody helped me. Enjoy!
SirShaggy

---

