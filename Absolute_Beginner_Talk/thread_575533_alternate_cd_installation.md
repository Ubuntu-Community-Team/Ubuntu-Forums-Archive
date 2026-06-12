---
title: "alternate cd installation"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-14
i installed my 64-bit ubuntu alternate cd becuase live would not boot to GUI but my the unbuntu intall just goes into a black screen.  anyone know of this happening?  my video card is:

NVIDIA GeForce Go 8600M GT 512MB with Turbo Cache Technology Video

---

### Post by Abild on 2007-10-14
Could you give some more information please? Have you installed ubuntu successfully and are experiencing black screen when booting (if so, at which stage does it happen?) or does the screen go black during the alternate installation?

---

### Post by RyanZec on 2007-10-14
The installation completes fine, then at boot screen i see ubuntu 2.0.15 kernal and windows vista, i selec ubntu and then my screen goes blank, the ubuntu load screen never shows.

---

### Post by overdrank on 2007-10-14
> **RyanZec said:**
> The installation completes fine, then at boot screen i see ubuntu 2.0.15 kernal and windows vista, i selec ubntu and then my screen goes blank, the ubuntu load screen never shows.

You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add vga=771 and then hit enter and then  b to boot. Hope this helps. Good luck!

---

### Post by RyanZec on 2007-10-14
well i have some new information.  have i select ubunut from boot loader and my screen goes black a noise will play.  i then press my power button and then the normal boot screen for ubuntu(the one that list stuf will ok to the right)  it then say nm_loader(something like that screen goes away to fast to me to catch it all)  error code 15.

---

### Post by RyanZec on 2007-10-15
to you guys think the gusty gibbon might have better support for my hardware than 7.04?

---

### Post by overdrank on 2007-10-15
> **RyanZec said:**
> to you guys think the gusty gibbon might have better support for my hardware than 7.04?

Hi I am using Gutsy now on a nvidia machine and it works great but there are a few things that have to be tweaked like in feisty. If you still have Feisty installed we can try and get that going and then you go from there. You an try and boot to recovery mode and reconfigure your xorg from there and hopefully get you to the desktop
Boot into recovery mode and then you can use these commands, enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and choose vesa as the driver then answer a few questions, If you do not know the answer leave the default answer given.When complete use the command to reboot ```
reboot
``` Hope this helps and good luck!

---

### Post by RyanZec on 2007-10-15
do you mean resuce an installation mode?

i tried that but wne i tried to run sudo dpgk-reconfigure it tells me that is not a command.

---

### Post by overdrank on 2007-10-15
> **RyanZec said:**
> do you mean resuce an installation mode?

i tried that but wne i tried to run sudo dpgk-reconfigure it tells me that is not a command.

Hi and no I mean on your installation, You said you had it installed by the alternate cd and you could choose from vista or ubuntu. There is a recovery mode in the grub it should be the second choice on the grub.

---

### Post by RyanZec on 2007-10-15
ah.  I never actually read what the second ubuntu option was.  I will try that when i get home and let you know how it goes.

---

### Post by eldepeche on 2007-10-15
> **RyanZec said:**
> do you mean resuce an installation mode?

i tried that but wne i tried to run sudo dpgk-reconfigure it tells me that is not a command.

dpkg-reconfigure is the correct command. 2 points off for spelling errors :)

---

### Post by RyanZec on 2007-10-15
when i try that command my screen goes blank and then i get a warning saying that the xorg file might be overwritten and that is made a back and then the prompt again, no options or anything.  it did not even ask for a password.

---

### Post by overdrank on 2007-10-15
> **RyanZec said:**
> when i try that command my screen goes blank and then i get a warning saying that the xorg file might be overwritten and that is made a back and then the prompt again, no options or anything.  it did not even ask for a password.

Hi and yes I just use that command I gave you and it did the same thing. In Gutsy  are you sure you did not install gutsy. But it did configure my graphics card which is a ati.

---

### Post by RyanZec on 2007-10-15
> **overdrank said:**
> Hi and yes I just use that command I gave you and it did the same thing. In Gutsy  are you sure you did not install gutsy. But it did configure my graphics card which is a ati.

i installed 7.04

---

### Post by RyanZec on 2007-10-16
anyone else have any other thoughts?

---

### Post by RyanZec on 2007-10-17
i will just try 7.10, maybe it has better hardware support for my video card.

---

### Post by RyanZec on 2007-10-18
I have tried 7.10 and same result.  i tried sudo dpkg-reconfigure -phigh xserver-xorg and all it tells me is that it created a backup but it does nothing.  anything else i can tried to get my video card to work?  again my video card is a 8600M GT 512MB

---

### Post by RyanZec on 2007-10-19
Well i have managed to change the driver from "nv" to "vesa" but my screen still turns off when i try to boot into ubuntu 7.04 64-bit

---

