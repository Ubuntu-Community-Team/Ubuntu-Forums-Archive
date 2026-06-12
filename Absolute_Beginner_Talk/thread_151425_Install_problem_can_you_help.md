---
title: "Install problem can you help ?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by west1966 on 2006-03-27
I did look on the forum for this problem but drew a blank, well as a new member and a linux virgin I am now trying to install Ubuntu for the first time.
My problem is I seem to have froze at 33% of the Partitions formatting part of the install,and wanted to know How long does the process normaly take.and is it ment to freeze @ 33% while it does it`s job ?

The hd is a sygate 40 gig ( did contain fresh install of windows 98 no hardware errors - this was just to check all system + harware ran perfect - no probs on disk scan ). The system I use is an AMDk6Mk2 , 500Mhz , 120mg ram , 40 gigs sygate mater and 80 gig cap maxtor drive + pioneer dvd rom 

Its been @ 33% for over 2-3 hours , Do i need to chaneg any bios setting ? If anyone can help me.:-k 

is thee any way around having to partition and format with the DVD so I can just install the software ?or anyways I can check the driive

---

### Post by zxee on 2006-03-27
No, over two hours to format your drive doesn't seem normal. Exactly how are you formatting the drive? I haven't used the dvd install just cd. You can drop into a shell from the installer by doing <alt>+<ctrl><F1> and do sudo cfdisk /dev/hd*  *=the drive your wanting to partition. You can create a linux partition and swap, write changes to disk and then return to the installer. Hope that helps.

---

