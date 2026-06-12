---
title: "Dual Booting and Wireless"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Forgery on 2007-02-28
Hey there completly new here and, well, needing a few questions answered. I am considering dual booting XP and Ubuntu onto my notebook, which has a 60GB hard drive. 

What would you recommend the partitions to be? I don't really want a /share partition because as far as I can see, things I have in windows will be there for windows and linux with linux.

Secondly my notebook comes with a Broadcom Wireless PCI adapter. Will this work if I was to install Linux? From what I've read it suggests it will not be I'm really not entirly sure.

Thank you

Forg

---

### Post by overdrank on 2007-02-28
> **Forgery said:**
> Hey there completly new here and, well, needing a few questions answered. I am considering dual booting XP and Ubuntu onto my notebook, which has a 60GB hard drive. 

What would you recommend the partitions to be? I don't really want a /share partition because as far as I can see, things I have in windows will be there for windows and linux with linux.

Secondly my notebook comes with a Broadcom Wireless PCI adapter. Will this work if I was to install Linux? From what I've read it suggests it will not be I'm really not entirly sure.

Thank you

Forg
Well for me I always just split the size of the drive for the partitions. That is if I keep windows for dual boot.
As for your wireless I would refer to this link
[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Wireless+PCI+adapter](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Wireless+PCI+adapter)

---

### Post by Forgery on 2007-02-28
Split the size of the drive? By that do you mean equally? e.g 30gb for windows and30gb for Linux? Or does Linux not need as much? e.g would 15gb for Linux be more than enough.

Thank you for the link

Forg

---

### Post by mikewhatever on 2007-02-28
15 BG is a good size for Ubuntu root. Don't forget to make a swap partition of roughly 500 MB.
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Broadcom adapter is well known to be troublesome and there are lots of howtos to make it work. Some report it does, others it does not. You can't know in advance.

---

### Post by bodycoach2 on 2007-02-28
My desktop is dual boot, and my I did it with my laptop for awhile too. It's not too hard.

Install Windows XP first. Get all your updates done, and install all the software you want. I highly recommend using [Open Soure Windows applications]("http://www.opensourcewindows.org/"). Get all the files you want on your windows side (personal, music, etc). If you want your Linux side to be able to read Windows, format in FAT32. I didn't bother, and kept the Windows partition in NTFS. Once you've got everything you need, scandisk and defrag.

Use the Ubuntu LiveCD if you want the graphical installer to help you. Boot the comp with the LiveCD in, select install, and follow the prompts. At some point it will suggest drives and formatting. There should be a selection to divide the drive, and it will suggest to use 1/2 the drive for Ubuntu. Install.

When the computer reboots, you're boot menu (GRUB) will prompt you for which system to boot to. Page down if you want to boot to Windows.

Personally, booting to windows feels criminal. But, I have to for school.

---

