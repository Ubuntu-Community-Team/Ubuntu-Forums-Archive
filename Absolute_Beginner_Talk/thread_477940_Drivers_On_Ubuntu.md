---
title: "Drivers On Ubuntu?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Elias~ on 2007-06-18
Hi, I was recently attempting to install the latest ATI Drivers on my computer.

I found a program call Envy.  I tried it but it doesn't work.  It cannot find any suitable drivers for my card. 

My card is: Radeon Mobility U1 (Radeon IGP 320M)

Can anyone help me find the correct drivers?

---

### Post by smoker on 2007-06-18
hi, i don't have an ati card, but i found this thread that may help you:
[http://ubuntuforums.org/showthread.php?t=81547](http://ubuntuforums.org/showthread.php?t=81547)

best of luck

---

### Post by starcraft.man on 2007-06-18
> **Elias~ said:**
> Hi, I was recently attempting to install the latest ATI Drivers on my computer.

I found a program call Envy.  I tried it but it doesn't work.  It cannot find any suitable drivers for my card. 

My card is: Radeon Mobility U1 (Radeon IGP 320M)

Can anyone help me find the correct drivers?

[3 Guides to manual install of ATI drivers. ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29")Try them. I can only point you to them though, I'm an nvidia man through and through. I don't even know if that line is supported... best of luck with it. I usually recommend Envy to get these in but if it failed then I guess manual is the only way (assuming they are supported, might want to check ATI site to be certain).

---

### Post by Elias~ on 2007-06-18
Okay, Thanks guys.

---

### Post by w4ett on 2007-06-18
Here's installation instructions for your specific card:

[http://ubuntuforums.org/showthread.php?t=310018&highlight=Radeon+IGP+320M](http://ubuntuforums.org/showthread.php?t=310018&highlight=Radeon+IGP+320M)

They're pretty complete and seem to be just what you need.  

Good Luck,,,,Check back with any questions you might have.

---

### Post by Elias~ on 2007-06-18
Uh, I think you posted the wrong link... =X

---

### Post by w4ett on 2007-06-18
Sorry...put the wrong link.....Long day :)

---

### Post by Elias~ on 2007-06-18
Uhh this already shows for me.

elias@elias-laptop:~$ glxinfo | grep direct
direct rendering: Yes
elias@elias-laptop:~$


Without doing all that stuff.

---

### Post by w4ett on 2007-06-18
Yes...that should be using the open source ATI driver.  If you read further FGLRX will not install with that chipset, but with a couple tweaks, you can us AIGLX and get Beryl to work.

---

### Post by Elias~ on 2007-06-18
Beryl desktop enviorment alreadyworks for me.  Is that what your talking about?

---

### Post by w4ett on 2007-06-18
Yep....well  if Envy can't give you an alternate driver, and you got Aiglx and Beryl working with no problems,  then you should wait and see if the new drivers from Xorg (coming out in Gutsy, I believe) give you any better 3D rendering.

---

### Post by Elias~ on 2007-06-18
Weird...  When useing beryl I get the "Black Window Bug" that NVidia users get when useing blur.

---

