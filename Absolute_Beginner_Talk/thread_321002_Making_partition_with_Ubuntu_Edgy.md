---
title: "Making partition with Ubuntu Edgy"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2006-12-18
Hello

Right now I am running the live cd with Ubuntu Edgy (6.10). I want to make a dual boot, so I can use both Windows XP and Ubuntu.

I choose "Install". In the 5. section I have the opportunity to resize my harddrive. I want to have most space on the Windows-part, like I have maybe 50 GB on Ubuntu and 150 GB on Windows XP.

The question: When Ubuntu automatic resizes the harddrive, how can I know, how much Ubuntu uses? I have taken a screenshot. It says:

"36% (12.6 GB)"

Is that what UBUNTU will use or what my WINDOWS XP will use?
Thanks

---

### Post by taurus on 2006-12-18
The best way is to use gparted from the LiveCD to resize your harddrive first, making room at the end for Ubuntu.  Then, install Ubuntu and tell the installer to use that empty space.  That way, you can create whatever amount you want to use with Ubuntu.

---

### Post by Wikzo on 2006-12-18
I am not so good at harddrives, boot etc. Therefore I want to use the easy automatic partition installer in Ubuntu. I just wanna know, that the bar on the button is what Ubuntu uses or Windows XP?

I can scroll the bar from 12% to 100%. I think, it is what Ubuntu can use, but I need to be 100% sure first.

---

### Post by taurus on 2006-12-18
If I have to guess from the screenshot, I would say the percentage of your harddrive that Ubuntu will use.

---

### Post by matt_risi on 2006-12-18
Hey I've had quite a bit of experience dual-booting and such, so here's what I do that seems to work.

1) Wipe drive.
2) Install Windows.
3) Use the Knoppix Live CD, using qtparted to partition the drive (gparted is absolute crap in my experiences)
4) Install Ubuntu

If however, you already have a working windows install and don't want to wipe your drive, defragment your windows install, then continue the above process from step 3.

---

