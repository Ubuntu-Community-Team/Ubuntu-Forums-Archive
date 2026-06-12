---
title: "Ubuntu dissappeared and Windows no longer works"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by Justin Holt on 2008-09-03
So I decided that I would like to install Ubuntu on my 4,1 Macbook Pro (Penryn). I'm currently using rEFIt to boot all 3 partitions. I have just recently come upon a few problems.  

If I select Windows, it used to force me to go through GRUB but now it just goes straight to Windows and says that hal.dll is missing? Windows hasn't worked since I installed Ubuntu, what would cause that?

All of a sudden, I inserted my Windows install cd into my Macbook Pro to try to repair windows, and when I rebooted, the Ubuntu icon disappeared from the rEFIt loader? Is there anyway to get all of that back? Do I have to reinstall GRUB?

Thanks for any help!
Justin

---

### Post by cyberdork33 on 2008-09-03
> **Justin Holt said:**
> If I select Windows, it used to force me to go through GRUB but now it just goes straight to Windows and says that hal.dll is missing? Windows hasn't worked since I installed Ubuntu, what would cause that? Likely to install Ubuntu you had to adjust the partitions on your disk. Windows tends to throw a fit when you do that. Easiest thing is likely to reinstall windows.

> **Justin Holt said:**
> All of a sudden, I inserted my Windows install cd into my Macbook Pro to try to repair windows, and when I rebooted, the Ubuntu icon disappeared from the rEFIt loader? Is there anyway to get all of that back? Do I have to reinstall GRUB?It sounds like it tried to reinstall the windows bootloader to the MBR (where GRUB is by default), so you need to reinstall grub to the Ubuntu partition. See this thread:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by Justin Holt on 2008-09-03
Thanks for your response. So far, I have wiped out the ntfs, ext3, and swap partition, and then created a single large ntfs partition for windows to use to install on. To my dismay, when I boot up the Windows install disc, it only shows one 200 gig disk. 

One friend suggested that I go and use fdisk on the Ubuntu live cd and find a "repair" option to fix it.

Any suggestions so it sees my hfs+ partition and doesn't wipe out the whole laptop?

Justin

---

### Post by cyberdork33 on 2008-09-03
> **Justin Holt said:**
> Any suggestions so it sees my hfs+ partition and doesn't wipe out the whole laptop?
Yea, don't use fdisk :) (It can only edit the MBR partition table and not the GPT that the Mac has.)

Is OS X bootable still? Can you use Disk Utility? If you are going to just reinstall everything, then you should create your partitions all upfront, then install the OS to the correct place. There are several guides to "triple-boot" here in the forum.

---

### Post by Justin Holt on 2008-09-03
OS X is fully functioning, I'm typing up notes I took in class on Tuesday right now with Pages... 
My main issue that when I go to put in the Windows cd (after i've deleted all those partitions) It still sees the disc as one whole 200 gig partition.  

What is it that I have to do to fix that? Is that in a guide?

Thank you so so much!

Justin

---

### Post by Justin Holt on 2008-09-04
yep, I can be classified as an idiot. After your ssggestion about not using fdisk because of mgr and gpt partition tables, I decided to try and sync mbr on rEFIt. I now have the instal disc seeing all partitions an hopefully it will be smooh sailing from here. And again, thanks a lot. 

Justin

---

### Post by cyberdork33 on 2008-09-04
> **Justin Holt said:**
> yep, I can be classified as an idiot. After your ssggestion about not using fdisk because of mgr and gpt partition tables, I decided to try and sync mbr on rEFIt. I now have the instal disc seeing all partitions an hopefully it will be smooh sailing from here. And again, thanks a lot. 

JustinYes windows can only read the MBR table, so if it had not been updated, it would look like nothing had changed.

---

