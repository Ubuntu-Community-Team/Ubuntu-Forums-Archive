---
title: "3D Graphic Problems"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Ixnay on 2006-11-02
Hi,

I installed World of Warcraft using Cedega and it installed just fine. Also had no problems downloading the patches. Anyways, when Im in the game it's EXTREMELY slow. By that I mean like less than 1 frame per second. So I thought it might be a Graphics Driver Issue or something, and so I went onto the NVIDIA website and downloaded a driver for Linux. It says I should install the file by typing: "sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run". Where do I type this? I typed it into the Terminal thingy and just got some error messege telling me that the file couldn't be found. This is where I got the driver by the way: [http://www.nvidia.com/object/linux_display_amd64_1.0-8776.html](http://www.nvidia.com/object/linux_display_amd64_1.0-8776.html)

Also...just klicking on the link to download the file just links me to a bunch of text, so I right-clicked and saved as. I think that was the right thing to do. Anyways, I think installing the driver will solve my graphical issue, but I don't even know how to install the driver. Any help?

Regards,
Chris

---

### Post by igknighted on 2006-11-02
Hmm, NVIDIA drivers are tricky if I remember correctly.  I would recommend downloading automatix2 from [www.getautomatix.com](www.getautomatix.com) to install the drivers (along with lots of other cool software), much easier.

---

### Post by CatKiller on 2006-11-02
If I were you, I'd install the nvidia-glx package through Synaptic, or use the command ```
sudo aptitude install nvidia-glx
``` You're right that clicking on the link does show you the contents of the script, so a right-click and Save As is fine. If you do decide to attempt the install of the stuff you've downloaded from the nVidia website, you'll need to **cd** into the directory that you've saved it in (**cd Desktop**, for example), make it **executable**, and run it as [root]("https://help.ubuntu.com/community/RootSudo"). You may also need to refer to it as ./NVIDIA-Linux-x86_64-1.0-8776-pkg2.run instead.

If you're interested, the version in the repositories (easy to install) is 87.62.

It must be said that a lot of people have struggled to get Wine working satisfactorily on a 64-bit Ubuntu install. It might be worth trying the 32-bit install of Ubuntu for a while, until you're confident enough with Ubuntu to fix the problems you'll encounter with 64-bitness - not just with Wine, but graphics drivers and other software too.

---

### Post by lkr0se on 2006-11-02
> **CatKiller said:**
> If I were you, I'd install the nvidia-glx package through Synaptic, or use the command ```
sudo aptitude install nvidia-glx
``` You're right that clicking on the link does show you the contents of the script, so a right-click and Save As is fine. If you do decide to attempt the install of the stuff you've downloaded from the nVidia website, you'll need to **cd** into the directory that you've saved it in (**cd Desktop**, for example), make it **executable**, and run it as [root]("https://help.ubuntu.com/community/RootSudo"). You may also need to refer to it as ./NVIDIA-Linux-x86_64-1.0-8776-pkg2.run instead.

If you're interested, the version in the repositories (easy to install) is 87.62.

It must be said that a lot of people have struggled to get Wine working satisfactorily on a 64-bit Ubuntu install. It might be worth trying the 32-bit install of Ubuntu for a while, until you're confident enough with Ubuntu to fix the problems you'll encounter with 64-bitness - not just with Wine, but graphics drivers and other software too.

I'm going to jump in here as I'm having a simular problem.  Where are these repositories that you speak of?

---

### Post by CatKiller on 2006-11-02
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by lkr0se on 2006-11-02
Thanks CatKiller

---

### Post by Ixnay on 2006-11-03
Im not sure if I have the 64-bit or 32-bit version of ubuntu installed. Btw, I'm not using wine to play WoW I installed it with cedega. I need to know which bit version of ubuntu I have, since there is an NVIDIA driver for each. How can I check which version I have?

Also I have another question. I used "cd desktop" and then "sh NVIDIA-Linux.....pkg1.run" and it sorta worked. It told me to run it as "root" though. How do I do that? (please keep it simple :D).

Regards,

Chris

p.s. thanks for the help so far

---

### Post by Ixnay on 2006-11-03
bump

---

### Post by CatKiller on 2006-11-03
> **Ixnay said:**
> Im not sure if I have the 64-bit or 32-bit version of ubuntu installed. Btw, I'm not using wine to play WoW I installed it with cedega. I need to know which bit version of ubuntu I have, since there is an NVIDIA driver for each. How can I check which version I have?

It should tell you which version you're using on the cd that you used to install it. The i386 version is 32-bit. The AMD64 version is 64-bit, and is less suitable for beginners, from what I've heard. I've never used it.

And you **are** using Wine. Cedega is just Wine that you pay for, with some binary patches. I doubt that they've made it so different that all of the people struggling to get Wine to work on the 64-bit version would magically have all their problems go away by giving TransGaming some money. After all, it's not like Windows applications can handle 64-bit processors that well.

> Also I have another question. I used "cd desktop" and then "sh NVIDIA-Linux.....pkg1.run" and it sorta worked. It told me to run it as "root" though. How do I do that? (please keep it simple :D).

Just... don't. Install the drivers through Synaptic or Automatix or something.

You'll probably want to read these pages:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Anyway, once you try to run the script as root, it'll tell you that it won't work when X is running. So you could try the following:

Close everything that you've got open.
Press **Ctrl-Alt-F2** to get to a virtual console.
Log in.
```
sudo /etc/init.d/gdm stop
cd Desktop
sudo ./NVIDIA-Linux.....pkg1.run #(*use tab-completion rather than typing out the name*)
sudo /etc/init.d/gdm start

```

It must be said that some of this might be wrong, since I've never had to do it. Because Synaptic is so much better.

Good luck.

EDIT: You certainly didn't need to bump after an hour. Especially since I'd already told you how to run things as root.

---

### Post by Ixnay on 2006-11-03
thanks, the FPS rate seems fine now...I have some problems with the font and text, but Ill post that into the Cedega-WoW forums.

Thanks for all your help

Regards,
Chris

---

### Post by livinginx on 2006-11-03
I have some slight font issues with Wine and CS 1.6, but nothing I cannot deal with.  Wine (and Cedega) from what I have read can act different with every install even with the same hardware.  Usually just takes some tweaking.

---

