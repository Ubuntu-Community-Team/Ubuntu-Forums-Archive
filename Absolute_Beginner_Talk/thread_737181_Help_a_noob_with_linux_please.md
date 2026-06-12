---
title: "Help a noob with linux please?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Dmarcisz on 2008-03-27
I am downloading ubuntu and will burn the ISO to a disk. But when  i put in my laptop and boot from cd will i be given an option to completely erase all my hard drive before installing ubuntu? I am asking this because i had vista instaleld but i cant boot into vista because its ****** up and says bootmgr is compressed. so i thoguht instead of installing vista i will have a go with linux. please help!

---

### Post by LowSky on 2008-03-27
dont choose linux because of a Vista error. If the laptop is under warrenty then try to get it fixed first.

If you dont mind loosing you Vista partition then install ubuntu over the entire hard drive, but I wil warn you you cant go back.

---

### Post by mikewhatever on 2008-03-27
Yes.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Dmarcisz on 2008-03-27
thanks, yah the laptop warranty ran out 10 days ago, and the recovery cd for it dont even work well, it wont install vista agen cos of a missing file and also the command prompt tells me that certain files that are supposed to be there arent :( Plus i heard linux is faster? whic hsi good cos my laptop is mainly used for internet and using the gimp

---

### Post by scramasax on 2008-03-27
> **Dmarcisz said:**
> thanks, yah the laptop warranty ran out 10 days ago, and the recovery cd for it dont even work well, it wont install vista agen cos of a missing file and also the command prompt tells me that certain files that are supposed to be there arent :( Plus i heard linux is faster? whic hsi good cos my laptop is mainly used for internet and using the gimp

I'd boot the CD live and check your hardware is supported.

---

### Post by mikewhatever on 2008-03-27
> **Dmarcisz said:**
> thanks, yah the laptop warranty ran out 10 days ago, and the recovery cd for it dont even work well, it wont install vista agen cos of a missing file and also the command prompt tells me that certain files that are supposed to be there arent :( Plus i heard linux is faster? whic hsi good cos my laptop is mainly used for internet and using the gimp

Linux is quite good, but it is also different. I hope you'll like it, but just to know what to expect, check this out [http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315).

---

### Post by twright on 2008-03-27
if vista has problems with the boot manager installing ubuntu will fix that :KS
(it installs it's own boot manager which replaces vistas and allows you to boot into both)

and if anything doesn't work in ubuntu one quick google should tell you how to fix it

---

### Post by hyper_ch on 2008-03-27
or you could just install grub on its own... that should also fix it

---

### Post by lswest on 2008-03-27
actually, Ubuntu installs GRUB, yes, but it installs it **in front** of the vista bootloader, so it would look something like this:

> GRUB-->Ubuntu
            GRUB-->Windows Bootloader--->XP/Vista

so if the bootloader is messed up for Vista, chances are you won't be able to boot after installing linux either

---

### Post by hyper_ch on 2008-03-27
Grub replaces the Windows Bootloader... at least that's how I undestand how it works

---

### Post by lswest on 2008-03-27
yes, it replaces the windows bootloader front-end that is placed in the MBR, but the required files and base of the windows bootloader must be intact to be able to load the files required for windows to boot.  (that's essentially what a bootloader does, tells the computer which files need to be booted/started) and so it works fine for Ubuntu, since it's open-source GRUB can manage the necessary files itself, or maybe it boots slightly differently than windows, i don't know for sure, but i do know for a fact, if the windows bootloader won't work due to missing files, GRUB will not fix it.  I've had that problem before, however, you can often fix it by getting to a repair console in windows and running ```
fixmbr
fixboot
``` in windows XP or ```
bootrec /fixmbr
bootrec /fixboot
``` in windows Vista

---

### Post by mrsudo on 2008-03-27
you could return the laptop because vista wasnt installed properly
or.... you could join us and use linux :)  
welcome

---

### Post by lswest on 2008-03-27
Actually, he says the warranty ran out, and so the guarantee from the store is probably long gone, meaning he can't return it.  However, he can try the commands i posted above to restore the windows bootloader, or yes, he can see the light and switch to Linux ;)

Only reason i actually have windows is because i need it for school, and as a learning experience for later in life when i plan on getting an IT-related job someplace, but it does break quite often, but once you get the hang of how to fix it, fixing it isn't that hard...Linux on the other hand, once you get it running, it runs so well that I haven't touched my PC system upstairs since Gutsy was released (i even upgraded from Feisty on that thing, and everything works great).

---

### Post by piousp on 2008-03-27
Indeed. You should be aware that  [LINUX IS NOT WINDOWS]("http://linux.oneandoneis2.org/LNW.htm").
You can always try ubuntu in the live CD form and see it for yourself.
And, if you decide to swith to the light ;), you can always haev a virtual machine with windows, just in case you really need it.

---

