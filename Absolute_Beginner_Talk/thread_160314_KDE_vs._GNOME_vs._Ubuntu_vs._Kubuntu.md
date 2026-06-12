---
title: "KDE vs. GNOME vs. Ubuntu vs. Kubuntu"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-14
Im reading as much as  Can before installing on my machine. I just finished ubuntu on afriends laptop, now its my turn.  I have a dell 700m, 1.8ghz p-m 1 gig ram 80 gig hd, I assume graphics suck but i dont know how to tell. Im curious with desktop settings, can you do more 'eye candy' stuff with a KDE instead of gnome?  what about 3ddesktop deal, can a little laptop run it or would i need a big video card?  if installing ubuntu it come with gnome, but you can erase gnome and replace with kde if desired for better looks right? any experiences and preferences and advice are quite welcome, im choosing what to install probably tonight. Thank you all :mrgreen:

---

### Post by OffHand on 2006-04-14
You can run both  :D

---

### Post by Monster_user on 2006-04-14
Your little laptop can run 3ddesktop, if it gets atleast 600 when you run **'glxgears'** from a terminal. Glxgears may not be install, if not then do a search for it on synaptic.

I'd say it will work, just slowly. I wouldn't run 3Ddesktop.  It really just slows down Desktop switching. When you are not switching desktops, it not have any effect on your laptop.

Also, 3Ddesktop is not Xgl/Compiz which is a 3D OpenGL accellerated Desktop for Ubuntu 6, and Suse Enterprise Desktop 10. That will NOT run on your little laptop.

As for KDE vs Gnome. I've always found Gnome to be easier on the eyes. It is cleaner somehow... Although KDE has all those fade effects, and shadows, and animated progress bars, etc... It just seems so cluttered, and it seems like everything is running into something else.

I run them both anyware. If you are going to install KDE, I suppose we should welcome you to Kubuntu.

---

### Post by IYY on 2006-04-14
> That will NOT run on your little laptop.

Why not? It all depends on his video card. A laptop with his specs could easily have a 128 mb nvidia card, which runs XGL flawlessly.

And yes, you'd be able to install KDE later on. I wouldn't really say it looks better though, just different.

---

### Post by x5452 on 2006-04-14
> Why not? It all depends on his video card. A laptop with his specs could easily have a 128 mb nvidia card, which runs XGL flawlessly.

How can I check what video card if any I have in this, i never figured that out???

> And yes, you'd be able to install KDE later on. I wouldn't really say it looks better though, just different.


Oh, I just thought people got better looking desklets and panels to work in KDE, but half of the KDE stuff I find in the GNOME pages, so I dont know.  There is one thread about 'stealing KDE's eye candy' wasnt sure what all that was about...

Edit: One of these days ill get the quoting thing down, lol

---

### Post by Monster_user on 2006-04-17
I meant to reply sooner, but I have been fighting with a Wifi USB adapter. I finally got it working in Windows though...

To check what kind of Video card you have, just open the Device Manager. I believe it is under the "System -> Administration" menu at the top. That is the case in Dapper Drake.

It should be listed under the PCI devices. Nvidia or NVxx, ATI or Radeon, SIS, i8xx, i9xx, Via, Matrox, etc...
Where those x's stand for numbers. I have only seen an NV18 (NVidia Geforce 4)

---

### Post by AndyCooll on 2006-04-17
Since it's your first go I'd suggest you start with the Gnome desktop just to get a feel of Ubuntu (Gnome is the default desktop environment anyway). Then you can install KDE/Kubuntu by typing:

```
sudo apt-get install kubuntu-desktop
```

Then next time you login as part of the process select your "Session" (which is on the login screen) and take your pick.

:cool:

---

### Post by x5452 on 2006-04-17
I went with the gnome for now, and ill check out the KDE desktop eventually.  I do have two questions though, where are some  good wallpaper sites for the 700m with the 1280x800 resolution? everyone i find is 1024x768 and look not good...  
also how about skins for gaim? anything like that?  I installed the guifications theme thing, but all it does is make little pop ups when people come online?

---

### Post by catlett on 2006-04-17
Go to GnomeArt and GnomeLook they are two web sites about extras (wallpapers,icons,splash screens etc) for the Gnome desktop. Also like the previuos post said it is very easy to install Kubuntu and Ubuntu. After you run the Ubuntu install do sudo apt-get install kubuntu-desktop and "Kubuntu" will be installed. What happens is when you go to the login in screen you click on sessions. You will get the choice of Gnome (Ubuntu) or KDE (kubuntu). It's as simple as that. The only thing (which shouldn't affect you) is it requires another 300+ mb of disk space. The even better part is you don't have to reboot to change desktops. Just log out. You go back to the login scrren. Pick Gnome and your back in Ubuntu. This way you don't have to choose only one.

---

