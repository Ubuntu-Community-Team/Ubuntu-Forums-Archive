---
title: "installed wrong version of ubuntu... what next?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by cus1984 on 2008-02-15
hi all, i am an absolute beginner to linux, liked the look and fed up of XP so i downloaded  ubuntu-7.10 i386. I successfully installed the OS but when i got there the desktop was frozen, i then quickly came to realise that i do need the i386 version as i have an athlon 64 processor :( 

I have windows XP running on the same machine and I am currently downloading the correct version of Ubuntu (not the live versions btw). 

What  I would like to know is how do i go about deleting the previous Ubuntu installation, do i need to re-partition, is there a repair option etc

what should i do first??? 

Thanks

---

### Post by arashiko28 on 2008-02-15
Hi, before you do the change, try to find out the cause of the freezing, because it's not usual. And the 64bit version has some applications that are still in development. If you still want to install the 64bit version all you have to do is select manual partitioning and then, the same partition of Ubuntu and format it, then you reinstall Ubuntu on the empty partition. Nothing weird nor extravagant. Good Luck!

---

### Post by firefly76 on 2008-02-15
If I recall correctly the installation will ask you to re-partition and reformat, which apparently you want to do.

---

### Post by cus1984 on 2008-02-15
thanks that sounds simple enough. As for the freezing, i logged on easily enough to the desktop, but then i couldn't select anything and there were jagged lines going through the screen etc. Thought it may be a driver problem, though i just presumes the wrong version of ubuntu was installed

---

### Post by rbprogrammer on 2008-02-15
> **cus1984 said:**
> 
...
... and I am currently downloading the correct version of Ubuntu (not the live versions btw). 
...

just to help further your understanding, the live versions are the same iso cd-images as the ubuntu install iso cd-image.  the only thing that makes it "live" is the fact that the cd is bootable.  meaning, the cd-image, when written to a cd, will have the option to install ubuntu after you load the "live" part.

---

### Post by cus1984 on 2008-02-15
that does help tbh.. thanks

download has just finsished, gonna try it out now :)

---

### Post by rbprogrammer on 2008-02-15
> **cus1984 said:**
> thanks that sounds simple enough. As for the freezing, i logged on easily enough to the desktop, but then i couldn't select anything and there were jagged lines going through the screen etc. Thought it may be a driver problem, though i just presumes the wrong version of ubuntu was installed

the jagged lines don't necessarily mean its the wrong version.  chances are, if you did have the wrong version, the installation process would not have begun.  b/c the architectures are different, you would not be able to execute the installation instructions, therefore, not allowing you to install ubuntu.

my though is that you *probably* have an x-org configuration problem.  and helping you with that is way out of my expertise.  what might help is, did you build the computer yourself?? if so, what parts did you use.... if not, what computer did you buy??  eg, a dell model, compaq, sony, etc...

---

### Post by cus1984 on 2008-02-15
yes i did build the computer myself.

Amd athlon 64, 3200+
EVGA k8n nf41 mobo
1gb ddr ram
7800gt 256 ram

primary hd IDE 120gb
secondary hd 250 gb 

ubuntu was installed on the primary hard drive in the free available space left over from an XP installation.

---

### Post by cus1984 on 2008-02-15
im assuming that 'x-org' is the options screen at boot-up asking for the chioce of operating system, where i can still boot into windows from the windows NT/200/Xp option.

Would you reccomend installing ubuntu on the secondary hard drive....
the 250bg on the drive is all free.

---

### Post by crazycaveman on 2008-02-16
x-org is actually the gui interface (the one that lets you log in and gives you all the jagged lines)  It appears to me that there might be a problem with the video driver and not the architecture (as others have mentioned, as well).  The boot up screen, where you can select the OS is actually run by GRUB (don't ask me what it stands for...) and installing Ubuntu on your primary HDD with XP is fine, I have my computer set up the same way.  As for the driver problem, I would advise you to search around the forums and the net to find out more.  I'll poke around as well and see if there's anything I can find that'll help you.  You might not have to reinstall, just tinker a little.

[edit]
you can check this out and see if it works:
[http://ubuntuforums.org/showthread.php?t=696787](http://ubuntuforums.org/showthread.php?t=696787)
I hope this helps you some, and if you ever need anymore help, don't hesitate to ask.  We love to help out where we can!
[/edit]

---

