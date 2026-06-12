---
title: "Xp &amp; Kubuntu Fiesty - Lost Grub / Error 17"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by mikelucasiscool on 2007-07-16
From the beggining

I was running windows xp 80gb one partition
installed kubuntu fiesty dual boot 60gb windows 20gb Linux
ok
windows crapped out
deleted windows partion
created a new partions for windows 30gb
installed windows
windows killed grub no option to boot to linux

tried these instructions
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
to recover grub
everything in those commands went well until i typed "quit" then it gave me an error i copied it and pasted into kate but some how lost the error :( (sorry)
rebooted hoping maybe it worked anyway

Grub was back and everything looked the way it was before, however 

When i tried to boot to linux i got
"Error 17: cannot mount selected partition"

at that point i had that raw partition and 
i thought maybee it was the problem 
so i formated it with the xp disk 
at which point it got rid of the grub again

Any ideas?

i have files under my linux install i would like to keep

- T4ct1cs

I have Kubuntu Fiesty install cd and can boot to that, however i can't seem to figure out how to mount my old linux :S i am so lost.

---

### Post by gn2 on 2007-07-16
All the information you need is in the Hermanzone link in my sig.

Basically if you install Windows after Ubuntu, Windows overwrites the Grub bootloader.

All you need to do is re-install Grub again.

There are other bootloaders one of which is Gag, and information regarding all of this has been kindly written up by Herman.

---

### Post by SamMessing on 2007-07-20
I have a similar problem. I have a system where I'm dualbooting between Windows and Ubuntu (on two different drives). I booted into Windows and then restarted and it appeared as though Windows had deleted my Main Boot Record (MBR).

I reinstalled grub to fix the issue with an ubuntu live cd, and then tried to restart. Seemed to work, but when I selected Ubuntu from the grub menu, I got error 17: failed to load partition. I also cannot boot into Windows, although selecting the OS just brings me back to grub's main menu.

I tried using the Super Grub Disc, but it didn't seem to help. I don't think the issue has anything to do with grub any more.

Can someone help me out? Or at least direct me? What do you think is going wrong?

Thanks!

---

### Post by mikelucasiscool on 2007-07-20
I finally gave up, i also used super grub disk with no sucess :S no resolution to my problem i finally became really irritated and wiped everything out and started over.

---

