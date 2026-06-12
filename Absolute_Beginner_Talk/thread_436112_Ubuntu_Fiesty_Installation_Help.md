---
title: "Ubuntu Fiesty Installation Help"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-07
Well I tried the Kubuntu way.  Put the disk in... Blah.

I currently have Kubuntu.  And Im switching to Ubuntu.

How do I start the new installation?


I have the Ubuntu Fiesty disk.

---

### Post by hessiess on 2007-05-07
eather make new partitions or format the old ones dont do later if you want to move data   then create a swap and one with / as the mount point

---

### Post by LollYouSuckZor on 2007-05-07
Well I installed Kubuntu a day ago.

A friend from here gave me the Ubuntu Feisty disk.

I was wondering how to start the install.
I dont mind disk partitioning, I'll erase.

How do I start the install successfully?

---

### Post by LollYouSuckZor on 2007-05-07
Okay.  I found the mount point area.  What do I do from here...

---

### Post by fakie_flip on 2007-05-07
If you dont know what you are doing, just use automatic partitioning.

---

### Post by LollYouSuckZor on 2007-05-07
> **fakie_flip said:**
> If you dont know what you are doing, just use automatic partitioning.

Is that from the Install window?

Im asking how to get to the INSTALL window.
I have the CD for Ubuntu Feisty.
I want to open that Install window, but I dont know how.

---

### Post by LollYouSuckZor on 2007-05-07
The Kubuntu basically had an auto install. I just selected my language, etc.
I have a whole CD with everything on it.
I dont have any other CD's with the right amount of size. The cd was given to me by a friend. The CD is in the drive right now. How do I change the settings?


Go to Advanced. Then to Disk and Filesystems.

Then Admin mode.

What do I do from here?

---

### Post by fakie_flip on 2007-05-07
> **LollYouSuckZor said:**
> Is that from the Install window?

Im asking how to get to the INSTALL window.
I have the CD for Ubuntu Feisty.
I want to open that Install window, but I dont know how.

Reboot your computer with the Ubuntu Feisty disk in it. Now you should see a different screen after you reboot. If your computer goes back to windows again instead of booting to from the cd, then tell me, and I will help you get the cd to boot by changing your bios settings. After you get the cd to boot, double click the install icon that you will see on the desktop of the Ubuntu cd running live and follow the directions from there. If you get stuck somewhere else, let me know.

---

### Post by zvacet on 2007-05-07
If you want just change desktop enviroments there is no need for reinstall.install ubuntu desktop and remove kubuntu desktop.Go to hte Adept>edit>mark by task and choose ubuntu desktop.If you can not find that option in Adept type in terminal

```
sudo aptitude install ubuntu-desktop
```
and when it is install
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by LollYouSuckZor on 2007-05-07
> **fakie_flip said:**
> Reboot your computer with the Ubuntu Feisty disk in it. Now you should see a different screen after you reboot. If your computer goes back to windows again instead of booting to from the cd, then tell me, and I will help you get the cd to boot by changing your bios settings. After you get the cd to boot, double click the install icon that you will see on the desktop of the Ubuntu cd running live and follow the directions from there. If you get stuck somewhere else, let me know.
Lol no dude, Ive already installed a kind of Linux
Kubuntu
and im trying to lose it and get Ubuntu.
everytime I boot with the disk in the drive, i get the  kubuntu loading screen right after the Nvidia Gefore screen


So basically how do i get it to boot from the cd?

---

### Post by psyopper on 2007-05-07
When your computer starts there is usually a key strok to enter the BIOS. Most systems it's ESC or F-10. Look on the screen, it will tell you "Press <xx> to enter BIOS" or "Press <xx> to Enter Setup".

Once inside poke around for a boot order and put the CD at the top of the list. Save your changes and exit. Restart the computer with the Live CD in it.

Kubuntu and Ubuntu are almost identical. They differ only in the user interface (in  the LInux world they call this the Window Manager). What is being recommended is that you keep your Kubuntu installation with the KDE window manager and ADD the Gnome window manager.

---

### Post by LollYouSuckZor on 2007-05-07
After trying the Above ^

I got this




*Activating swap
*Checking root file system
fsck 1.39 (29-may-2006)
/dev/shm/root: clean, 88283/4751360 files, 718175/94883282 blocks

/etc/rcS.d/s20checkroot.sh: 407 readlink: permission demnied
/etc/rcS.d/S20checkroot.sh: 407: usplash_write: permission denied
* CAnnot initialize /etc/mtab.
/etc/rcS.d/S20checkroot.sh: 407: rm: permission denied
int: unable to execute "/bin/sh: for rc-defualt: permission denied
init: rc-defualt process (3246) terminated with status 1

---

### Post by fakie_flip on 2007-05-07
Is that the 64 bit version of Ubuntu?

---

### Post by LollYouSuckZor on 2007-05-07
Im not sure, a friend just gave me the CD

---

### Post by fakie_flip on 2007-05-07
Check the cd for defects. After you boot the cd, it gives you that option on the menu. Maybe your friend gave you the wrong version? 64 bit Ubuntu and you have a 32 bit pc?

---

### Post by LollYouSuckZor on 2007-05-07
I have a 32.  Im doing a memory test right now, im so pissed I dont know what im doing.

---

### Post by ZeroWing on 2007-05-07
> **fakie_flip said:**
> Check the cd for defects. After you boot the cd, it gives you that option on the menu. Maybe your friend gave you the wrong version? 64 bit Ubuntu and you have a 32 bit pc?

 It's a 32-bit cd. I gave it to him, and he doesn't like me much now. :) 

 Could be scratched, right? I know I didn't burn it too fast. I used 2.0x.

 Just try going to a terminal and typing

 sudo apt-get install ubuntu-desktop

 same thing as a clean install, kind of. When that's done, log out and go to sessions(on the bottom of the login window, usually, and select GDM, or GNOME.

 And try going into your BIOS and resetting it. Works, usually.

---

### Post by LollYouSuckZor on 2007-05-07
[QUOTE=ZeroWing;2612231]It's a 32-bit cd. I gave it to him, and he doesn't like me much now. :) 

 Could be scratched, right? I know I didn't burn it too fast. I used 2.0x.

 Just try going to a terminal and typing

 sudo apt-get install ubuntu-desktop

 same thing as a clean install, kind of. When that's done, log out and go to sessions(on the bottom of the login window, usually, and select GDM, or GNOME.

 And try going into your BIOS and resetting it. Works, usually.[/QUOTE


What I Dont Know:
What a BIOS Is.
GDM? and GNOME?
Logout and SESSIONS? Wheres sessions...

[Sorry, Im a Linux N00b]

---

### Post by ZeroWing on 2007-05-07
> What I Dont Know:
What a BIOS Is.
GDM? and GNOME?
Logout and SESSIONS? Wheres sessions...

[Sorry, Im a Linux N00b]

 BIOS: screen that flashes up on startup.

 some look like this:

 [IMG]http://www.ixbt.com/video/images/aiw-radeon/bios.gif[/IMG]

 GDM: GNOME desktop manager

 GNOME: Graphical thingy for Linux. What you're using is KDE, and it's generally not recommended for Linux 'newbies'.

 Sessions should be around the edges of the screen. Example: 

 [IMG]http://reverendted.wordpress.com/files/2006/09/sled-004-joined-displaymanager.png[/IMG]

 And you know how to log out. It's in the menu that pops up when you click the shutdown button. With the sleeping lizard-thing?

---

