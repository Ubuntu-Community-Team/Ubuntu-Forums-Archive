---
title: "How do I remove Kubuntu desktop?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-04-18
I tried the only 2 codes that I could think of... 

```

matt@ubuntu:~$ sudo apt-get remove kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 162 not upgraded.
matt@ubuntu:~$ sudo apt-get remove kde-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde-desktop

```

And thats what it gave me. I just installed Ubuntu via the internet from KDE, I can select KDE from the session menu but the terminal, as you can see, says there is no KDE. Thanks in advance for any help.

---

### Post by starcraft.man on 2007-04-18
*scratches head* You installed Ubuntu from KDE? I don't follow... KDE is the desktop environment, and Ubuntu doesn't come preloaded with it. Do you mean you installed Kubuntu from the Kubuntu site and now you want to switch to Ubuntu with Gnome? Please clarify.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
> **starcraft.man said:**
> *scratches head* You installed Ubuntu from KDE? I don't follow... KDE is the desktop environment, and Ubuntu doesn't come preloaded with it. Do you mean you installed Kubuntu from the Kubuntu site and now you want to switch to Ubuntu with Gnome? Please clarify.

I was uisng Kubuntu. I opened the terminal and typed ```
sudo apt-get install ubuntu-desktop
```

I am now on Ubuntu desktop, which uses Gnome. I now want to remove the KDE desktop, as I have old hardware and KDE using up 500 some odd megabytes significantly slows down my computer when Ihave both desktop environments installed. I only want Gnome installed. How do Iremove KDE desktop environment?

---

### Post by milton1 on 2007-04-18
the terminal message you give says there is no kubuntu-desktop. this is a meta-package that includes many packages as dependancies. not having that does not mean you don't have kde installed. If you really want to completely purge kde, your best bet is a fresh install of Ubuntu. Otherwise, you will waste huge amounts of time finding and removing all the programs and libraries required to run kde.

---

### Post by milton1 on 2007-04-18
> **Narcoleptic_Insomniac said:**
> KDE using up 500 some odd megabytes significantly slows down my computer when Ihave both desktop environments installed. 

Just having the kde packages installed should not slow down your system if you are currently running gnome. If you need the space, that is different, but removing the packages is unlikely to result in improved system performance.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
> **milton1 said:**
> the terminal message you give says there is no kubuntu-desktop. this is a meta-package that includes many packages as dependancies. not having that does not mean you don't have kde installed. If you really want to completely purge kde, your best bet is a fresh install of Ubuntu. Otherwise, you will waste huge amounts of time finding and removing all the programs and libraries required to run kde.

I tried to do a fresh install of Ubuntu but due to the poor hardware of my computer I can't install from the live CD so I need to use the alternate text installation CD. That is what I first used to isntall Ubuntu which was when it was on Dapper. Now its on Edgy, so  I burned the Edgy alternate CD, and Feisty Beta alternate CD, neither of which my computer will boot from start up, so I can't install from those. I tried the old Dapper alternate CD and that won't start up either. 

So I tried going into my computers bio's by pressing F2, Esc, Del and the usual buttons at the usual screen, but apparently my computer has none of those options, so I don't know what button to push when my computer starts up to tell it to run the CD before it runs the OS.

---

### Post by starcraft.man on 2007-04-18
Sounds like your computer has an extremely serious problem, booting from a CD is vital. I don't suppose you have a backup copy of your bios and can flash it back on? (thats a bit techie >.<). I think you should really focus on fixing your bios, without it if you corrupt your install and have to reformat your drive your well ... screwed. If ya can't get your bios back to working, might be time for a new comp >.>.

---

### Post by milton1 on 2007-04-18
Let me be sure that I understand; your computer did boot earlier alternate install cd's, but not more recent ones? If this is true, it is not a bios issue. Either something is wrong with your cd's or something is wrong with the drive. Are you using cd-r or cd-rw? Many older cd-roms will not read cd-rw. also, at what speed did you burn the new cd's? Sometimes problems can occur when the cd images are bured too fast.

Hope some of this helps.

---

### Post by milton1 on 2007-04-18
Have you tried searching your computer manufacturer's website for instructions on accessing the bios?

---

### Post by starcraft.man on 2007-04-18
> **milton1 said:**
> Let me be sure that I understand; your computer did boot earlier alternate install cd's, but not more recent ones? If this is true, it is not a bios issue. Either something is wrong with your cd's or something is wrong with the drive. Are you using cd-r or cd-rw? Many older cd-roms will not read cd-rw. also, at what speed did you burn the new cd's? Sometimes problems can occur when the cd images are bured too fast.

Hope some of this helps.

I'm pretty sure its his bios... he said > **Narcoleptic_Insomniac said:**
> I tried the old Dapper alternate CD and that won't start up either. 


I assume that was his old cd that did work when he originally installed Kubuntu.

Milton has a point though, if your mobo manufacturer gives you instructions to modify and restore your bios you should give it a shot.

---

### Post by Tundro Walker on 2007-04-18
I had the same issue when I first started out with Ubuntu on an old 800mhz machine.  Gnome was slow, and I read instead of reinstalling using Xubuntu, I could simply install "xubuntu-desktop" to load XFCE.  I did, but it was still sluggish to boot and load.  I stumbled across the following site... 

[http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop)

...which made me realize there was a lot of extra stuff that just removing the "*buntu-desktop" meta packages didn't remove (even if you selected "complete removal").  He explicitly says "this should work in theory", so use at your own risk.  

As an alternate method, you can open Synaptic, search for all installed entries that have "KDE" in the title or description, and start right-clicking them for complete removal.  When you're done running his script, or picking off "KDE" entries manually, do the following in a terminal.

```
sudo apt-get remove; apt-get autoremove; apt-get clean; apt-get autoclean
```

This will run apt-get to find any libraries or other packages that ran helped run KDE that are no longer needed and will get rid of them.

You can also look at WackToMack's "Cleaning" How-to, which talks about some simple procedures for system cleanup (with a quickie script added by me to help automate some of it)

[http://ubuntuforums.org/showthread.php?t=140920&highlight=clutter+control](http://ubuntuforums.org/showthread.php?t=140920&highlight=clutter+control)

Same can be done with the XFCE or GNOME desktops.  If you find one you like and want to bump off the others, just Synaptic search for their names as title & keywords, and you'll get a group of their respective, installed stuff.  Bump off what you want, keep what you like (which is why I don't recommend running a script), and then apt-get remove to clean up useless stuff left behind.  You should find a faster system when done.

---

