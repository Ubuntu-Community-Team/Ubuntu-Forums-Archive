---
title: "Vmware/Virtualization Ubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Kur5678 on 2008-01-24
Hello all, I've used Ubuntu in the past mostly dual booting a few of my PC's. I like the OS, but often find I have to log into Windows XP to do certain things. 

Yesterday, a coworker brought his PC into work, to try and have me and another fix it. He contracted a nasty, NASTY virus on his windows xp pro machine. It came in through his web browser as a plug in, and reproduces itself each time he reboots his machine. He has spent over 30 hrs. now trying to fix the problem, with no success. Ultimately he is going to have to wipe his hard drive and reinstall. 

A few questions: 

[B]I'm thinking of running Linux on all the PC's in my home, and booting Windows xp in a virtual machine. I've heard doing this, that ultimately no harm can come to your PC via windows security holes, as its an OS running in a closed off box basically. Is this true?
[/B]
**[B]Also, how functional is your windows xp virtual machine? I know I can do most of the tasks with the virtual machine, but has 3d come further in Vmware, and the other Virtualization products out there? Is running 3d games in Virtualization still questionable, and it makes more sense to just boot into a .exe machine to run windows games?**[/B]

I dont mind dual booting, but with all the holes with Microsoft products, I'd really like to stop having Windows as my main OS, and switch full time to a more secure OS. 

Thanks in advance for any advice/help!

Matt.

---

### Post by nonewmsgs on 2008-01-24
i would dualboot at least one machine with win2000/xp, because 3D games really dont work well in virtualization.

what i do is i have my linux machine and on the other side i have my dualbooting machine.  i have had issues with just setting up vmware and while virtualbox is easy to set up, it straight out won't run any 3D apps and i have had some issues,

---

### Post by emarkd on 2008-01-24
I can tell you that, in my experience, VMWare won't do DirectX at all.  Everything else runs great.  I can even run Visual Studio, the most bloated hog of an IDE ever, at full-speed in VMWare.

I haven't played with VirtualBox much, but according to nonewmsg above, it won't work very well either.

I think you're still going to be booting into Windows for games.

---

### Post by Kur5678 on 2008-01-24
Thanks much for the info ; )

---

### Post by alxlabs on 2008-01-24
You may want to consider Wine. This is not an emulator, but environment to run Windows applications under Linux. From my experience - every other application works, at least as I was able to run my favorite games (3d and opengl) except one.

---

