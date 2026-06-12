---
title: "A question about Diablo 2 (applies to all other games as well)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by DanielJackins on 2008-01-03
Hello, I just had a question about running Diablo 2, but I'm sure it would apply to any other game requiring installation, as well.

I currently have Diablo installed on my iPod (acting as an external hard drive) to make for easy installation after the switch from Windows to Ubuntu. I am not very pro-efficient at installing things yet (clearly) and was just wondering if I need the discs to install, or if I could somehow do it by copying the files from my iPod. 

Thanks :)

---

### Post by tzulberti on 2008-01-03
I don't know about other games, but if when you play Diablo 2, you are never asked for cd, then copying the files would be enough.

---

### Post by ~LoKe on 2008-01-03
It might be a nice challenge.  You'll have to run in under wine, and you'll need to apply a no-cd crack, as well.  Copying the directory from c:/program files/Diablo II to Ubuntu should be enough to get it to at least run.  I think there's a guide in the how-to forum section, just search for it.

---

### Post by DanielJackins on 2008-01-03
Do I need a No CD patch? I have the Disc to run the expansion, I've just misplaced the installation discs for the non-expansion.

---

### Post by ~LoKe on 2008-01-03
> **DanielJackins said:**
> Do I need a No CD patch? I have the Disc to run the expansion, I've just misplaced the installation discs for the non-expansion.

I think you might, unless you want to mess around trying to get WINE to detect your CD.  However, it's been a while since I've used Wine + D2, so I imagine there's been some progress on that front.

---

### Post by harold4 on 2008-01-03
Once wine is installed, copy the files into ~/.wine/drive_c/Program\ Files/Diablo\ II/, or whatever path you initially installed the game to before coping to the ipod.  Otherwise, you'd need to change the install path in the WINE registry after first run.

Once the game runs and asks you to insert the CD, just pop in the LoD CD and you should be good to go.

---

### Post by DanielJackins on 2008-01-03
Well the path would have been something like Program Files/Diablo 2, but it was installed in Windows

---

### Post by ~LoKe on 2008-01-03
> **harold4 said:**
> Once the game runs and asks you to insert the CD, just pop in the LoD CD and you should be good to go.

Glad to see things have improved.  I could never get it to detect my CD before.

---

### Post by ~LoKe on 2008-01-03
> **DanielJackins said:**
> Well the path would have been something like Program Files/Diablo 2, but it was installed in Windows

Then it'll be ~/.wine/drive_c/Program\ Files/Diablo\ 2

---

### Post by harold4 on 2008-01-03
> **DanielJackins said:**
> Well the path would have been something like Program Files/Diablo 2, but it was installed in Windows

In that case, just copy to the location I gave in the previous post.

---

### Post by DanielJackins on 2008-01-03
Okay, so everything is copying right now; so far, so good.

Quick question about Wine though. Is it constantly active? If I try to run something (Eg. Steam or Diablo 2) will it automatically be done through Wine?

---

### Post by DanielJackins on 2008-01-03
K all the files are copied, but when I try to run Diablo I get an error stating it is unable to initialize DirectDraw

---

### Post by DanielJackins on 2008-01-03
Anyone?

---

### Post by mattator on 2008-01-03
Try a French project called playonlinux,if I remember well : [www.playonlinux.com](www.playonlinux.com)
hope it helps

---

### Post by DanielJackins on 2008-01-03
Sorry, I'm brand new to Ubuntu and Linux, and have no idea what any of that is, isn't that just WINE?

---

### Post by argie on 2008-01-03
Hey! Diablo II : LoD worked just perfectly fine for me but I haven't tried in a long time. If there's a D2VidTst.exe or something that works as a video test or something then try running that first. It'll give you the choice of 2d or 3d driver. Try it with both of them.

---

### Post by P235 on 2008-01-03
Hi, this is slightly off topic, but how many people have used PlayOnLinux and what are your thoughts?  How well does it work?

---

### Post by DanielJackins on 2008-01-03
The video test said it couldn't detect anything usable, and that my computer can't run Diablo 2, although it has on Windows before. It also says to download the latest version of DirectX, which obviously won't work. Any solutions?

---

### Post by ~LoKe on 2008-01-03
You can actually download the directx 9 installer and run it in wine.  However, PlayOnLinux (POL) will give you the option to do it automatically.  I suggest giving it a shot.

---

### Post by DanielJackins on 2008-01-03
I can't seem to get the install for PlayOnLinux working, it says I am missing something

---

### Post by P235 on 2008-01-03
I just installed PlayOnLinux with the Gdebi Package Installer and everything seems to be in order.

It begins with French on default, but it does have an English version and a German version (I think).  I'll have to try this out later though as I do not have a Windows game on hand.

---

