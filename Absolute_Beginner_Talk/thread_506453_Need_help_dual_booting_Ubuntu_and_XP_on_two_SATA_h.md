---
title: "Need help dual booting Ubuntu and XP on two SATA hard drives"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by kircher1 on 2007-07-21
I just started using linux, so I don't know alot about what I'm doing. 

Both of my hard drives are SATA, and hence they are both on seperate channels and each is a master.
My bios won't let me change that, so I can't use the master/slave dual boot method.

But I've got the dual-boot scenario to work where I can choose from a menu which OS I want to run - XP or ubuntu.  I used the method here - [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902). 

 However, after a few XP restarts, when I choose to boot into XP I get the NTLDR is missing error which means I can't boot into windows at all. This has now happened twice. The last time I fixed it by copying the NTLDR file from the XP install cd to my C drive, and then succesfully rebooting into windows.  However, when I did that XP would start without the option menu for ubuntu/xp. So, I had to disconnect the XP drive, boot the Ubuntu drive, then shutdown and reconnect the XP drive, and then the OS menu succesfully worked again.  

I REALLY DON'T WANT TO DO THIS EVERY TIME I GET AN NTLDR IS MISSING ERROR. 

I don't know what causes the NTLDR error, becuase i didn't install any new updates for windows before my last reboot. So... can anyone help me fix this problem? I'd really like to dual-boot both OS's without this stupid NTLDR error.

---

### Post by Moop on 2007-07-22
I have the same setup and no problems. Even though both sata drives are masters you should still be able to change the boot order in the bios. 

I have XP on sata1 and Ubuntu on sata2. Make sure that XP is installed first and then install Ubuntu to sata2, I chose the "use entire disk" option and left grub at it's default setting. 

After Ubuntu is installed you need to boot from sata2. Grub will give you the option of booting XP or Ubuntu. If you boot from sata1 you will boot directly into XP.

---

### Post by kircher1 on 2007-07-22
my ubuntu is on sata1 and xp is on 2, but i edited the grub so that it works that way. so far i haven't had any more problems with my NTLDR since i fixed it for the second time. I don't know why it got screwed up in the first place though. I still can't find a place in my bios to choose which HD boots first, but so far thats not an issue. thanks

---

