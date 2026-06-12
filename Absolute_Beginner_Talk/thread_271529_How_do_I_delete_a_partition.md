---
title: "How do I delete a partition?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Anemic_Royalty on 2006-10-04
Please, people, I need to know: How do I delete a partition on my hard disc? I tried installing Ubuntu but something went wrong, and now I don't know how to get back onto Windows! When I tried installing Ubuntu, it created a partition, and I think that's what's stopping me from getting onto Windows. I'm on a Slax LiveCD right now, and I can access both partitions (the one with all my Windows files, etc., and the one that Ubuntu created), but I don't know how to delete the partition that Ubuntu created. Please help!

---

### Post by kidders on 2006-10-04
Deleting a partition won't help you boot into Windows, I'm afraid :-( but you can do it easily enough with a partition editor like qparted or cfdisk.

---

### Post by Anemic_Royalty on 2006-10-04
> **kidders said:**
> Deleting a partition won't help you boot into Windows, I'm afraid :-( but you can delete one easily enough with a partition editor like qparted or cfdisk.

Can you please help me get into Windows, then? I really need help!

---

### Post by kidders on 2006-10-04
It's hard to say exactly why your Windoze stopped working without a little more information. What did you do? What happens when you try to boot it?

---

### Post by Anemic_Royalty on 2006-10-04
> **kidders said:**
> It's hard to say exactly why your Windoze stopped working without a little more information. What did you do? What happens when you try to boot it?


Well I tried installing Ubuntu, and it had a couple of installation problems. I don't exactly know what. I mean, I burned the image to a CD, and then when I booted it up, there were a couple of options: "Install as text" or something like that, "Install as OEM" or something like that, and someothers. I clicked "Install as text". Well, it created a partition, and then there were some errors. I don't know what. Anyways I don't care about getting Ubuntu anymore, I just urgently need Windows! So now when I try to start up my computer without this Slax LiveCD in, it says "Please use proper boot device or insert..." I don't know what it says after that. Basically it tells me that it doesn't have anything to boot up. However, I KNOW that I still have all my Windows stuff because I can access it through Slax. Does that clarify anything?

---

### Post by h2gofast on 2006-10-04
if slax can see your windows partition then your windows install is most likely still there.  It sounds like your boot loader (called grub) is messed up.  Ubuntu installs grub and grub gives you the option of booting into windows or linux.  I would try the ubuntu install again.  If you have older or oddball hardware that ubuntu is having issues with, try xubuntu, it seems to work better on older/oddball hardware.  

What this will accomplish is successfully installing grub to your master boot record.  What this means is that you will get windows back.  
 
It sounds like chances are your ubuntu install overwrote your mbr when install grub and then got screwed up.   There might be a way for windows to fix what has been erased on the mbr.  
You have two options.  
1. repair the mbr and forget about linux [http://www.tech-recipes.com/windows_installation_tips483.html](http://www.tech-recipes.com/windows_installation_tips483.html)

2. Try ubuntu/xubuntu and get a dual boot system where you can choose between linux and windows everytime you turn your computer on.

Cheers, 
h2.

---

### Post by kidders on 2006-10-04
Exactly what went wrong would be useful to know. For instance, it's entirely possible that Ubuntu tried to resize your Windows partition for you, failed somehow, screwed it up, and now it won't work.

In any case, your hard drive doesn't seem bootable any more. You should probably boot your system with a Microsoft boot CD and rescue it that way.

---

### Post by podunk on 2006-10-04
[http://www.tech-recipes.com/windows_installation_tips483.html](http://www.tech-recipes.com/windows_installation_tips483.html)

---

### Post by kidders on 2006-10-04
> **h2gofast said:**
> It sounds like your boot loader (called grub) is messed up.

If your install got that far, then ignore my post ... h2gofast's is waaay better!

---

