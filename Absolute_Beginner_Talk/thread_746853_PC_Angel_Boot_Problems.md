---
title: "PC Angel Boot Problems"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by NR1224 on 2008-04-05
I have an eMachines(T3516), and have installed ubuntu via wubi. I would like to transfer to a partion but am having some problems. ~6 months ago i tried to install Sabayon, and when i tried to boot windows, a previously unknown program to me(PC Angel), locked me out and i had to reformat. After some googleing, i found that pc angel is a recovery program used to "save" crashed hard drives. I have recently aquired a new hard drive and need to know if there is any way to remove pc angel, or if there was any way around the software. I have already searched and found nothing, and i apologize if this is in the wrong section, but any help would be appreciated, thanks

---

### Post by mrpixels0 on 2008-04-06
since it is an OEM machine it should have a recovery partition that came with it from the factory, you could look there and see if it is there. if so find it and don't delete it just rename it to something else.

for example if it is named say "pcangel.exe" then rename it "pcangel.old" and since it is renamed is should not be able to execute. or you could go in to windows startup files and REM out it's boot config for it.

then when your done undo the changes when your done and that should be that, that way if you ever need to recover windows for some reason you still have the needed programs and partition to do it with.

hope this helps

MP0

---

### Post by NR1224 on 2008-04-06
ya, that explains it, i thought i had seen something similar about it somewhere else, thanks. But just to be safe, how do i go about changing the windows boot loader? Can i do it from system properties or to i need to directly edit boot.ini?

---

### Post by mrpixels0 on 2008-04-06
you can edit the boot.ini, but i suspect that pc angel sees what is going on in some form TSR (Terminate and stay resident program) so if you feel comfortable doing so use Gparted and KIll the partition the that it lives on and you will be troubled no more. but by doing so you may not be able to restore windows properly if things go wrong with windows on down the road later.

MP0

---

