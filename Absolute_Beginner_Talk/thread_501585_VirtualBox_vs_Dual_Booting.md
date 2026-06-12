---
title: "VirtualBox vs Dual Booting"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-15
I am a bit confused about what exactly Virtualization software like VirualBox does...

I ask because I might have to set up a dual boot system, with Ub on it right now and with XP as the addition. Should I just install XP from another drive, or is it just as easy to run it inside VirtualBox? Cause I dont want XP messing around with the bootloader or stuff like that...

Like I said, first and foremost what is the purpose of such software...

---

### Post by oilchangeguy on 2007-07-15
> **FleetAdmiral74 said:**
> I am a bit confused about what exactly Virtualization software like VirualBox does...

I ask because I might have to set up a dual boot system, with Ub on it right now and with XP as the addition. Should I just install XP from another drive, or is it just as easy to run it inside VirtualBox? Cause I dont want XP messing around with the bootloader or stuff like that...

Like I said, first and foremost what is the purpose of such software...

one thing to consider, virtual machines are only allocated a small portion of the computers resources. whereas a dual boot setup allows each os to take advantage of the computers full resources. i run a dual boot with xp pro on another drive. but it still shows up in grub, there's no way around this, and there's nothing wrong with it. if you do it correctly. and virtual software allows you to run several os's on your computer. and they all can run at the same time if you desire.

---

### Post by Nythain on 2007-07-15
not sure but i think you might also encounter graphics driver issues on a virtualized install of xp... either that or it was the other way around and people were encountering graphics driver problems with a wubi install of ubuntu in xp...

if you have the system resources i would advice virtualization, no need to reboot to switch... and if you follow a few cool guides you can even get it integrated pretty well... and if you happen to have dual monitors its even cooler cause you can run a virtualized xp on one monitor and everything else on another

but if you dont have an up to par system, i would suggest dual boot so you can get the full extent of your hardware out of each os

---

### Post by freebird54 on 2007-07-15
Mostly it depends on what you want to run in XP.  If it is graphically intensive (ie: games) you lose too much by virtualizing it.  If it is editing, or business purposes, or anything not really bound by system speed then VirtualBox is a pretty neat solution, and doesn't require rebooting all the time.

As for putting XP on second, re-installing Grub is a pain, but not that difficult -and good guides abound.

What I've found (having both options on this machine) is that I just don't use Xp much any more :)

---

### Post by Nythain on 2007-07-15
yeah, i dual booted for a few days... and then i realized i went a few days without ever loading windows so i nixed that waste of space... wine has been a blessing to me at first, but now i dont even use it... all native all the way... but im not a major gamer or graphic designer or work for a multi million dollar corporation and need that true MSOffice ability so giving up world of warcraft, photoshop, and office wasnt to tough

---

### Post by gn2 on 2007-07-15
> **FleetAdmiral74 said:**
> 

Like I said, first and foremost what is the purpose of such software...
.
In simple terms, the purpose of Virtual PC's is to allow you to run two operating systems on the same PC at the same time.
.
You have a "Host" Operating System and a "Guest" operating system. 
The "Guest" virtual PC can run in a window or full screen.
As an example here's a picture of a Windows guest running inside a Mac OSX host: [http://www.vmware.com/files/images/product_shots/vmware_on_macosx_large.png](http://www.vmware.com/files/images/product_shots/vmware_on_macosx_large.png)
.
The major limitation of a "virtual" PC is the lack of 3d support, so you can't run games or 3d applications in a virtual PC.
.
You also need lots of RAM to run both OS's at the same time, say 512 for Ubuntu and another 512 for Windows, you also need a reasonable CPU, the lowest CPU I had success on was an Athlon 2100XP
.

---

