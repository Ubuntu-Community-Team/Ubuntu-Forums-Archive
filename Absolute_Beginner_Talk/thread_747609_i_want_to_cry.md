---
title: "i want to cry"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by w3lshm3n on 2008-04-06
four the last couple of days i'e battleing ubuntu gutsy  i installed to try it out and i liked but for some reason it conflicts with my windoes vista. so i'm trying to uninstal it but with no remorse from GRUB. i clean up my partions and used the mbrfix in dos promt but when i reboot GRUB has a error i think it error 17 or 5 but anyways can someone help me get rid of GRUB or if i do a system recovery to the orginal factory setting will that clean this mess up

---

### Post by pseudo-random on 2008-04-06
The fixmbr command from the windows setup recovery console will overwrite GRUB.
How are you doing it exactly?

---

### Post by w3lshm3n on 2008-04-06
doing?

---

### Post by geek_Man on 2008-04-06
... How are you running fixmbr?

---

### Post by w3lshm3n on 2008-04-06
i type  "mbrfix/drive 0 fixmbr /yes"

---

### Post by wPwLUi3N on 2008-04-06
Sad ... its vista the one you should be uninstalling.

---

### Post by w3lshm3n on 2008-04-06
i do in prompt than restart ubuntu liveCD and use gparted to clean the partions

---

### Post by w3lshm3n on 2008-04-06
i wish i coud but all my stuff is on the HD and i can't get  to it to backup or save ****

---

### Post by pseudo-random on 2008-04-06
> **anuj.pathania said:**
> Sad ... its vista the one you should be uninstalling.
Agreed. However these GRUB errors seem to be the most common mistake people make when they install ubuntu. I think the entire GRUB mechanism needs overhauling if its to be really user friendly.

---

### Post by kellemes on 2008-04-06
[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/]("http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/")

---

### Post by mansell on 2008-04-06
I agree the whole grub install dual boot and partitioning thing is very scary to newbies like myself. I was successful though-but it was Windows XP & Ubuntu 7.10 I was playing with. I almost reformatted my windows install by accepting the gpart tool default setting. However my mother-in-law just got a new Compac laptop with Vista (of course) and I mentioned free OS and programs to her and he's interested so I did my research and I'm opting for a VirtualBox install inside of Vista that will run Ubuntu. This way a couple of clicks and she's back in Vista. Mainly I'm afraid of messing up her laptop. I tested out this whole plan out on my XP I'm running at home and it worked by following the virtualBox manual PDF. I would be greatly interested if anybody out there has successfully installed a dual boot Vista/Ubuntu setup. Is Vista more wiggy about this kind of thing?

---

### Post by king2007 on 2008-04-23
> **anuj.pathania said:**
> Sad ... its vista the one you should be uninstalling.

i want to cry too !! first things first - noticed ubuntu gutsy gibbon in a local store and was very interested - played around after downloading .iso and burning with Linux ! - so anxious to learn more upgraded to hardy heron and downloaded the betaversion few weeks ago already - this version 8.04 can be installed without a separate dedicated disc - okeh, it turned out to take ALL space on one disc i decided to remove it with one click of the mouse..... SHOULD not have done that !!, because the GRUB bootloader was gone as well ! now tell me how to get to my second disc with the hardy heron installed, which is NOT recognised by Vista or XP - no way you can access this disc which is physically not there to mr. gates and his staff. what i just found is Linux Reader 1.1 on this forum which is very good and SHOWS all my discs. Still, how can i create a dual-boot or triple-bootloader which can NOT be messed-up by Vista. Maybe Vista will be deleted, but then the absolute beginners talk-section should show much more howto's.....

---

