---
title: "How to install rEFit...without OSX"
date: 2009-05-06
forum: Apple Hardware Users
---

### Post by Romu on 2009-05-06
Dear all,
I'm trying to get back to Ubuntu only on my Macbook Pro 2G.

I recently was with a double boot OSX + Ubuntu and rEFIit, and I don't like this, too many user rights problem when using a common partition to access data from the 2 OSes.

I've just discovered rEFIit is not installed on the EFI partition but on the OSX one, that explains while I don't have rEFIit at boot time anymore...I just kept the EFI parition.

So, my question is: is there a way to install rEFIit when there is only Ubuntu on the Mac? The purpose is to remove the 30s lag at startup.

Thanks in advance.

---

### Post by cyberdork33 on 2009-05-06
> **Romu said:**
> Dear all,
I'm trying to get back to Ubuntu only on my Macbook Pro 2G.

I recently was with a double boot OSX + Ubuntu and rEFIit, and I don't like this, too many user rights problem when using a common partition to access data from the 2 OSes.

I've just discovered rEFIit is not installed on the EFI partition but on the OSX one, that explains while I don't have rEFIit at boot time anymore...I just kept the EFI parition.

So, my question is: is there a way to install rEFIit when there is only Ubuntu on the Mac? The purpose is to remove the 30s lag at startup.

Thanks in advance.

First, have you blessed the Linux partition?
[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21](http://ubuntuforums.org/showpost.php?p=5166788&postcount=21)

if you still want to install rEFIt, you can, you will need to copy the appropriate files into the EFI partition and then use the bless command to bless it. (The bless part requires OSX. You can use the terminal on the Installation DVD.)

---

### Post by Romu on 2009-05-06
Whaou, many thanks, I didn't know at all about such a trick.

I'll try asap.

Do you know if there is a way to make this trick the normal Ubuntu operating mode?

---

### Post by cyberdork33 on 2009-05-06
> **Romu said:**
> Whaou, many thanks, I didn't know at all about such a trick.

I'll try asap.

Do you know if there is a way to make this trick the normal Ubuntu operating mode?
unfortunately, you cannot since the bless command is in OSX... but someone working with GRUB2 is working on an open source version of the same thing, so it may very well become reality in the future.

---

### Post by Romu on 2009-05-07
Ok thanks.

Last question: if I do this, will I be able to get back to the normal configuration in the future (for example if I want to switch to OSX)?

---

### Post by cyberdork33 on 2009-05-07
> **Romu said:**
> Last question: if I do this, will I be able to get back to the normal configuration in the future (for example if I want to switch to OSX)?
I don't fully understand what you are asking, but if you mean can you go back to OSX only, or even dual-booting with OSX, then yes.

Bless is just a utility that sets a flag telling the firmware what is the default boot item. OSX blesses itself when it is installed... rEFIt blesses itself when it is installed (by default). When you use the statup disk utility in OSX to select another partition or CD to boot, you are "blessing" that volume.

---

### Post by Romu on 2009-05-07
ok, thanks.

---

### Post by handy on 2010-03-03
Why don't you want to maintain a small OS X, partition?

It gives you the ability to upgrade your firmware.

Of course if you have an external drive that you can run OS X, from, then that will solve this problem.

---

### Post by jbiggs12 on 2011-02-22
So I suppose this thread's a bit old to be replied to, but would it be possible to bless the volume while the computer is in fw target mode? That way I wouldn't have to bless it from my nonexistent OSX partition on that computer.

---

