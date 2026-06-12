---
title: "Wine"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-12
I have installed Wine. I'm thinking that there must be something wrong with me because I don't know how to use it. Here is a list of the games that I have that I would like to consider playing in Linux. If not, I guess I can just play them in windows if I have to. I still have XP installed. If they run better in windows, I suppose that would still be the way to go. 

Command and Conquer 3 - Tiberium Wars

Command and Conquer - Decades ( I really only play Zero Hour or Generals for the most part)

Civilization III Complete

Civilization IV and the Warlords Expansion Pack

Doom 3 (I understand that I could play this in Linux without Wine, but I honestly don't have the foggiest idea how to.)

Tiger Woods PGA Tour 2008

---

### Post by Maestro23 on 2007-11-12
Check the Wine App DB to see if your games will run and if there are any issues with them under Wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by oneadvent on 2007-11-12
Someone else can tell you if those specific games work or not, because all I play is diablo ii lod....however.

This is how you install games (or other aps) via wine.

Insert the cd. 

notice on the top bar it tells you the location, ie /media/cdrom0

goto a terminal, and type cd /media/cdrom0

then locate the install exe...most of the time it is setup.exe

type wine setup.exe

let it set it all up. Once that is done it should show up on your main menu under wine.

Good luck, let me know if you have trouble.

Josh

---

### Post by asbani on 2007-11-13
I just installed generals & zerohour via wine. it worked fine. except few known bugs and there are patches for them aswell. here are the steps.

1. Download msvcirt.dll and put it in your .wine/drive_c/windows/system32 directory
2. Copy both CD's to your harddisk into the same folder.
3. Install Command & Conquer Generals from your harddisk using wine setup.exe
4. Once the installation is done, find yourself a no-cd crack and replace the original game.dat and generals.exe with the cracked ones.
5. Start winecfg and, go to the Graphics tab, and at the bottom in the Direct3D area set Vertex Shader Support to none and unthick "Allow Pixel Shader" otherwise the world won't show but just the buildings.
6. Go into the Data folder and rename the folder Movies or delete it.
7. Next go into the english folder (sub-folder from data) and either rename or delete the Movies directory from there aswell.
8. Go back to your Generals Installation directory and launch the game using wine generals.exe
9. Go to the Options Menu. In the Display Options Area, Set Detail to Custom. A new window will pop-up. Make sure you unthick Extra Ground Lighting there to fix the bug that certain parts of the ground aren't showing.
10. Have fun playing the game! :D

same goes for generals and zerohour. Make sure you copy the files from disc1 and disc2 to your /home/org/cncgames or somewhere.

---

### Post by bgast1 on 2007-11-13
Unfortunately, I have Command & Conquer Decades. I will have to do more research on that or just do like a lot of people. When I want to play games, boot windows. I have to keep windows on my hard drive anyway for my wife or until I get around to fooling with a Virtual drive, or get a new computer. Haven't decided whether I am going to just go buy one or build one. I lost track of what processors are out there, what sort of socket they fit into etc.  since the last computer I built was a P3. Although I have upgraded the one I have quite a bit. Shouldn't be too hard to build another one. For sure though if I want to continue to play games, I am going to have to upgrade beyond what my present computer is capable of. 

One question though. Does Linux support crossfire or SLI? Is there really a need for 2 video cards yet, even in Windows?

---

