---
title: "Direct rendering."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by dankdank on 2008-03-23
Okay so I would like to install and play world of warcraft I first googled "world of warcraft on ubuntu" and I clicked a link that brought me to a help.ubuntu. site and the first step was to make sure I had direct rendering enabled for 3d graphics.

it said to type glxinfo | grep rendering in the terminal so I did it said to make sure that direct rendering came up "yes" which it didn't so my question to you guys/girls is if it is completely necessary to have direct rendering on because I am already using compiz effects wich requires 3D drivers

PS: I have ATI and have the ATI restricted drivers install and enabled.

---

### Post by dankdank on 2008-03-23
No one? :(

---

### Post by dankdank on 2008-03-23
bump?

---

### Post by Ub1476 on 2008-03-23
To use Compiz with the ATI driver from Restricted Driver Manager, you have to install XGL which "steals" your 3d acceleration except from Compiz. Therefore you get a negative output from terminal. You would be better off with the latest drivers from ATI, which Envy can install and configure for you. Or you can wait till Ubuntu 8.04 will be released in April, with the new drivers in repos. 

If you want to use the new drivers now, remove XGL (xserver-xgl) and the drivers from RDM (do not reboot). Then, get Envy and let it install the drivers and configure X for you. Now reboot and install WoW.

---

### Post by dankdank on 2008-03-23
I'm a little scared doing this without a walk through guide because when I have tried this before i followed a guide that told me to delete the xgl drivers and install envy then reboot I then had a blank black screen and had to reinstall ubuntu all together :(

---

### Post by forrestcupp on 2008-03-23
Well, it's pretty much either that, or don't use Xgl and Compiz at all.  If you aren't using Compiz and Xgl, the drivers from the RDM will work with direct rendering.

BTW - if you get a black screen with Envy, you don't need to reinstall Ubuntu.  You can boot to the recovery mode, which is usually the 2nd choice in the GRUB menu. Then you type:
```
envy --uninstall-all
```
That will undo everything envy did and get you to where you can boot to the desktop again.

---

### Post by dankdank on 2008-03-23
Okay well that would have helped me :P

But now how do I go about installing the RDM drivers and making direct redering work? (please be gentle this is my 4th day in linux)

---

### Post by cdsboy on 2008-03-23
I'm going to assume that your on gutsy. Follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually") guide. Thats what worked for me. Plus some little tweak that only applies to the ati xpress 1100.

---

### Post by dankdank on 2008-03-23
Okay so I followed the guide "The ubuntu way" and followed the terminal commands typed

```

glxinfo | grep rendering

```
came up
```

glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

---

### Post by forrestcupp on 2008-03-23
So you want to use the drivers in the RDM and have direct rendering?  That means you are willing to **not** have Compiz.  If you still have Envy, then boot to recovery mode and type
```
envy --uninstall-all
``` to get rid of the mess you've made of your drivers.  Then type
```
apt-get remove xserver-xgl
reboot
``` to get rid of Xgl, then to reboot.  When you reboot, you won't be able to enable Desktop Effects because you don't have Xgl anymore, but you should be able to get direct rendering to work.  Go to your Restricted Drivers Manager and enable the driver for your ATI card.

Then try again
```
glxinfo | grep rendering
```
And it should say 'yes'.

When Hardy comes out the end of next month, the drivers in RDM will support Compiz without Xgl.  Maybe you're best off just to do this and wait on the effects till then.

---

### Post by JoshuaRL on 2008-03-23
And just in case you were wondering, (and because it confused me for a second) RDM is Restricted Driver Manager in Settings->Administration.

---

