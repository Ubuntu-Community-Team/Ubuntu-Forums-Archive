---
title: "UBUNTU STUDIO won't boot"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by cousin-it on 2007-05-23
I am fairly new to Linux so I may just be overlooking something. But here goes. I just built a machine with a Biostar P4M80-M4 MB with a Celeron 2.6G CPU, 512M RAM, 80G IDE HDD (although this board has SATA), CDRW, and DVD Rom. 
At first it wouldn't finish the install of Ubuntu Studio. It would get to 85% and lock up. Then I turned off ACPI on the motherboard. It then finished the install but now it won't boot. It gives me "DISK BOOT FAILURE" message. The motherboard is detecting the HDD on POST. 
I can load Windows 2003 Server with no problem. 
Can anybody tell me what the problem might be here, and how to fix it?

Thanks

---

### Post by MetalMusicAddict on 2007-05-23
> **cousin-it said:**
> I am fairly new to Linux so I may just be overlooking something. But here goes. I just built a machine with a Biostar P4M80-M4 MB with a Celeron 2.6G CPU, 512M RAM, 80G IDE HDD (although this board has SATA), CDRW, and DVD Rom. 
At first it wouldn't finish the install of Ubuntu Studio. It would get to 85% and lock up. Then I turned off ACPI on the motherboard. It then finished the install but now it won't boot. It gives me "DISK BOOT FAILURE" message. The motherboard is detecting the HDD on POST. 
I can load Windows 2003 Server with no problem. 
Can anybody tell me what the problem might be here, and how to fix it?

Thanks

It didn't hang at 85%. Its actually going through alot of packages at that point. You need to let it finish. You got the error because you killed the install. Start the install again.

---

### Post by cousin-it on 2007-05-24
I started the install over after I turned off ACPI, then the install finished. After the install finished, it still won't boot. Any ideas on that?

---

### Post by Terl on 2007-05-24
Are there error messages?  What is it doing?

---

### Post by cousin-it on 2007-05-24
When it reboots, it goes through POST then says "Boot From CD:" the hesitates, then says "Disk Boot Failure, Insert System Disk And Press Enter"

I just reloaded Ubuntu Studio on this machine so it is a fresh copy. It just won't boot into it.

---

### Post by confused57 on 2007-05-24
Herman has a couple of links for this error on his site:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_hard_disk_error](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_hard_disk_error)

looks like it'll take some reading, but hopefully you can find something helpful..

---

### Post by cousin-it on 2007-05-24
I finally got it figured out. Thanks for all the help. It was a jumper setting on my HDD. It was set to Master, and I changed it to Cable Select and everything started working like a top.
Thanks "confused57", I got the idea from one of those posts.

---

### Post by confused57 on 2007-05-24
> **cousin-it said:**
> I finally got it figured out. Thanks for all the help. It was a jumper setting on my HDD. It was set to Master, and I changed it to Cable Select and everything started working like a top.
Thanks "confused57", I got the idea from one of those posts.

Glad you were able to get it to work...thanks for the update.  I'll have to remember your solution, if I see someone else with the same problem.

---

