---
title: "from dapper (with xp and grub) to gutsy (keeping xp and grub)"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by eimor on 2007-11-15
Hi,  im from argentina (spanish speaker) and my english sucks, hope you understand what im trying to ask. Well,  here is the problem. I have dapper and xp in the same hard drive and i use grub to choose wich os i want to booy. I got my gutsy yesterday and wanted to know if there is a way to install gutsy where dapper is without changing xp partition and keeping grub working fine. I also have a fat32 partition to move files from one os to the other that i must preserve. My dad needs xp because he uses a company program thats not linux compatible. Thanks in advance

---

### Post by louieb on 2007-11-15
Hello, Your writing is fine. And you should not have a problem reusing the same partitions now used by Dapper.  You will need to use the manual partitioning option and choose you Gutsy mount points to match what you have in Dapper. 

If you have any questions please open a terminal window and run ```
mount
```and post the output with your question.
Also did you get the Live or alternate install CD?

---

### Post by eimor on 2007-11-15
i got the live cd from Canonical. So, if i didnt get it wrong, when i get to the point where i have to choose from guided options or manual option to specify wich partition will belong to gutsy, i choose manual, and simply select the dapper existing root partition to be the gutsy root? what about the swap partition, do i have to do the same with that. And doing this wont affect grub so the next time i boot il be able to choose gutsy or xp? Oh, thank you for your reply, its like being in a chat.
,

---

### Post by bulldog on 2007-11-15
> **eimor said:**
> i got the live cd from Canonical. So, if i didnt get it wrong, when i get to the point where i have to choose from guided options or manual option to specify wich partition will belong to gutsy, i choose manual, and simply select the dapper existing root partition to be the gutsy root? what about the swap partition, do i have to do the same with that. And doing this wont affect grub so the next time i boot il be able to choose gutsy or xp? Oh, thank you for your reply, its like being in a chat.
,

Your GRUB will be overwritten.it has to because you use another kernel.
But don't worry,your windows entry will be there too.
Yes you need to mount your / and your swap.
Set the / to format ext3 and bootflag enable
swap must be format as swap.

---

### Post by eimor on 2007-11-15
Thanx for your quick replies, ill try this and hopfully i will be posting to thank you all again from my freshly installed gutsy (but first ill have to configure roaring penguin so i can connect to dsl, ;)  ). Oh damn look at the time!!, forgot to go to class, im fed up with electronic engineering. Well, tonight, as soon as i get back from  university ill try this, bye

---

### Post by eimor on 2007-11-15
hi guys, im posting from my new os, gutsy, im so happy, thanks for all your help. It took me no time to get it working. You have been so useful to a newbie like me, thanxs a lot. 
What else can i say........ ah, yeap, UBUNTU ROCKS:guitar:

p.d.: How can i get the compiz effects (the rotating cube, etc.)

---

