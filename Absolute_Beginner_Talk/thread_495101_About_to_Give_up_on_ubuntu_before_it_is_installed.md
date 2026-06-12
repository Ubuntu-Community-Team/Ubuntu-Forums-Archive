---
title: "About to Give up on ubuntu before it is installed"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by cknightfl on 2007-07-07
Alright here is my situation.  I have never used linux or ubuntu.  I tried to download the v7 amd 64bit version. When i go to install it, the installer stops normaling when it says loading drivers.  I post a tread and people said to try the 32 bit.  I just got done dling it and went to install.  Made it past the 64bit version but goes to a screen that fades black and does nothing.  I have verified both cds from the menu.  

I have a a hp dv9038nr with vista currently installed.  I am atempting to dual.  

[http://www.bestbuy.com/site/olspage.jsp?skuId=8294268&type=product&productCategoryId=pcmcat103700050028&id=1172880155501](http://www.bestbuy.com/site/olspage.jsp?skuId=8294268&type=product&productCategoryId=pcmcat103700050028&id=1172880155501)

I am following this tortorial

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I would appreciate any help or ideas you guys could offer
Thanks in advance

---

### Post by vexorian on 2007-07-07
I would either wait for another version to be released or try daper (LTS) instead of 7.04 , if live-cd is having issues I recommend against installing even if you figure out how to make it work.

---

### Post by atria on 2007-07-07
Weird the 64-bit version didn't work. In any case did you try booting the 32-bit version in safe graphics mode (second boot option) ?

---

### Post by cknightfl on 2007-07-07
I have not used graphics safe mode... what does that do

---

### Post by phidia on 2007-07-07
I think it would  be helpful to have all the system specs i.e video card in particular. If both the 32 & 64 bit versions are failing theres a good chance this is a video or other hardware problem. Knowing the hardware details gives the forum more info to work with. 
Do whatever feels best for you, as far as giving up goes, but if you stay with it long enough to figure it out you might be glad you did.

---

### Post by cknightfl on 2007-07-07
I posted a link to the best buy page with my laptop, it has all the specs.  I dont want to give up, just fustrated.

---

### Post by atria on 2007-07-07
> I have not used graphics safe mode... what does that do
If i remember correctly it forces your computer to boot with the generic vesa graphics driver.

---

### Post by cknightfl on 2007-07-07
and than would i download the nvidia drivers (type of video card i have)

---

### Post by cknightfl on 2007-07-07
Tryed the graphics safe mode on the 32bit version.. It goes to the same screen as before and did a similar thing just the screen was a little lighter

---

### Post by TheExplorer on 2007-07-07
Try to boot using the option 'noapic' without the quotes. (having selected from the boot menu something like 'Start live CD and install' you should type 'e' on the keyboard. You'll see the line of code. Just add the word 'noapic'. Press enter and then 'b' letter.)

---

### Post by macogw on 2007-07-07
What graphics card is it, specifically?  All you said is "Nvidia" but there are TONS of Nvidia cards out there.  If it's supported it'll be listed here [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

If it's a very new card, you'll need to get the drivers from nvidia.com and follow this [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) If it's

---

### Post by TheExplorer on 2007-07-07
I had this issue. Still can't find the solution for it. 'Noapic' switches off some apic/acpi support if I'm not mistaken. I've got AMD64. Still strange for me.

---

### Post by cknightfl on 2007-07-07
The noapic worked... What does that do and do you think it will be safe for me to install fully

---

### Post by macogw on 2007-07-07
TheExplorer, apci and apic are different things.  APCI is for power management (like hibernate and suspend). 

APIC is "Advanced Programmable Interrupt Controller" which I gather has something to do wtih the way the kernel handles hardware interrupts and seems to make its handling more complex. Disabling it just simplifies how interrupts are handled.  It's perfectly safe to do.  Certain Nvidia cards get black clouds if you don't do it (that's what one of my friends' did).

---

### Post by TheExplorer on 2007-07-07
Glad that it helped you. You should also add 'noapic' to the menu.lst in your /boot/grub directory.

P.S. If you really can give up on installing the OS then you are simply unable to google, man :) Read man-pages, use google and you'll be lucky.
Btw, try to find anything amd64 apic related and PM me here.

---

### Post by cknightfl on 2007-07-07
that must have been what i had than because it sounds like what i was seeing... Thanks so much to everyone

---

### Post by macogw on 2007-07-07
To make sure that the boot option is added every time you get a kernel update,
> sudo gedit /boot/grub/menu.lst
and when you find this line:
> 
# defoptions = quiet splash
change it to
> # defoptions = quiet splash noapic
save it, then run
> sudo update-grub

---

### Post by TheExplorer on 2007-07-07
I think it is an nvidia-amd64 interrupt releated bug in Ubuntu since it has a lot of bugs unfortunately.

---

### Post by macogw on 2007-07-07
No, my friend had the problem with both 64-bit and 32-bit.

---

### Post by TheExplorer on 2007-07-07
I mean: Nvidia + amd64 and Ubuntu (whether x86 or x64). Just the mixture of them and Ubuntu itself. I dunno. Maybe :)

---

