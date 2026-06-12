---
title: "3 operating systems"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by jerden on 2008-04-13
I got my new laptop hp dv2000 series with vista 64bit operating system and imediatley installed ubuntu 7.10 from there i just got fed up with vista so I wanted to install windows xp so i tried but it wouldnt allow for more than 4 primary partitions. 

So I used Gparted and editied the hard drive and made a xp partition and an extended linux partition. I installed xp then but it wouldnt load the boot menu to access xp so I thought ubuntu would do it for me so I installed ubuntu.

From here it gave me only the vista loader nd itself but the vista loader had the hal.dll file missing so it wouldnt load so I had to do a a restore i did vista know works fine but ubuntu and xp are still there with no access to them. I know ubuntu is the best option what can be done anything?

---

### Post by Oldsoldier2003 on 2008-04-13
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817) is a great tutorial on multibooting

---

### Post by Squish on 2008-04-13
Its best to install ubuntu last.
From my experience, as I am trying to do a bit more of a complicated multiboot at the moment, it is best to partition first using gparted, making 2 dummy fat32 partitions for vista and xp. then go forth and install xp first, and it will detect the fat32, and will let you partition it as ntfs, then complete the install. Then go forth with vista on the other one, and finally set up ubuntu, and the grub will take care of it. 
Note that you can install ubuntu in a logical - extended partition, and while it is possible to do it with windows as well... it is very difficult. The extended supports upto 15 partitions, and any linux can go on that.

Now try and get mac into that scene... ughh, this hasnt been allot of fun for me so far...
hopefully it will be worth it!

---

