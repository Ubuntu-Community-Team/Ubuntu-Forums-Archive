---
title: "Adding Hard Drives and the GRUB 17 Error"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-10-04
Hey all. Computer works great. Feisty dual-boot w/ XP, and no problems.. EXCEPT

I have 3 old drives I need to copy data from - 2 IDE, and 1 SCSI.

For now, I'd be satisfied with getting the IDE data, and that will probably be more simple.

The hard drives that i use every day in my computer are SATA, but I still have 2 channels of IDE on the MOBO - one to a CD burner, and one to a DVD burner. Back in my Windows days, I could have unplugged the CD/DVD drives, hooked up my 2 IDE hard drives, booted into Windows, and had access. Now that GRUB is installed, it won't get me past the 17 error. 

I have tried booting from CDs, such as the Ubuntu live CD, and others, but can't get to anyplace where the drive(s) is/are recognized. (I've only tried one at a time at this point.) 

Same deal with the SCSI drive (and it's adapter) but I'm not worried about that right now because it gets more complicated.

What can I do to get to these IDE drives? 


Thanks for any help

EDIT: I'd rather not change my GRUB install for each disk I need to hook up and copy from. Everything is working so great now, I really don't want to mess with that unless absolutely necessary.

---

### Post by Dr Small on 2007-10-04
If you have more SATA ports on your motherboard, you could get a PATA to SATA adapter so you can plug in these old IDE hard drives, which use a PATA connetor.

This is what I had to do to run my old PATA hard drives.

Dr Small

---

### Post by coldstatue on 2007-10-04
It's worth a shot. I've tried everything else short of buying an old win 98 comp from craigslist. I really just need them for 1 day, which is why I don't want to change anything in GRUB. If it comes to that, I'll get another comp and burn the files to CD. Thank you. I'll post back when I've tried it for an update.

---

### Post by coldstatue on 2007-10-04
Should that take care of the 17 error? I mean, i was plugging them right into the old PATA sockets. were you getting the 17 error Dr. Small?

---

### Post by logos34 on 2007-10-04
Try connecting just one IDE hard disk at a time.  Then on the ubuntu kernel selction on Grub menu screen hit 'e' key to edit.  Hit 'e' again on 'root' line and change from (hd0,x) to (hd**1**,x).  Hit enter and 'b' to boot...I'm thinking that maybe grub is seeing the IDE as if it were first in the Bios hard disk boot order.

anything?

---

### Post by coldstatue on 2007-10-04
@logos34

I get the GRUB error 17 before I reach the kernel selection menu, but I rebooted to look at it just to be sure. i use the UUID for root, so that isn't the issue, as far as I can tell. 

I am not informed at all about the boot process, and while I have read some, there is just to much that needs to be known for me to learn to the extent that I can figure this out. So any options, like yours, are greatly appreciated. I just want to try everything I can.

I know 17 is the 'bad geometry' error, but I am having a very hard time locating information in plain English about what causes it.  I can't be the only one who has been in this situation.

---

### Post by logos34 on 2007-10-04
> **coldstatue said:**
> I get the GRUB error 17 before I reach the kernel selection menu...
I know 17 is the 'bad geometry' error,

oh, I thought you were getting [this error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

---

### Post by Scruffynerf on 2007-10-04
If you are just retrieving data from old hard drives, why not do the simple thing and get an external case from somewhere, and run the other hard drives as essentially a big USB?

Finding one of those for a SCSI will be fun though, however the IDE's will be easy. You might be able to creatively have the IDE to SCSI adapter  in there as well.

---

### Post by coldstatue on 2007-10-04
scruffynerf - I've seen that name before, and i do believe I associated that handle with a solution in the past. Any brand/store/site recommendations?

That goes for the SCSI adapter too.. I am looking, but if you know any info off the top, I'd love to hear it.

---

### Post by coldstatue on 2007-10-05
I found what I need scruff. I'll be trying and posting back for future searches. It'll be a week or two. 

Thanks to everyone.

---

### Post by Scruffynerf on 2007-10-05
No worries.

I'm in Australia, so my store choices probably won't work for you!:)

Edit: Wow. I'm being noticed, and in a good way!

---

