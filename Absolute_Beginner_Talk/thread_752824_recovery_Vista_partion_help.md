---
title: "recovery Vista partion help"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by penguin5 on 2008-04-12
Before I installed ubuntu 7.10 to dual boot with vista, I partitioned the drive C and D together and then gave half to vista and the other half to ubuntu. But now I realized that vista used the D drive for recovery. So now when i try to make a recovery disk, it says that there is not enough memory on my D drive, which no longer exists. What should I do? How can I make a recovery disk when ubuntu is using that half of the dive which i also formatted for ubuntu. Do I have any options available? 

Your help is appreciated,
 
-Alex

---

### Post by Master Yami on 2008-04-12
Your recovery partition is completely gone and can't be gotten back, so you might have to order a recover disk set through your manufacturer, depending on who it is. I know HP lets you order them, but I don't know about others.

Just take more care next time.

---

### Post by penguin5 on 2008-04-13
So there is nothing I can do to get it back? I also found a 7.8 GB partition that does not show up in My Computer. Any ideas on what this hidden partition may be? 

Also, when I dual boot my acer aspire 3680 laptop, on the selection menu I get ubuntu, vista and other option called "NT/Windows XP. Im afraid to select it. Is that unusual to have when dual booting even though my OS is vista and ubuntu?

Thanks for all your help 
.

---

### Post by penguin5 on 2008-04-13
Any ideas?

---

### Post by nazareno on 2008-04-13
i think your recovery is gone.. next time be careful

---

### Post by Master Yami on 2008-04-14
> **penguin5 said:**
> So there is nothing I can do to get it back? I also found a 7.8 GB partition that does not show up in My Computer. Any ideas on what this hidden partition may be? 

Also, when I dual boot my acer aspire 3680 laptop, on the selection menu I get ubuntu, vista and other option called "NT/Windows XP. Im afraid to select it. Is that unusual to have when dual booting even though my OS is vista and ubuntu?

Thanks for all your help 
.

Don't be afraid to select it, it may be a recovery partition of some sort. A lot of manufacturers hide the recovery partition - though usually it will appear in Linux and GRUB. My GRUB menu has two options for windows vista on my desktop - one of them is recovery.

Again, be more careful when partitioning - check what the partitions contain before deciding to format them.

---

