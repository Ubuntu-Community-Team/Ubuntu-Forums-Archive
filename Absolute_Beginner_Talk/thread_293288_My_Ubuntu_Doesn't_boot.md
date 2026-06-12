---
title: "My Ubuntu Doesn't boot"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by hsingarajah on 2006-11-05
hi.  I'm running a 650Mhz PIII, with 300 Megs of RAM. I Allocated 10 gigs  of ext3 for linux with about 512MB for swap.  

I tried running Ubuntu's live disc (the one they ship) but after it load components it freezes.  (Right after Enterprise Volume Manager) - the screen clears and the flashing cursor appears on the blank screen. Then it just freezes and doesn't work.

I downloaded the alternate disc and installed it- the installation was successful but it freezes JUSt like it did before!  I'm not sure what the problem is - it doesn't even give an error message or at a specific point, it just freezes after all the components have loaded. 

Please help!

---

### Post by HereInOz on 2006-11-05
Try installing on a different hard disk, if you have one.  Had the same trouble and eventually it came down to a HDD that checked fine, would format as FAT32 no worries, it looked like it was doing the job, but was indeed the source of the trouble.

Also swap your RAM if you can, and also try a different video card.  

Hopefully you have some of these as spares.

---

### Post by hsingarajah on 2006-11-05
I have absolutely NO spares, and no money to buy new stuff. Oh yea my video card is 16MB Nvidea thing I bought used for $20. It works find with everything else so that must not be the problem

Fedora Core 4 worked fine for me when I installed it last year.  The only reason I'm installing Ubuntu is beccause I reinstalled Windows Xp and that wrote over the MBR and erased grub, and I didn't bother to get it replaced. So recently my friend told me to install Ubuntu. ..

Should I just reinstall Fedora Core?

---

### Post by taurus on 2006-11-05
Do you have a network connection?  Try downloading the alternate CD since it would work better if you plan to install Ubuntu on your machine.

---

### Post by hsingarajah on 2006-11-05
Actually i tried the alternate disc. I mentioned that in the original post.   At this point the system installs, but it doesn't boot. IT just freezes after everything is loaded.  Again, another distro (Fedora Core) worked exactly the same way it was installed. I have a master drive( where windows resides) and a slave (where linux resides) and Fedora COre 4 worked perfectly on that.

---

### Post by hsingarajah on 2006-11-07
*bump*
Please?  Is it possible to put some flags when I boot from the command line so takethings off so it will boot?  IF it is possible what do I put and how do I do it?

---

### Post by hsingarajah on 2006-11-07
Bump again????

---

### Post by hsingarajah on 2006-11-08
> **hsingarajah said:**
> Bump again????

Again?

---

### Post by drtvasudevan on 2006-11-08
> **hsingarajah said:**
> Again?

your system is more or less similar to my old one.
perhaps not enough muscle?
but you say you could install fedora..
try xubuntu or one of the lighter distroes like zenwalk?

you are dual booting right?
what method are you following?
where did you put the bootloader -grub or lilo

just trying to follow some random thoughts since you have had no replies otherwise..

---

### Post by hsingarajah on 2006-11-09
Hey thanks for the reply, I seriously appreciate it.

I hadnt' thought of the xubuntu.

I have the bootloader (grub) on the master harddrive (which I installed XP on).  I think I *just* meet the requirements for ubuntu, but I'm sure it shoudl work.    I heard there is a way to take out some of the options when booting to lighten the load - like turning off services or booting form the command line with certain flags.  Do you know anything like that, and/or how to do it?

---

### Post by drtvasudevan on 2006-11-10
> **hsingarajah said:**
> Hey thanks for the reply, I seriously appreciate it.

I hadnt' thought of the xubuntu.

I have the bootloader (grub) on the master harddrive (which I installed XP on).  I think I *just* meet the requirements for ubuntu, but I'm sure it shoudl work.    I heard there is a way to take out some of the options when booting to lighten the load - like turning off services or booting form the command line with certain flags.  Do you know anything like that, and/or how to do it?

oh.sorry.
i am relatively a newbie.
i understand applications etc.
nothing technical.
there is a way to do what you are asking in system>services but then you must first be inside.
i dont know abt boot parameters to turn off services.

---

