---
title: "Help with booting 7.10"
date: 2008-03-28
forum: Apple PPC Users
---

### Post by crapple on 2008-03-28
Here is my problem I just installed Ubuntu 7.10. but when I try to boot it dose fine till the page with ubutu and the loading bar. When the bar gets about 1/15 of the way it freezes and then goes to the busy box 
I have a g4 processor and 789mb of ram.   According to the download page it should be able to run on my computer.  This also happend when I tried to update from 7.4 to 7.10.  So I decided to try a fresh install.
Any Ideas?

---

### Post by avtolle on 2008-03-28
crapple, at the busy box prompt, type ide-core, and hit enter; at the next prompt, type exit. Your boot will then continue. I'm not at a place where I can access my notes to tell you the rest of this fix, but there are other threads on this problem.

Good luck.

---

### Post by crapple on 2008-03-28
When I portioned the disk I selected use entire disk guided portion.

---

### Post by crapple on 2008-03-28
It tells me ide-core is not found or something like that

---

### Post by avtolle on 2008-03-28
crapple, my bad; first line should be modprobe ide-core. 

(Memory isn't what it used to be, I fear. :-( )

---

### Post by avtolle on 2008-03-28
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) will give you some further information and assistance, too. Good luck.

---

### Post by crapple on 2008-03-28
When I do that it goes through a bunch of things and then the screen goes black

---

### Post by avtolle on 2008-03-28
crapple, yes it does; it stays black for a bit, the precise length of time dependent upon various factors. On my cube, I didn't time it, but after executing the commands in busy box, it went black; then a bit later, a white screen appeared; then back to black, then a graphic came on, and then eventually finished booting. I don't know how long you waited at the black screen before aborting (I presume) the process. I'd try it again, and see what happens. I'm an impatient person myself.

If it doesn't continue to boot, then look at some of the boot options listed in the link I posted earlier. I didn't need any of them; others have.

Again, good luck.

---

### Post by crapple on 2008-03-29
It is now giving me a bunch of device lookup failed.  Also I can hear it but all I see is a blank screen.  The imac g3 thing isn't for my computer because mine is emac g4.
Also will 8.4 have these "bugs" fixed?

---

### Post by ssam on 2008-03-29
> **crapple said:**
> It is now giving me a bunch of device lookup failed.  Also I can hear it but all I see is a blank screen.  The imac g3 thing isn't for my computer because mine is emac g4.
Also will 8.4 have these "bugs" fixed?

8.04 seems to be a big improvement over 7.10 on my titanium powerbook G4 1GHz

---

