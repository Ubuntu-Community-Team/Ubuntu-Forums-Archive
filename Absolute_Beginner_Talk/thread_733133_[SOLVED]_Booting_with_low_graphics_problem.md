---
title: "[SOLVED] Booting with low graphics problem"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-23
Hello,
I have another thread, but I don't think it was descriptive in the way it should be.

The problem is that after installing ubuntu studio for video editing, the software required a reboot, and after rebooting a ubuntu realtime kernel had appeared. I don't know why it's there, but I assume that the studio needs a different kernel to run properly. However, after a couple of strange screens in the boot (of rt mode) which included a prompt and some information, ubuntu loaded in Low-graphics mode. I don't seem to be able to regain my good graphics mode, which is quite sad :( 

I've uninstalled studio, as I'd like to learn a bit more about Linux before messing with kernels ._. but nothing seemed to change... So my question now is this:

Is there a way to restore my ubuntu settings as of yesterday?,Like windows system restore? If someone helps, I promise not to touch things I don't know about in Synaptic :D


Thanks for any helps.:KS

---

### Post by Ub1476 on 2008-03-23
Unfurtnately there is not system-restore available, but have you tried to reinstall ubuntus default packages?

```
sudo apt-get install ubuntu-desktop --reinstall

sudo apt-get autoremove
```

---

### Post by hungryOrb on 2008-03-23
Thank you for the reply. Although it didn't reset my boot options, and Ubuntu generic kernel is still failing to make use of the graphics card properly, highest res is 800x600.
Will I need to reinstall Ubuntu? And if so, what's the best way? If I do that, is it possible to pick up my desktop settings that I have at the moment? Can I pack them into a file, shove it on my windows drive and transfer it later onto the new install? 
Or something... similar? ^.^
Thanks for any helps!

---

### Post by hungryOrb on 2008-03-23
Any helps please? :'(

---

### Post by ubuntu-freak on 2008-03-23
What sort of settings do you want to back up? Did you search Synaptic for the previous kernel? Also, this command will help you to reconfigure your graphics device and screen;
 
**sudo dpkg-reconfigure -phigh xserver-xorg**           

Just follow the prompts and make sure you select the right video driver and resolution.
 
Nathan

---

### Post by hungryOrb on 2008-03-23
Thanks man, I'll try it out :)

---

### Post by hungryOrb on 2008-03-23
Worked great :) How do you learn this stuff? In the desktop help file? ^^

---

### Post by ubuntu-freak on 2008-03-23
> **hungryOrb said:**
> Worked great :) How do you learn this stuff? In the desktop help file? ^^

 
Great! Use the thread tools and mark it as solved.
 
Was it the dpkg command that fixed your issue? It's the standard way to configure or reconfigure devices. You can also add options to xorg.conf for extra features or workarounds.
 
Everything I know has been due to other forum goers or online articles. 
 
Nathan

---

### Post by Tews on 2008-03-23
> **Ub1476 said:**
> Unfurtnately there is not system-restore available, but have you tried to reinstall ubuntus default packages?

You CAN now do a system restore with Quick-Start .. see the thread [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

