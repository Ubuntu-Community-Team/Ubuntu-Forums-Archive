---
title: "Have a problem booting"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Delusiondejavu on 2008-01-12
I have XP on my primary HD and I installed Ubuntu 7.10 on my slave. I did this from the live cd and after rebooting I get a Grub error 21.  I tried looking online but have not found an answer that has helped.  I did a fixmbr so that I could get back into XP.  I want to have the dual boot setup if anyone can help me I really appreciate it.  I am a newb to Ubuntu and Linux.

---

### Post by ckuka on 2008-01-12
When you ran fxmbr, grub, the interface you would most likely use when booting up is no longer useabble and wont be able to access ubuntu. If your windows partition was not damaged, you may want to try installing ubuntu again, but you will overwrite your main boot record again. You should be able to successfully set up a dual boot by setting up partitions using gparted on the livecd, formatting the partitions, and then running the install located on the desktop. If you are uncertain how to set up what disk space will be used by ubuntu, I would suggest reading the forum "complete guide to installing ubuntu" in the Absolute Beginner Talk, or simply follow the directions on the live cd and hope for the best. 
Good luck, I hope you are able to get things running!

---

### Post by Delusiondejavu on 2008-01-12
> **ckuka said:**
> When you ran fxmbr, grub, the interface you would most likely use when booting up is no longer useabble and wont be able to access ubuntu. If your windows partition was not damaged, you may want to try installing ubuntu again, but you will overwrite your main boot record again. You should be able to successfully set up a dual boot by setting up partitions using gparted on the livecd, formatting the partitions, and then running the install located on the desktop. If you are uncertain how to set up what disk space will be used by ubuntu, I would suggest reading the forum "complete guide to installing ubuntu" in the Absolute Beginner Talk, or simply follow the directions on the live cd and hope for the best. 
Good luck, I hope you are able to get things running!I had to restore the mbr with the XP disk.  I had no choice because I could not boot into any OS (without a cd) because of the grub error.  I can reload using the live cd but I am afraid i will get the same grub error. I still have Ubuntu  installed on the 2nd HD but I can't boot it because I don't have a dual boot program.  Is there a way to load grub or something like that without reloading Ubuntu?  I might figure this out one day LOL...  

Another question is should I not Use 2 hard drives?  I thought this would be best.  I gave Ubuntu a 40g hd.  The 40g had nothing on it.

---

### Post by logos34 on 2008-01-12
Here's a really good guide:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by ckuka on 2008-01-12
If you get the same error, the grub file itself may be corrupted. (although i think it is unlikely). Run a checksum, or boot using the livecd and there is an option to verify the disks' data. 
Also, Are you using two separate physical drives, or logical? It should not matter, I am just curious. The link logos34 posted should answer all of your questions about how to set up the dual boot.
good luck!

---

### Post by Can+~ on 2008-01-12
When an application gives you a numbered error (in this case, error 21. The best way to get some quick info, is looking in google. "Grub error 21"

---

### Post by bumanie on 2008-01-12
If you did a fixmbr this would have overwritten grub. It is likely that you can fix grub and point tell it where to go. As yo cannot boot into ubuntu at present, you have two choices. the first is to boot into the live cd and try to fix it from there or you could download supergrub disk (a live cd) and give it a try.
Supergrub disk is not officially supported by linux, however it has proved to be very good and is helpful with fixing grub (some) errors. As long as grub has been installed on your hard drive supergrub disk will be able to get the computer to boot into either xp or ubuntu. It also gives a choice for fixing linux/gnu boot and sometimes it does fix it and you won't need to do any more.
Give that a try first - it is a handy tool to have around because it can boot windows and  linux.
If supergrub disk doesn't work, boot with live cd and once on the desktop,open terminal and type 
sudo grub --> enter
>grub find /boot/grub/stage1    [You will get an output (hd?,?) and a file system mentioned] from what you said you should get an output of (hd1,0), if I understood how you set up your computer.
>grub root (hd?,?) [replacing the ? with the corresponding numbers from the above output]
>grub setup (hd?)
>grub quit
If you manage to boot into ubuntu and can't fix grub then post the output of 
gksudo gedit /boot/grub/menu.lst [that is a lower case L, not a 1] and post the output.

---

### Post by dfeller on 2008-01-13
Regarding supergrub, that tool provides a manual boot option that will allow you to test and make sure everything else is ok - when you insert the live supergrub CD, one of the options is to manually boot into either OS - as long as that works, the same CD contains the scripts to reinsert grub in the mbr and fix your problem. Good luck.

---

### Post by hums07 on 2008-01-14
There is a way to boot using XP bootloader. So MBR still belongs to XP, then when XP starts bootloader (via NTLDR) we can give it a choice to boot to XP as usual or boot to other OS. In this way, if the other OS has a problem, you can always boot to XP.

In short this is how you do it:
1. Install grub to the slave HD
2. Copy the slave HD boot record to a file
3. Move the file into XP filesystem (C:\)
4. edit C:boot.ini so it give another option to execute the file
Sry I have a short time at the moment, but I believe someone else can explain in more detail.

---

### Post by Sef on 2008-01-14
Easiest way to reinstall GRUB is with [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by adrian15 on 2008-01-16
> **Delusiondejavu said:**
> I have XP on my primary HD and I installed Ubuntu 7.10 on my slave. I did this from the live cd and after rebooting I get a Grub error 21.  I tried looking online but have not found an answer that has helped.  I did a fixmbr so that I could get back into XP.  I want to have the dual boot setup if anyone can help me I really appreciate it.  I am a newb to Ubuntu and Linux.

Boot with a live cd. Check the menu.lst file... edit the groot line for something like:

groot = (hd0,X)

write

groot = (hd1,X)

Save the file

Run update-grub from inside a chroot environment (in your linux partition) so that menu.lst is regenerated.

Tell SGD to Linux -> Fix Boot of Linux. (I think this step is not needed in your case).

No error 21 should happen right now.

You can also check the Boot & Tools -> LiveSwap option (in SGD) if problems persist.

adrian15

If you need help on how to run commands inside a chroot please ask the other forum users or ask them for a guide to check it.

I hope some day I will finish Rescatux so that these kind of problems can be solved easily. Patience.

---

