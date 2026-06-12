---
title: "Drop to root shell prompt."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by LibertyShadow on 2008-03-12
Earlier I installed updates on Ubuntu 8.04 Alpha 6, and apparently updated the kernel.  I overlooked that by accident. I am using the proprietary driver (version 169.12) from Nvidia for my GeForce Go 7300, and each time I update the kernel I have to recompile the nvidia kernel module.    

So the next time I booted, I got the notification that I was running in low graphics.  It provides 3 options:  Configure; Shutdown; Continue.  I wanted to shutdown and end gnome so I could update my kernel headers and run the nvidia installer from the terminal.  When you click shutdown, you are given the option to "Drop to Root Shell Prompt."   ---?  

I may just be paranoid, but doesn't this give root access privileges the user without ever entering a password?  

Anyway, everything is working now, I just wanted to bring that up and see what the community has to say about it.  ....I mean anyone could have turned on my computer and had root access at that point.

---

### Post by justsomedude on 2008-03-13
> 
I may just be paranoid, but doesn't this give root access privileges the user without ever entering a password? 

Yes. 

You can use grub-md5-crypt to set a password though. 

On the other hand, it's debatable if that really protects your system from unwanted access.

---

### Post by lloyd_b on 2008-03-13
> **LibertyShadow said:**
> Earlier I installed updates on Ubuntu 8.04 Alpha 6, and apparently updated the kernel.  I overlooked that by accident. I am using the proprietary driver (version 169.12) from Nvidia for my GeForce Go 7300, and each time I update the kernel I have to recompile the nvidia kernel interface.  ( I don't fully understand that :) )  

So the next time I booted, I got the notification that I was running in low graphics.  It provides 3 options:  Configure; Shutdown; Continue.  I wanted to shutdown and end gnome so I could update my kernel headers and run the nvidia installer from the terminal.  When you click shutdown, you are given the option to "Drop to Root Shell Prompt."   ---?  

I may just be paranoid, but doesn't this give root access privileges the user without ever entering a password?  

Anyway, everything is working now, I just wanted to bring that up and see what the community has to say about it.  ....I mean anyone could have turned on my computer and had root access at that point.

Uh - you *do* realize that anyone can turn on your computer, hit ESC at the "Loading Grub" screen, select a "Recovery Mode" entry, and they'll have a root shell on the machine without entering a password?

Or if you close that door, they can boot from an install CD, and from there boot into a root shell?

Simple fact is that if a person with a sufficiently high clue-factor has physical access to your machine, he/she can get a root shell.

Lloyd B.

---

### Post by LibertyShadow on 2008-03-13
I guess it's a good thing I have a bios password, then :D

My clue factor is a bit low in the Linux dept, as you can tell.

---

### Post by tubasoldier on 2008-03-13
It is extremely easy to get root access on Ubuntu when you are physically at the machine. However, if root has it's own password then it is much harder. With Ubuntu's use of sudo a password is never really set for root... one of the disadvantages of sudo.

---

### Post by PeterJS on 2008-03-13
> **tubasoldier said:**
> It is extremely easy to get root access on Ubuntu when you are physically at the machine. However, if root has it's own password then it is much harder. With Ubuntu's use of sudo a password is never really set for root... one of the disadvantages of sudo.

Let's be fair, it's easy to get root on any machine* when you have physical access. There's no way to stop some one from gaining access, the best you can hope for is strong full disk encryption that will slow them down a few years. But if you've got physical access to a machine, you can always boot it to a liveCD. Ok, so you can counter that with a BIOS password, and physical access can overcome that as well, just crack the case, pull the CMOS battery, give it a 30 count, and the BIOS password is gone, and then it's back to the liveCD. Long story short, there is no digital security without physical security.

*And I do mean any, with physical access you can even get root access on a windows box that doesn't even have a root account with a liveCD.

---

