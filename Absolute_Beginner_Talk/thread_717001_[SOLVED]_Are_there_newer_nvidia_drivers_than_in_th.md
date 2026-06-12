---
title: "[SOLVED] Are there newer nvidia drivers than in the repository?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2008-03-06
How can I tell what the latest revision is for the nvidia drivers for my system? I get the impression from the fact that a tool like envy exists that the repository does not have the latest revisions. 

Also I have the Quadro 140NVS Mobile in my T61 and there are NO drivers on nvidia's web site for it. NONE! ZIP! None for linux, none for vista. I did not try for XP...

I would like to know what revision is newest compared to what I have so I can check if it will fix my brightness buttons before I waste yet another several Ubuntu hours on trying to get something to work instead of actually getting my work done. I really like Ubuntu but holy cow it has been an ordeal getting things to work. I swear I have spend 100 hours troubleshooting, researching and trying to fix broken things. 

Sorry for the mini-vent and I hope it doesn't prevent anyone from helping me out! 

Thanks!
Eric

---

### Post by neurostu on 2008-03-06
If you get your T61 brightness buttons fixed let  me know. I would like to get mine fixed too.

What other things are you trying to customize on your T61?

---

### Post by bodhi.zazen on 2008-03-06
Nvidia releases a proprietary, closed source driver fairly frequently:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Note: Sometimes they cause breakage so I am not so fast to update.

---

### Post by zekica on 2008-03-06
The newest version is [169.12]("http://www.nvidia.com/object/linux_display_ia32_169.12.html").
It supports your graphics card: NV Quadro NVS 140M.

I can suggest installing the newest drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by neurostu on 2008-03-06
If you install a driver using envy, what happens when you have a kernel update?

---

### Post by nowhere@cox.net on 2008-03-10
From what I have read, you have to unistall the envy installed nvidia drivers before a kernel update, then update then re-install the nvidia drivers. Are there any other kinds of updates you have to uninstall nvidia drivers for when using envy?

I am pretty new so I assume if an update has the word kernel in it, it is a kernel update. Is this the way to tell?

Also, synaptic reports my installed version of nvidia-glx-new is 100.14.19+2.6.22.4-14.10.  I am not exactly sure how to translate that to the nvidia version. I see the kernel version in it (2.6.22.4-14.10) but the 100.14.19? Is is version 100.14? 

Can I turn on a different repo to install a newer version? 

Thanks,
Eric

---

### Post by stchman on 2008-03-10
> **nowhere@cox.net said:**
> From what I have read, you have to unistall the envy installed nvidia drivers before a kernel update, then update then re-install the nvidia drivers. Are there any other kinds of updates you have to uninstall nvidia drivers for when using envy?

I am pretty new so I assume if an update has the word kernel in it, it is a kernel update. Is this the way to tell?

Also, synaptic reports my installed version of nvidia-glx-new is 100.14.19+2.6.22.4-14.10.  I am not exactly sure how to translate that to the nvidia version. I see the kernel version in it (2.6.22.4-14.10) but the 100.14.19? Is is version 100.14? 

Can I turn on a different repo to install a newer version? 

Thanks,
Eric

I use Feisty and from what I see the kernel only get new modules added and not an entirely new kernel.  I cannot speak of Gutsy.

---

### Post by forrestcupp on 2008-03-10
If you're using drivers from the Restricted Driver Manager, and they're working for you, stick with them.  Those drivers automatically get updated when the kernel gets updated.  If those drivers don't work, then you're right.  Every time your kernel gets updated, you will have to uninstall your envy drivers first then reinstall them afterward.

But usually, unless you're using an alpha or beta version of Ubuntu, the only time you will get a kernel update that will break your drivers is when you upgrade to a new version.  Like when you upgrade from Gutsy to Hardy.

And it's true that Envy installs the latest drivers directly from nvidia's website.

---

### Post by johnwillyums on 2008-03-10
Hi. I dual boot Ubuntu 7.10 64x with Vista HP 64x and am using an nVidia 8600GT at the moment. I want to upgrade to an 8800GT but seem to be struggling because of the dual boot.
Vista forums advise me to boot Vista into safe mode, uninstall the 8600 drivers, run drivercleaner and then swap cards.
After that install the appropriate drivers from nVidias website and reboot as normal.
I looked on driver cleaner's website and that says to run it in safe mode in Vista.
However since I installed Ubuntu my boot menu is totally different-
I get:
Ubuntu 7.10
Ubuntu recovery mode
Ubuntu memtest 86x
Other operating Systems
Windows Vista/Longhorn (loader)

There doesn't seem to be a way to boot Vista into safe mode. I can enter setup by pressing Del or boot by pressing Tab and I've done that but cannot see a way to boot Vista into safe mode. There doesnt seem to be any further reference to Vista once I get past the initial choice. 

Can anybody help me out with this?
Thanks, John (complete newbie}:confused:

---

### Post by nowhere@cox.net on 2008-03-10
Hi John,

I would definitely post this as a new and seperate thread. Buried within my thread about a different topic will not get you the audience you will need to answer your question. 

That said,  I think you should be able to select Vista from the grub menu and immediately after selecting Vista to boot start pressing F8. I believe that is the key to get the boot option menu to come up.

If this doesn't work then repost your question as a separate thread. 

Good luck!
Eric

---

### Post by nowhere@cox.net on 2008-03-10
Thanks guys. I will give envy a try I suppose. I assume the "undo" process would be simply to use envy to uninstall the driver then use the restricted package manager to re-install the older version?

Thanks,
Eric

---

### Post by johnwillyums on 2008-03-10
Thanks Eric. I think I will post this as a fresh thread as you suggest. I will look in the grub menu again but I don't think there is any other mention of Vista after the initial choice.
Thanks again, John

---

### Post by nowhere@cox.net on 2008-03-10
Hi John,

I don't think I was clear. When booting your machine, the grub menu will come up. You can then let the default boot or select the OS you want to boot. Select Vista. As soon as the grub menu goes away, start pressing F8 repeatedly (doesn't have to be really fast). This should bring up the boot options for Vista.

I will give it a try on my machine right now...

Edit:  John,  works like I expected. Hit enter to tell grub to boot Vista and a "Starting Up..." message appears at the top left. Hitting F8 brings up all the boot options for Vista. This, I believe, is what you are after, to be able to boot in safe mode.

Good Luck!

Eric

---

### Post by nowhere@cox.net on 2008-03-11
Ok, 

The envy website gives instructions on how to handle kernel updates and it seems to be pretty simple so I have installed envy and the latest nvidia driver. I removed the additions to my acpi scripts for up and down brightness and rebooted. The brightness keys now work as well as everything else. I think I have a little bit better performance on 3D as well judging from the smoothness of the rotating cube desktop effect. 

The only quirk is that the the lowest brightness setting is reached 4 notches before the lowest OSB meter setting so the last four clicks down and the first four clicks up have no effect. No big deal at all.

Thanks for the help. I'll post again in a few days to report if anything was broken on my T61 from using envy and the latest nvidia drivers.

Eric

---

### Post by Cerny on 2008-03-11
I would recommend envy to find and install your latest drivers for Nvidia

---

