---
title: "Dual Boot XP/Ubuntu -- Would like to remove old hacked up 5.10 &amp; install fresh 6.06"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by prs444 on 2006-10-29
I have a Dell Inspiron 8200 Running Win XP & Ubuntu 5.10(Dual Boot).
The problem is I installed Ubuntu a long time ago and hacked it up pretty bad.(learning linux). I have tried to follow the upgrade instructions but Things keep getting stuck along the way. Not sure if it is things I changed along the way or what. When it tries to upgrade it kept asking for the Dapper CD but when I put the new CD in it would not recognize the Ubuntu CD.
I got the 6.06 CD from Ubuntu and wanted to delete or remove the old version (5.10) and install the new one. Is this possible? I downloaded the Dapper 6.06 alternate iso if that is needed.
If I do remove the old version and replace it with the new version how will that affect the Grub Boot Loader? Will I have to change anything in there or will the install program do this automatically?
Thanks for any guidance!
](*,) Paul

---

### Post by tzulberti on 2006-10-29
When installing the new ubuntu 6.10, it will search for all the OS in your HD, and add them to the grub file. If you format the partition where 5.10 was installed, it wont appear in you grub

---

### Post by oracle5 on 2006-10-29
I messed up my 6.06 install when trying to upgrade to 6.10 and I used the alternate install cd to reformat the partition and install 6.10 from scratch. You can probably do it in the livecd too but I've never used it to know since I prefer to have more control over installations.

---

### Post by prs444 on 2006-10-29
Ok guys, thanks for the ideas!
I managed to get Dapper Installed! Somehow I still have the old version along with my WinXP showing in the Grub boot loader but Dapper seems to be working ok. Now If I can get my wireless card working tonight I will feel like I acomplished something!
Thanks again for your answers, without them I would still be stuck!
:biggrin: 
Paul

---

