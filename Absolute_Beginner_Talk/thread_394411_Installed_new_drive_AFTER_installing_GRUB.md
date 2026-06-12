---
title: "Installed new drive AFTER installing GRUB"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-26
Two hours ago, I finished installing a new Seagate 160 GB HDD. BIOS recognizes it and I can boot to it when it is set as MASTER. When I change it to SLAVE, my Master HDD (Ubuntu) will not recognize it. Do I have to re-install Ubuntu with the new drive attached as slave, or is there a way to mount it and have GRUB recognize it?  I tried mounting it through Nautilus. It wouldn't or couldn't do it. See attachment, please.
kh

---

### Post by Crushyerbones on 2007-03-26
Sorry about not being able to help much (I'm a Linux noob), but I think you have to edit some file or other on ubuntu to mount drives other than your Ubuntu partition.

Look around for how to mount drives and/or different partitions on this forum with the device set as a slave.

That is... if I understood your question right

---

### Post by kittyhawk63 on 2007-03-26
> **Crushyerbones said:**
> Sorry about not being able to help much (I'm a Linux noob), but I think you have to edit some file or other on ubuntu to mount drives other than your Ubuntu partition.

Look around for how to mount drives and/or different partitions on this forum with the device set as a slave.

That is... if I understood your question right

You did. I've looked, but I will keep looking. Someone has bound to have had this come up before me. Thanks for your reply.

:)kh

---

### Post by halitech on 2007-03-26
GRUB doesn't really have anything to do with seeing the drives, only setting the boot options for drives that have an OS on them. Do you want to use the drive as storage for your existing install or were you hoping to use it instead of the original drive?

---

### Post by alienexplorers on 2007-03-26
[http://www.smorgasbord.net/book/export/html/195](http://www.smorgasbord.net/book/export/html/195)

---

### Post by kittyhawk63 on 2007-03-26
> **halitech said:**
> GRUB doesn't really have anything to do with seeing the drives, only setting the boot options for drives that have an OS on them. Do you want to use the drive as storage for your existing install or were you hoping to use it instead of the original drive?

I want to use it with WinXP (with Word2000) set as slave drive. I have another drive with Ubuntu set as my master. I need Word 2000 for editing books for authors. 00.0 has some problems properly formatting some of Words features.
kh

---

### Post by kittyhawk63 on 2007-03-26
> **alienexplorers said:**
> [http://www.smorgasbord.net/book/export/html/195](http://www.smorgasbord.net/book/export/html/195)

I'm on my way to check this out. Thanks.
kh

---

### Post by halitech on 2007-03-26
> **kittyhawk63 said:**
> I want to use it with WinXP (with Word2000) set as slave drive. I have another drive with Ubuntu set as my master. I need Word 2000 for editing books for authors. 00.0 has some problems properly formatting some of Words features.
kh

ok, Windows doesn't like not being the primary boot drive so you will probably need to have it as the primary master with Ubuntu being primary slave. you need to somehow get grub installed on the windows drive so it will see the OS's on your computer. the other option would be to run MS Office in WINE or crossover office.

---

### Post by kittyhawk63 on 2007-03-26
> **halitech said:**
> ok, Windows doesn't like not being the primary boot drive so you will probably need to have it as the primary master with Ubuntu being primary slave. you need to somehow get grub installed on the windows drive so it will see the OS's on your computer. the other option would be to run MS Office in WINE or crossover office.

Ok. I am on my way to installing Ubuntu for the inth time. Do I set it as master when I am installing Ubuntu and have Windows hdd as slave? Or, do I have the hdd I want as Ubuntu set as slave with windows as master? I hope this is clear.
kh

---

### Post by halitech on 2007-03-26
hopefully this will clear things up :D

primary master - Windows

secondary master - ubuntu

You could try taking the ubuntu drive out and installing windows, then put the ubuntu drive back in next month when you get finished installing windows and the updates ;) then boot from a linux livecd and fixing grub to allow you to see all the operating systems in the system

you can use this link for info on setting up the MBR after getting windows installed and hooking up the ubuntu drive

[http://www.windowsitpro.com/Articles/ArticleID/13754/13754.html?Ad=1]("http://www.windowsitpro.com/Articles/ArticleID/13754/13754.html?Ad=1")

---

### Post by Crushyerbones on 2007-03-26
> **kittyhawk63 said:**
> I want to use it with WinXP (with Word2000) set as slave drive. I have another drive with Ubuntu set as my master. I need Word 2000 for editing books for authors. 00.0 has some problems properly formatting some of Words features.
kh

Oh... That will be a bit hard I think... You can install Windows easily on it, just put the CD in and install as usual on the drive you want.

BUT (THIS IS IMPORTANT)

The windows bootloader will overwrite Grub and make you unable to run Ubuntu again, only windows.

You CAN install Ubuntu afterwards to restore Grub or maybe you can manually exchange the windows bootloader to grub, but that sounds like a nightmare to do all by yourself.

~~~~~

Isn't removing the ubuntu drive useless? The windows bootloader will delete grub all the same but if he installs Windows on a different drive it won't touch Linux will it?

---

### Post by kittyhawk63 on 2007-03-26
> **halitech said:**
> hopefully this will clear things up :D

primary master - Windows

secondary master - ubuntu

You could try taking the ubuntu drive out and installing windows, then put the ubuntu drive back in next month when you get finished installing windows and the updates ;) then boot from a linux livecd and fixing grub to allow you to see all the operating systems in the system

Windows XP is already installed onto the new drive. I did that ealier this afternoon. I took out the Linux hdd and installed the hdd for WinXp with the jumper set as master. After installing WinXp I reset the new hdd as slave. I reattached the Linux drive set as master. 
I guess I needed to have both drives attached at the same time to make sure GRUB was propely installed.

---

### Post by halitech on 2007-03-26
if you had installed windows with Ubuntu already installed it would have wiped your grub anyway.

you can try manually editing grub to add windows to the list

actually, try opening a terminal and running this

```

sudo update-grub

```

---

### Post by kittyhawk63 on 2007-03-26
Me thinks I have said something to confuse some of you.
Let's see if I can make this clearer.

First off, I installed Linux when I had only _one_ HDD.

Now, here is where I am. I now have two HDDs.
1. I unhooked my old Linux HDD from my computer.
2. I hooked up my new HDD setting the jumper to the master position. I formatted the new HDD using the utility disk that came with the HDD. I then installed WinXP. I booted up and everything was working right. I then unhooked my new HDD, set the jumper to slave. I then hooked it back to the computer. Remember now, it is set as slave.
3. I then hooked up my old HDD (with Linux) set as master.

Now I have two HDDs.
One set as master with Linux. 
One set as slave with WinXp.

I am trying to get Grub to list my new HDD on boot.

Should I have re-installed Linux with both HDDs attached? If so, how would the jumper(s) be set for each?

---

### Post by kittyhawk63 on 2007-03-27
[FONT=monospace]I did these and they fixed my problem.

sudo update-grub

and then followed the instructions given here:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

[/FONT]Be sure to remove the # before  hiddenmenu or hidden, whichever you have.

---

