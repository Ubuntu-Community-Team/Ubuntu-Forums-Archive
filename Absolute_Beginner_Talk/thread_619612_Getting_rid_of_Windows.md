---
title: "Getting rid of Windows"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by mdinfamy on 2007-11-21
So currently I have my computer set up so it dual boots Windows XP and Ubuntu.  I installed Ubuntu yesterday and it created a parition to put it on.  How can I remove Windows from the other partition and then combine both partitions to make one whole again?  I have nothing I need to save on the Windows partitoin -  I already backed it all up.

Thanks!

---

### Post by Inxsible on 2007-11-21
If you don't plan to use Windows for anything at all, you can use the GParted on the Live CD to format that drive. you will also need to remove the Windows entry from the grub menu.

---

### Post by mdinfamy on 2007-11-21
thanks I can format that drive using the cd.  What about removing it from the Grub menu? How do I do that

---

### Post by mdinfamy on 2007-11-21
You know what, I wouldn't mind getting rid of everything at alll and then installing Ubuntu over on a fresh hard drive?

Like reformat entire computer and then install Ubuntu off the cd?

---

### Post by Inxsible on 2007-11-21
```
gksudo gedit /boot/grub/menu.lst
``` Then simply remove the entry for Windows and save the file.

---

### Post by Incense on 2007-11-21
> **mdinfamy said:**
> You know what, I wouldn't mind getting rid of everything at alll and then installing Ubuntu over on a fresh hard drive?

Like reformat entire computer and then install Ubuntu off the cd?

that would be the easy way. Just reinstall, and let ubuntu use the entire drive this time round. Then it will reinstall grub for you, and you don't have to worry about that at all.

---

### Post by Inxsible on 2007-11-21
> **mdinfamy said:**
> You know what, I wouldn't mind getting rid of everything at alll and then installing Ubuntu over on a fresh hard drive?

Like reformat entire computer and then install Ubuntu off the cd?You could do that too. This way you won't have to change the grub menu and will be much cleaner, i think.

---

### Post by mdinfamy on 2007-11-21
Yea, I think thats what I'm going to do.  Can I reformat everything using the Live CD?

---

### Post by FuturePilot on 2007-11-21
> **mdinfamy said:**
> Yea, I think thats what I'm going to do.  Can I reformat everything using the Live CD?

Yep. When you tell it to use the entire drive, it will reformat the entire drive as well.

---

### Post by Inxsible on 2007-11-21
since you are installing anew, I would suggest that you make a separate home partition. It will help you out in the future.

I don't think the auto install does that. I would always go for manual partition, just so I know what partitions I have and so on. Since you have already done this for the dual boot, it shouldn't be too difficult for you.

---

### Post by Incense on 2007-11-21
Yeah, when you hit the point in the install where it asks you to partition your drive, you can just select "Use the entire drive" and ubuntu will take care of everything for you. You can also run a program called gparted form the live disc, and delete the partition manually.

---

### Post by mdinfamy on 2007-11-21
kk thanks a lot everyone

---

