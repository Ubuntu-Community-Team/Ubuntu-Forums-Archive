---
title: "Installed ubuntu but..."
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Zack88 on 2008-01-29
I installed ubuntu 7.10 and it installed fine, but it wont boot after the computer is turned on, its reaches to the spot right before you see ubuntu and the loading bar, ive install xbuntu 7.04 on the same laptop before and it ran with no problem, does anybody have a solution?

---

### Post by njparton on 2008-01-29
Can you post your hardware please? Are you running an nvidia onboard graphics chip?

---

### Post by Zack88 on 2008-01-29
no an ati onboard chip (xpress 200m) and 512 mb ram

---

### Post by Zack88 on 2008-01-29
amd mobile sempron 3300

---

### Post by njparton on 2008-01-29
Sorry, can't help as I always use nvidia with linux.  Higher quality and more mature drivers although that doesn't help you...

---

### Post by Zack88 on 2008-02-02
*update*

I went back to windows but im really wanting ubuntu so is there anybody that can help me?

---

### Post by barbedsaber on 2008-02-02
can you boot into a command line ( I can) maybe the more experinced linux users hat are around could help you if you can get to the clu.

---

### Post by Zack88 on 2008-02-02
I don't know how to, if someone wrote out the steps I could try.

---

### Post by bluewraith on 2008-02-02
Did you let it sit and chew on it for a little bit?
I had the same problem. Turns out the splash screen was trying to display in a resolution that my LCD screen didn't like. If I waited it out, it would boot to the login screen just fine.

---

### Post by archmage258 on 2008-02-02
I had a similar issue with my laptop and I figured out that it will boot when the AC adapter is plugged in but not without.  I know it sounds stupid but it worked for me.

---

### Post by Zack88 on 2008-02-02
hmmm well I let it sit for awhile but cant remember how long and I had the ac adapter plugged in at the time, like i do most times, also since i reinstalled windows (vista) i've read there are problems with dual booting with vista where it cause vista not to boot so is there a way to make this not happen?

---

### Post by archmage258 on 2008-02-02
To make vista play nice with ubuntu I had to use the vista boot loader.  I found this tutorial [here]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")   very helpful for the initial setup of the installs and has a way to try and make GRUB work with vista.  The boot section didnt work for me so I used EasyBCD to edit my vista boot loader to include ubuntu.  (this may be because the tutorial is dated)

---

### Post by Zack88 on 2008-02-02
Ok I read the tutorial, I've done that before except make vista the default os, the problem I had was I partitioned my hdd using vista's own partition manager and then i installed ubuntu then I tried booting ubuntu and after it hanging i shut down my computer then i tried booting in vista but it did the same, I guess Im going to try it again and let it run (ubuntu) for awhile last time though I think I let it run for 2 hours or more but still nothing

---

