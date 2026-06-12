---
title: "kubuntu and ubuntu 7.04"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-21
right now i have kubuntu 7.04 fiesty and windows xp ,
the thing i want to do is --------------
can i install ubuntu ? , i want to keep both ubuntu and kubuntu on my pc and want to uninstall windows xp , so what should i do ?

---

### Post by armandh on 2007-08-21
I would free up some space on the hard drive leaving about 10g unpartitioned. use the install option "unpartitioned space"
boot loader should list all the operating systems. wait for other opinions first.

---

### Post by damansandhu on 2007-08-21
alright , thanks buddy

---

### Post by nosrednaekim on 2007-08-21
so.. you want a totally new installation for ubuntu? 
You know that its would probably be simpler to just use a "apt-get install ubuntu-desktop"

That is if you have enough space. if you don't you can move your /home to a new partition that you make from the windows XP space

---

### Post by damansandhu on 2007-08-21
i want to use both kubuntu and ubuntu after that command will i be able to use kubuntu?

---

### Post by schorsch on 2007-08-21
> **damansandhu said:**
> i want to use both kubuntu and ubuntu after that command will i be able to use kubuntu?
The only difference between kubuntu and ubuntu is the desktop: kubuntu uses KDE and ubuntu GNOME. So if you install the meta-package "ubuntu-desktop" as mentioned you have the choice between KDE and GNOME when you login. Everything else is the same. So why waste hard disk space with a second OS install?

---

### Post by sailor2001 on 2007-08-21
and still keep your windows on a dual boot...............It is difficult to use  10gig on kubuntu/ubuntu.... That would be almost 2000 pkgs.........whew!

---

### Post by AlexenderReez on 2007-08-21
to clear it just run in terminal

> sudo aptitude install ubuntu-desktop

log out then choose session --> gnome


you can remove it back with 

> sudo aptitude remove ubuntu-desktop

---

### Post by AlexenderReez on 2007-08-21
> **sailor2001 said:**
> and still keep your windows on a dual boot...............It is difficult to use  10gig on kubuntu/ubuntu.... That would be almost 2000 pkgs.........whew!

i havr 2767 packages installed with ofcouse i have both gnome and kde....(ubuntu and kubuntu)..and it takes only not more than 7 gig...6 something :)

---

### Post by sailor2001 on 2007-08-21
by the way. to change from kubuntu to ubunto (gnome) just ctrl/alt/backspace and at the options at lower left select sessions and pick what you want.........and I have a lot of avi's on file...

---

### Post by schorsch on 2007-08-21
> **sailor2001 said:**
> by the way. to change from kubuntu to ubunto (gnome) just ctrl/alt/backspace and at the options at lower left select sessions and pick what you want.........and I have a lot of avi's on file...
Perhaps it is better to do a clean logout than just restart the Xserver without warning ...... otherwise you can lose data and possibly damage the system .....

---

### Post by toidi on 2007-08-21
> **schorsch said:**
> Perhaps it is better to do a clean logout than just restart the Xserver without warning ...... otherwise you can lose data and possibly damage the system .....

Good advice, although I am rapidly becoming a linux freak and just love using the quick (ultra lazy) shortcuts to do things.  Also I was lucky not to ever lose anything in the last couple of weeks of doing the old ctrl+alt+backspace.

Oh and also if you install the gnome desktop to your KDE (I did it the other way round), you can then remove your KDE desktop from your install at a later date (I believe so anyway) if you prefer the GDE environment.

I might even try installing XDE at some point and removing and reinstalling my GDE just for the experience.

---

