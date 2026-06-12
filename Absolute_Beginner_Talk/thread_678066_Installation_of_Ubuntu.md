---
title: "Installation of Ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Ayrek on 2008-01-25
Hello. 

I am new to the Linux world and I want to get Ubuntu working on my PC. I have WinXP on one HDD and another HDD with nothing on it, I am attempting to install Linux on this empty drive and Dual Boot. 

My problem is:

When I insert the dics, my comp reads it and it gives me the menu, i select the option to install. The progress bar goes back and forth for a bit, the HDD crunches and then the system locks up. I also had problems installing SuSE. Anyone know what the issue might me?

Please help! I want to run Ubuntu. 

My system is an HP a1220n

Hardware
Base processor 
Pentium4 516 (P) 2.93 GHz:
533 MHz front side bus
Socket 775
Chipset 
Intel 915GV
Motherboard 
Manufacturer: Asus
Motherboard Name: PTGD-LA
HP/Compaq motherboard name: Goldfish3-GL8E
2GB Ram 

Any help would be appreciated. 

Thanks!

---

### Post by Het Irv on 2008-01-25
Is the empty HD a new one?
If you enter BIOS do both hard drives appear in the Boot Menu?

It almost sounds like the Blank HD is having a problem.

---

### Post by agim on 2008-01-25
When you get to the menu, choose the option to test the cd. It will make sure that the problem isn't just a bad cd. If it tests ok we can go from there.

---

### Post by Het Irv on 2008-01-25
> **agim said:**
> When you get to the menu, choose the option to test the cd. It will make sure that the problem isn't just a bad cd. If it tests ok we can go from there.

Thanks for that.  I always forget the simple step.

---

### Post by Ayrek on 2008-01-25
> **agim said:**
> When you get to the menu, choose the option to test the cd. It will make sure that the problem isn't just a bad cd. If it tests ok we can go from there.


Both HDD's are there. Even SuSE detected them. Nothing wrong with the disc it just freezes up on me. Its driving me insane. I almost had SuSe installed and when it was checking Kernal dependencies at the end of the install the comp locked up. 

I want to run Ubuntu and not SuSE.. lol. 

Could this be a Hardware issue? I have an HP a1220n I posted the specs earlier. Im not sure where to go from here.

---

### Post by toastysquirrel on 2008-01-25
> **Ayrek said:**
> Both HDD's are there. Even SuSE detected them. Nothing wrong with the disc it just freezes up on me. Its driving me insane. I almost had SuSe installed and when it was checking Kernal dependencies at the end of the install the comp locked up. 

I want to run Ubuntu and not SuSE.. lol. 

Could this be a Hardware issue? I have an HP a1220n I posted the specs earlier. Im not sure where to go from here.

I was having a very similar problem when I was trying to install Ubuntu.  Sometimes it installed, sometimes it didn't, usually LifeCD loaded, but every so often it would freeze before the GUI popped up.  Ultimately it came down to a bad drive, more or less (it's kind of a complicated scenario).  Ultimately my install problems went away when I used a different hard drive.  Do you have a spare you can at the very least test with?

---

### Post by Ayrek on 2008-01-25
> **toastysquirrel said:**
> I was having a very similar problem when I was trying to install Ubuntu.  Sometimes it installed, sometimes it didn't, usually LifeCD loaded, but every so often it would freeze before the GUI popped up.  Ultimately it came down to a bad drive, more or less (it's kind of a complicated scenario).  Ultimately my install problems went away when I used a different hard drive.  Do you have a spare you can at the very least test with?


Hmm, maybe I can try repairing it with windows check disk. I had files stored on it when i was using it with windows. Not sure if that makes a difference. Yeah I think i have an extra HDD laying around. Maybe ill try that. Might be the reason for my failed SuSE attempt as well. Other than doing this, any other recomendations? With what i have for hardware it should run hey? It being a HP comp should not affect it in any way? the mobo?

---

### Post by Het Irv on 2008-01-25
Your Hardware (excepting HD) should be fine, being HP shouldn't matter.

---

### Post by Ayrek on 2008-01-25
> **Het Irv said:**
> Your Hardware (excepting HD) should be fine, being HP shouldn't matter.

Yeah thats what I thought. Well ill attempt it with another HDD or try and repair the current one and see if I can get it to work. Other than that I guess im SOL. 

Thanks for the help.

---

### Post by ugm6hr on 2008-01-25
I assume you are using the Gutsy LiveCD.

When the progress bar *goes back and forth*, try pressing Alt+F1.  This should give you text about what the errors are.

---

### Post by Ayrek on 2008-01-25
> **ugm6hr said:**
> I assume you are using the Gutsy LiveCD.

When the progress bar *goes back and forth*, try pressing Alt+F1.  This should give you text about what the errors are.

Yeah I am using the live CD of 7.10. Sorry im pretty new to Linux :-) I am just at work now but I will try that. Is there any other way to install it? I want to dual boot with WinXP.

---

### Post by ugm6hr on 2008-01-25
> **Ayrek said:**
> Yeah I am using the live CD of 7.10. Sorry im pretty new to Linux :-) I am just at work now but I will try that. Is there any other way to install it? I want to dual boot with WinXP.

There is an Alternate CD too.  But I'm not sure that would help you.

---

### Post by Ayrek on 2008-01-25
> **ugm6hr said:**
> There is an Alternate CD too.  But I'm not sure that would help you.

Ok! Well thanks for the help. Im going to attempt to repair the drive, if not ill try it on another one. Or just partition my Windows drive and install it that way.

Thanks!

---

### Post by toastysquirrel on 2008-01-25
> **Ayrek said:**
> Ok! Well thanks for the help. Im going to attempt to repair the drive, if not ill try it on another one. Or just partition my Windows drive and install it that way.

Thanks!
This isn't pertaining to the drive issue, but since you're new to Linux and going dual-boot (such as myself)  I thought I'd point out [this thread ]("http://ubuntuforums.org/showpost.php?p=4138677&postcount=3")which helped me out immeasurably when I was futzing with partitioning/setting-up my drive.

---

