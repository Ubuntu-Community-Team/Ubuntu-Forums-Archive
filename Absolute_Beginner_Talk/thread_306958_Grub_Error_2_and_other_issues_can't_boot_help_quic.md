---
title: "Grub Error 2 and other issues can't boot help quick please"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by wildsrv on 2006-11-25
Why do i do this to my self. I was doing so good at learning linux and getting so relaxed, but I guess thats what happens when you let your guard down. Ok people of this very friendly board please lend me your assistance.

I dual boot in to winblows XP Pro (still have to use it for work ::sniffle:: ) but i was using norton partionmagic to resize my partions on my HDA. I have others but no operating system or files are on them so they do not matter at this point. I have HDA1 with Winblows on it, HDA2,3,4 for linux (swap, root, and home) While resizing my partitions it gave me an error and partitionmagic forced me to click ok and close. (can't remember the error but i rember it saying something about being crupt). I played in windows for a few thinking i could get it to work (resize like i was trying to do) and it wouldn't let me so i decided to try to boot in linux and contiue. That is when i fould the issue that i can't boot. While booting i get an error #2 from grub. I think that it is not able to read or doesn't know to look at the correct partition to load linux. But the other ovious issue is i can't load windows either. I do have the live cd and have booted with it a few times but when it loads it just gives me a blank scrren (i need to chage the video options on the pci slot from 2:0:0 to 5:0:0 but on the cd i don't know how to do that...) i can hit ctrl+alt+f1 and goto the prompt however. I hope this is enough information to get this rolling because i don't have much more time off of work and this is the only time i'll be able to work on it for some time. Thanks again.

Edit: I was also just able to mount my orignal root partition. Don't know if ths helps

---

### Post by wildsrv on 2006-11-25
any one?

---

### Post by wildsrv on 2006-11-25
OK mor information. I was able to find out that (HDA3 my root) is croupt and has and the superblok contains illegal information. I don't know if this is fixable but i was able to boot windows and goto the recovery console and fix the MBR so i can atleast boot windows. I have the two partitions for linux as listed above but the only thing i'm wandering if there is going to be an issue once i reload linux? ideas. I didn't delete/format yet.

---

### Post by vtel57 on 2006-11-26
You can attempt to reinstall Ubuntu on the same /root partition that you had it on previously. If you had a lot of personal data in your /home directory, then you can reinstall Ubuntu without formatting the current /home directory, thus saving your data there. When you reinstall, allow Ubuntu to install its GRUB bootloader on the MBR (erasing the Windows bootloader). Don't worry, it will automagically detect the Windows and set it up in the GRUB for you. If you did indeed corrupt the /root partition by resizing it (quite possible), then the reinstall of Ubuntu should solve your problems.

Luck!

---

### Post by wildsrv on 2006-11-26
thanks vtel57 not exactly what i wanted to hear but o well. Now with the two partitions of my files what would be on the root partition that i would want? all my files should be in the other one right (of course depending on where i put them)?

---

### Post by wildsrv on 2006-11-26
you can save your self with the video issues i got that fixed.

---

### Post by bulldog on 2006-11-26
Download the gparted live cd,burn it to a disk and boot from it.
See if you can correct the things you messed up.
PM is a great application which I used several times in the past with no errors.
But I'm using the gparted live cd instead now.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Good luck.

---

### Post by vtel57 on 2006-11-26
> **wildsrv said:**
> thanks vtel57 not exactly what i wanted to hear but o well. Now with the two partitions of my files what would be on the root partition that i would want? all my files should be in the other one right (of course depending on where i put them)?

All your personal items were probably stored in your /home directory. They'll still be there if you reinstall without formatting the /home directory. You will probably have to reinstall whatever apps you had added to Ubuntu before if crashed, though. No biggie. It's salvageable.

---

### Post by wildsrv on 2006-11-26
ok reinstall of the apps isn't that bad of a thing (pratice isn't that bad) its just a pain. So if i'm correct i'll be safe formating the root partition but leave the /home partition alone. Just want to make it clear if i understand what your saying. I ran Ubuntu live cd and got it working when i booted and ran gparted (came with ubuntu??) and it gave me an error and couldn't fix it. I don't mind format just want to know what to back up prior. Thanks all!

---

### Post by catlett on 2006-11-26
Just run the installer like you did when you first installed. When it comes to the partitioner, make sure the partitions match your current configuration, meaning make sure (I am going by your first post for these labels, just make sure it is corrct)
/dev/hda2....swap
/dev/hda3...root
/dev/hda4....home
This is the part to pay attention to. You want to let the installer reformat root but DO NOT reformat home. (it doesn't matter for swap.just let it do what it wants with it) Hda1 with windows aill be left alone by default.
Then select to write the changes to disk and let the partitioner run. When it is done, your home will be left untouched and your root will be fixed.

---

### Post by wildsrv on 2006-11-26
ok thanks i'll try that here in a little bit.

---

### Post by vtel57 on 2006-11-26
> **catlett said:**
> Just run the installer like you did when you first installed. When it comes to the partitioner, make sure the partitions match your current configuration, meaning make sure (I am going by your first post for these labels, just make sure it is corrct)
/dev/hda2....swap
/dev/hda3...root
/dev/hda4....home
This is the part to pay attention to. You want to let the installer reformat root but DO NOT reformat home. (it doesn't matter for swap.just let it do what it wants with it) Hda1 with windows aill be left alone by default.
Then select to write the changes to disk and let the partitioner run. When it is done, your home will be left untouched and your root will be fixed.

Catlett's advice is just what you need to do.

---

