---
title: "Duel Booting without the OSX"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by Garrulousbrevity on 2008-11-27
So, I have a second generation Macbook, and at the current moment it has Ubuntu and Windows XP Pro SP 3 on it.  I do not have OSX on this computer.  The computer is about two years old, and about a year and half ago I installed Ubuntu.  I did use Bootcamp, and I did intend to duel boot, but I ran into some problems, and instead of giving myself a headache, I just ditched OSX.  More recently, I tried to play a game on this computer (City of Heroes), and the game just froze before it could get to the login screen.  I tried playing with the video drivers a bit, but to little success.  Ultimatly, I tried installing XP to see if the hardware was even capable of playing the game (I was thinking that if I couldn't play the game the way it was intended to be played, that I didn't have much hope for playing it through Wine). 

To install Windows I used a Gparted live disk to make a 40 gig empty partition, and then a windows install disk to fill the empty partition. 

Well, it worked.  but now I can't boot back into Ubuntu.  If I leave the computer to its own devices, the computer goes directly from the 30 second gray screen into Windows. If I hit "Options" (or alt), I only get the option of booting into the windows partition.  It would be nice if I could duel boot, at least until I can get this game working in wine.

However, if I can't get that done (because I do need to be in Ubuntu by Saturday), I was wondering if using GParted to nuke the windows partition would work.

---

### Post by pxwpxw on 2008-11-27
I think windows has written its boot code over what was the grub bootcode for ubuntu.
If so, you need to run a ubuntu rescue disk and reinstall grub, then the grub menu should be automatically updated and boot ubuntu or windows.

However, if you dont have Macosx or refit, you will need to download the refit CD to sync the msdos partitoning table (MBR) to the GPT tables used by ubuntu.(use the refit partioning tool)

Alternately, if you can get ubuntu running - 

```

$ sudo apt-get install refit
$ sudo gptsync /dev/sda

```

I think its a bad move to lose macosx, unless you go to a fully msdos partitioned drive.

---

