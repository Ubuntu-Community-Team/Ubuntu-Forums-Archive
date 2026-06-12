---
title: "Appearance"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by will-t-c on 2008-01-13
Hi guys,

Just registered so sorry if this is in the wrong place. I downloaded ubuntu 7.10 last night and made a live CD. I haven't been able to enable the extra visual effects. It either says it is unable to do it or that I need to download my nvidia graphics card driver.... Which I have done aout 10 times as it keeps telling me to restart. Once I restart it just asks me to download it again as if I never did. 

Hope someone can give me a helping hand to get this sorted. 

Thanks in advance. 

Will

---

### Post by Arthur Archnix on 2008-01-13
Well, if you're just running the livecd what that means is that no changes are being made to your hard-drive. When it says to restart, that's because it thinks that you're running ubuntu as its installed to your harddrive. But when you restart, since nothing was saved to your hard-drive it forgets everything you did in the previous sessino. There are ways to get around this, with flash drive for instance. Here's a link with more info [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

Unfortunately, the livecd can only approximate the ubuntu experience. Another way to try it out is to use wubi, which is ubuntu installed on your windows partition.  Here's a link to wubi. [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by will-t-c on 2008-01-13
Ah ok. I think I will probably install it soon, but first I will check out your two links. The only thing that would concern me is how many windows based programs actually work on it. For example Office? 

Oh and one more question...is Beryl like theme or what exactly? And once I have enabled the
more advanced visual effects will that allow me to use the cube etc?

Thanks again for your help!

Will

---

### Post by sleepingdragon on 2008-01-13
This might be worth a try on a LiveCD.

Download the nvidia driver as normal. You should be asked to restart your system. Say No (or Later, i can't quite remember what it said). Now press Ctrl-Alt-Backspace togther. This should restart your display on the LiveCD and with a *bit of luck* make use of the nvidia settings. For some odd reason, I had to use C-A-B twice in succession to get it to work... go figure.

Of course, the moment you close or restart your computer it will forget this download so you'll have to do it again everytime you use the CD.

**EDIT**: Yes, once you get the extra visual effects running, you can use the cube. A simple way to see te cube is to hold down Ctrl-Alt-Left Mouse Button and move the mouse to rotate the cube. Release all to return to a normal desktop. There are many more features to the cube and other desktop effects, but to make the most of them you'll need to install other software (Advanced Desktop Settings) and all this is only worth it on a permanent installation. See if the cube works first, if you like what you see and everything else works OK (check for hardware compatibility, etc.), then seriously consider a permanent install. After that, you can go ahead and enjoy all the bells 'n' whistles that Compiz has to offer. Look at Youtube and search for Compiz to see what it can do.

Beryl and Compiz were seperate projects for the whole 3D desktop thing, they've now merged and been called Compiz Fusion. You'll find Compiz themes at either [www.gnome-look.org](www.gnome-look.org) or [www.kde-look.org](www.kde-look.org). If this is your first experiece of Linux , you might be a little surprised at how many options there are when it comes to customsing your desktop. In my personal opinion, the Windows Aero interface was soooo yesterday...

As for Windows software... this is Linux. It's gonna have a whole range of software that can do the same job (or better in some instances), but will not be the exact same software you're used to in Windows. There is some software that is identical, such as Acrobat Reader, Opera & Firefox web browsers to name but a few. Linux uses a central "repository" to download from. Just pick off the list, click Apply and wait for it all to download. Easy... and it handles all software/security updates too.

OpenOffice should take care of your office needs, including importing Office documents, you can even make your own PDFs wth it. Games are going to be a problem, the Linux market is much smaller than for Windows, so the amount of titles are limited, but it's getting better. There's a company called Cedega that can help get Windows games to run on Linux, but you're going to open yer wallet for them. Not say they're aren't any excellent games. If you're an FPS fan, you'll find some great titles like Alien Arena, Sauerbraten, OpenArena, Nexuiz and Tremulous.

Lastly, welcome to Ubuntu! There's great support here when you need it.

---

### Post by Arthur Archnix on 2008-01-13
There used to be these two windows managers, compiz and beryl. They let you do all sorts of cool things like the cube. Then they merged and joined forces to make compiz fusion, which is installed by default in ubuntu gutsy. Once you use the restricted drivers manager to get nvidia up and running you will be able to use effects like the cube, though you'll also need to install the compiz settings manager. Very easy to do. 

As for you windows programs, they will not run on Ubuntu easily. You'll need to either install wine (a program that let's you run some windows programs), or cross over office (which is wine with professional support), or by running a virtual machine. 

You can find more specific answers by searching the wine app database to see if your windows programs will run. Also look into virtualbox. You'll find plenty of info on both by punching those terms into google.

Edit: Sleeping dragon beat me to it. :)

---

### Post by will-t-c on 2008-01-13
Haha, OK thanks guys, so basically I install the OS, then I can download the Nvidia driver and use the cube etc. After this I then can start downloading Compiz themes at the links you gave me?

Is there a Linux alternative to Office as I would need that for work

Better start backing up I guess :)

Thanks again guys, really helpful info!

Will

---

### Post by sleepingdragon on 2008-01-13
lol. I've lost track who answered what, where and when. I'm going for a lie-down, or possible sideways...

---

### Post by Arthur Archnix on 2008-01-16
Once you feel like you've gotten the answer you need, you can mark a thread as solved using the "thread tools". Doing so will help others find answers to their questions more quickly.

Best wishes,

---

### Post by sailor2001 on 2008-01-16
under your SYSTEMS you will find synaptics package manager..Enable your repositories under settings and then search away for almost anything you need. Open office is as good or perhaps better than microsoft office.

---

