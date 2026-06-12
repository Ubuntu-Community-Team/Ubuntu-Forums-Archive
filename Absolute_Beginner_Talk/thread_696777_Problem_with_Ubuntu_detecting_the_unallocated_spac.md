---
title: "Problem with Ubuntu detecting the unallocated space"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Starlance93@hotmail.com on 2008-02-14
Hi. I'm new to the Ubuntu community and I'm trying to install Gutsy Gibbon with my already existing Vista installation. I have freed up about 10gb (by shrinking my other drives with the vista disc manager) for my Ubuntu install. I booted up the Ubuntu live CD and clicked on the install icon on the desktop and went through the first few steps. When it got to the part asking where I'd like to install Ubuntu it only showed Manual and Guided - Use whole disc. I believe that there is supposed to be something saying "Guided - Use largest continuos space". 
I need to keep the windows installation. 
Is there something that I have done wrong, or do I need another version of Ubuntu to do this? If you know anything I'd really appreciate your help.

My computer (If it matters):
Asus F5R (laptop)
120gb HDD (50 - Vista OS, 50 - Logical Drive, ~13 Unallocated)
1024mb RAM
Intel Pentium dual-core

---

### Post by tangibleorange on 2008-02-14
OK. I think I was probably following the same [guide]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") as you :P. I tried "Use continuous free space", and it erased my whole disk with no operating system at all! I recommend you use the "manual" option. You've got that, right?

Click it and it should show the free 10GB. Simply divide that into two partitions. One with file system "swap" and one with file system "ext3". The ext3 one will be where the install will go. I recommend about 1GB for the swap and you can use the rest for the main partition. I think there are instructions similar to this at the bottom of the "Manual" window...

---

### Post by Starlance93@hotmail.com on 2008-02-14
Hmm... I did try out the "manual" part but it still only showed my hard drive and not my partitions. Something like this was shown:
Dev/(something else here)


I clicked on this and it still said that it would use the entire device... Do you maybe need more info?

---

### Post by tangibleorange on 2008-02-14
Could you maybe post a screen shot of what happens when you click the manual part?

---

### Post by Starlance93@hotmail.com on 2008-02-14
I can't get that at the moment... :-( I'm a school and it would take too long. Thank you for your help though.
On the Ubuntu website there was an alternate download. Is that just a mirror or would it give me some kind of a different version?
It was a text installer. Is there any possibility that this one would work better than the live CD edition?

---

### Post by tangibleorange on 2008-02-14
I think you're referring to the alternate CD. It is basically a text-based installer (you can't run Ubuntu from it), for systems that have trouble with the graphics in the Live CD. It can also be useful for complex partitioning, but I have never used it. Unless you know what you're doing, I think it's probably better to stick with the Live CD. The alternate one still installs the same system, just using a text installer.

---

### Post by Starlance93@hotmail.com on 2008-02-14
OK thank you for your help.
I think that I'll just keep tinkering and try to figure it out myself. :)

---

### Post by tangibleorange on 2008-02-14
OK cool. If you want some more help just post a screenshot of the manual partitioning screen. :)

---

