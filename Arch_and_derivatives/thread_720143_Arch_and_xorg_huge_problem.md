---
title: "Arch and xorg huge problem"
date: 2008-03-10
forum: Arch and derivatives
---

### Post by chris4585 on 2008-03-10
I have gotten just about everything setup good except for xorg, i fallowed the beginners guide, very helpful, but not as helpful as humans can be, this has been very frustrating for me.

Ok, i installed my intel video driver, created my xorg.conf file, edited it, and it works but only during the installing session, meaning after i reboot for the first time after installing arch, xorg wont work anymore, i get

Fatal server error:
lockup

any help? i've reinstalled arch twice and get the same both times..

---

### Post by TheOrangePeanut on 2008-03-10
Have you tried using the VESA drivers?  Edit your device section to use vesa drivers instead of Intels.  If it doesn't crash with vesa drivers, we have a better idea of where the problem lies.

---

### Post by Rumor on 2008-03-10
> **chris4585 said:**
> I have gotten just about everything setup good except for xorg, i fallowed the beginners guide, very helpful, but not as helpful as humans can be, this has been very frustrating for me.

Ok, i installed my intel video driver, created my xorg.conf file, edited it, and it works but only during the installing session, meaning after i reboot for the first time after installing arch, xorg wont work anymore, i get

Fatal server error:
lockup

any help? i've reinstalled arch twice and get the same both times..

Correct me if I am wrong, but it sounds from your post as if you are installing Arch and once the install is done, you are then installing Xorg and your video drivers without rebooting in between these two things? If so, you need to boot into your new Arch install before you begin to build on it.

---

### Post by finferflu on 2008-03-10
Hmm... does your video card need a module to be loaded? That seems the problem to me, since X starts fine before reboot. Eventually, after reboot, the module isn't loaded, so it brings up an error. 
So be sure to add the needed modules to your MODULES array in /etc/rc.conf.

---

### Post by chris4585 on 2008-03-10
> **Rumor said:**
> Correct me if I am wrong, but it sounds from your post as if you are installing Arch and once the install is done, you are then installing Xorg and your video drivers without rebooting in between these two things? If so, you need to boot into your new Arch install before you begin to build on it.

that is incorrect, i reboot after i get the base installed, and also.. i tried the vesa driver before this post, it was a no go

---

### Post by chris4585 on 2008-03-10
> **finferflu said:**
> Hmm... does your video card need a module to be loaded? That seems the problem to me, since X starts fine before reboot. Eventually, after reboot, the module isn't loaded, so it brings up an error. 
So be sure to add the needed modules to your MODULES array in /etc/rc.conf.

what module would that be? i had a feeling i had to do something with the modules in rc.conf but i didnt know what it was the video driver was xf86-video-intel if that matters any

thanks for the help peeps =)

---

### Post by finferflu on 2008-03-10
What's your video card model?

---

### Post by chris4585 on 2008-03-10
VGA compatible controller: Intel Corporation 82810 (CGC) chipset Graphics Controller

intel is what i went with

---

### Post by finferflu on 2008-03-10
After a brief googling it seems you need the module i810 to be loaded. Try to do a:
```
modprobe i810
``` 

as root, and try to start X.

**Edit:**
Ah, nevermind. I didn't read properly. I haven't got an Intel card, so I don't know much...

---

### Post by fwojciec on 2008-03-10
If "intel" driver is acting up you can always try the "i810" driver.  My old laptop, for example, didn't really like the intel driver at all.

---

### Post by chris4585 on 2008-03-10
woot woot woot!!! thank you, that worked, i had to start gdm under root, i'll look up how to fix that later, but it worked, i added i810 under my modules and ran gdm under root and it worked! thank you so much, i tried irc but #xorg and #archlinux i didnt get much help on freenode

---

### Post by finferflu on 2008-03-10
Ah well, I got it right even thinking I was wrong :P
That's all good :D

---

### Post by chris4585 on 2008-03-10
> **finferflu said:**
> Ah well, I got it right even thinking I was wrong :P
That's all good :D

thanks a bunch, now i need to configure my network lol

---

