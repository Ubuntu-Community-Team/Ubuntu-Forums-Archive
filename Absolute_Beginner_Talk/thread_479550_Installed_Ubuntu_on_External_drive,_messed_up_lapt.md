---
title: "Installed Ubuntu on External drive, messed up laptop"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by amoroso3645 on 2007-06-20
Ok so here is my problem
I booted up ubuntu using the live cd, installed it on my usb connected external hard drive and everything works fine. However once the external drive is disconnected and i attempt to reboot my laptop I keep on getting a "grub 21" error message. when the drive is reconnected and rebooted i'm given a list of OS options such as windows media edition or unbuntu. Does anyone one know how to fix this. I'd like to be able to start up my laptop without having to lug around an external drive. btw if this has been talked about before can someone just forward me to that thread.

---

### Post by Happy_Man on 2007-06-20
This is not just one thread, bud, it's almost 100 or so. What you have to do now, is to boot up a Windows CD, choose fixmbr. That gets back your Windows bootloader. Now, use the Super GRUB disc to install GRUB to the external drive. That way, when the laptop doesn't detect GRUB, it'll boot Windows, and when it does, it'll give you a choice. 

Super GRUB disc: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by molly_001 on 2007-06-20
Good advice from Happy Man, also please note that many laptop brands including Dell (100% of Dell laptops) use a proprietary MBR structure, and fixmbr command won't repair those types of MBRs.

---

### Post by Kubunteando on 2007-06-20
That is not totally true, I had the same problem installing Edgy and then when installing Feisty in an USB disk in a Dell Latitude 600, and "fixmbr" solved the issue.

I think we should fill a bug with this, because when you upgrade the kernel packages also messes up the grub installation. You can still boot Windows though, but not Linux, until you fix the grub menu file.

---

### Post by molly_001 on 2007-06-20
> **Kubunteando said:**
> Kubu wrote: ...

That is not totally true, I had the same problem installing Edgy and then when installing Feisty in an USB disk in a Dell Latitude 600, and "fixmbr" solved the issue.





I should amend the earlier statement to be more specific about two things regarding "fixmbr" and Dell laptops.  The "fixmbr" will work on older models (mid-2003 and earlier) such as the Latitude 600; Dell wasn't using the proprietary MBR yet.  

Also, I *think* that proprietary MBR of Dell is written only in the case of Windows being restored on the ***main internal boot HD*** when their Restore partition process is used.

I get around it by wiping the (internal) HD clean of all partitions including hidden Utility and Restore partitions (which GParted LiveCD can detect) and then when I have 100% unallocated, I install XP using any Dell Reinstallation Windows CD and not using their restore partition method.

---

### Post by hectorr on 2007-10-09
ok
i have the same problem on an acer aspire 1520. thing is i dont have a normal xp cd, but just a recovery, that only formats c and copys windosn onto it. do i have to get a windows cd from somewhere, or is there another way to restore the windows bootloader?
btw. i bought this laptop in december 2006

---

### Post by bigken on 2007-10-09
> **hectorr said:**
> ok
i have the same problem on an acer aspire 1520. thing is i dont have a normal xp cd, but just a recovery, that only formats c and copys windosn onto it. do i have to get a windows cd from somewhere, or is there another way to restore the windows bootloader?
btw. i bought this laptop in december 2006


you can use any windows xp cd and the correct commands are 

fixmbr  (enter)

fixboot  (enter)

exit (enter)

---

### Post by hectorr on 2007-10-09
it doesnt work wit my cd, because it never gives you any chance to type in and enter things. it gives a menu of languages and asks if you realy want to format c:. theres no dos or anything, t use because its a recovery by acer, whis only puts the c drive the way it was whenyou bought theh pc.

---

### Post by bigken on 2007-10-09
borrow a windows xp cd from somebody your cd sounds like a restore disc

when you booot from the windows cd you press R at the prompt to enter 
repair console then use the fixmbr fixboot commands

---

### Post by skymera on 2007-10-09
i had this problem last week

i deleted install on external.

but you can reinstall GRUB on your internal version.

then reinstall grub on External Ubuntu to a different place.

---

### Post by hectorr on 2007-10-09
i guess ill just borrow a xp cd, which shouldn be too hard, just so that ists simply normal windows. i have had enought trouble with this laptop already (irq not lo ro equal, antivir sign missing in tray and sometimes protection not starting etc. thanks for now, ill ask again if it doesnt work :D

---

### Post by hectorr on 2007-10-14
ok
i had som,e probs with the windows disk, cause of the admin pw. now windows is ok, but i cannt get grub to install onto the external drive. i tryed, but the disk owuldtnt install. what do i have to choose?

---

