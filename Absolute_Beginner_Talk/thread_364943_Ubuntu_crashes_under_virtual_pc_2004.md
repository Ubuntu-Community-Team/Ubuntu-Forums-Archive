---
title: "Ubuntu crashes under virtual pc 2004"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by master_phruby on 2007-02-18
Hi everybody. It's been a really long time since I use to administrate linux servers back in school. In fact, I remember the day that Linux got to 1.0!!! Anyway, I'm trying to install Ubuntu 6.11, I believe, under Microsoft's Virtual PC 2004 on a Windows XP box. I want to test out the operating sytem here before dedicating a real partition to it. I've given it 256mb of ram. 

The installation seems to go fine until we finally get to the desktop. At that point, the screen is completely grabled. You can't read anything. It looks like the screen is in somekind of weird EGA mode. Most of the pixels are missing. It seems Ubuntu doesn't like my graphics card.  This is a MSI K7N2G motherboard with a build in NVidia GeForce 2 graphics card. Any idea on how to fix this or should I just go to my old stomping grounds of Slackware?:confused:

---

### Post by sank on 2007-02-19
I have the same problem.  I wouldn't say that it has crashed, but the screen goes to 1600 x 600 x 8 resolution, and indeed it is all garbled.  If you blur your eyes and drink a shot, you can kinda see what is supposed to be there.  In fact, the menus and buttons and everything work - you just can't really read anything very well (nor see everything, since it's set to only 600 px tall).

I've tried to boot using the 'safe mode' and use vesa video drivers, but it doesn't work.

This is a similar issue:
[http://forum.freespire.org/showthread.php?t=821](http://forum.freespire.org/showthread.php?t=821)

If anybody knows how to get around this, please do tell.

---

### Post by sank on 2007-02-19
P.S.  I am trying to install 6.10, and this is what my screen looks like in 'safe graphics mode' as well as the normal mode.

---

### Post by sank on 2007-02-19
Okay, I got it working; here's what I did.

If I modify the LiveCD option F6 startup parameters to include vga=771, then I can read the display a *little* better (*very *little, mind you).

Then, I was able to double-click the Install icon and follow the steps by using these screenshots as a guide:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

When Ubuntu finally booted up, the display was still whacked out to 1600x600x8, so then I found this page which describes "Dealing with problems with the Xserver":
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

After running through the reconfigure 'wizards' as it instructs, and after the reboot command, everything is normal as expected!

Now, there must be a way to more properly specify the correct fix/flag from the LiveCD boot menu, but I don't know what it is.=D> 

It doesn't seem like something that difficult for the Ubuntu Gurus to figure out how to fix in the next revision.

---

### Post by esaym on 2007-03-03
Why in the world are yall trying to run a live cd in a virtual environment?  It is a live cd!  If you want to try out the OS before you install it you simply boot from the cd and you will have a fully functional OS and it will not mess with your hard drive until you click on the "Install" icon on the desktop.

---

### Post by Tomosaur on 2007-03-03
Try using InnoTek VirtualBox. It's free for personal use (and there is an open source version) - and it is much more stable than Virtual PC. I am right now installing Ubuntu on my parent's PC through VirtualBox - it's great.

---

### Post by Daveski on 2007-03-03
> **esaym said:**
> Why in the world are yall trying to run a live cd in a virtual environment?  It is a live cd!  If you want to try out the OS before you install it you simply boot from the cd and you will have a fully functional OS and it will not mess with your hard drive until you click on the "Install" icon on the desktop.

Indeed, but you have to boot the LiveCD in order to install on the virtual machine. The installtion is a real pain with the weird graphics you get with VirtualPC.

---

### Post by Arkaniad on 2007-12-31
Ello, i just saw this problem when i was googling how to install 7.10 on virtual pc .

I recently found on a site that if you are having trouble with vpc display installing 6.06 dapper drake you should boot into safe graphics mode. Hope it helps!

---

### Post by Arkaniad on 2007-12-31
ok, i have freshly booted 7.10 in vpc 2004 , and i get teh garbled screen of death. there is a HUGE error box in the screen. what should i do?

---

