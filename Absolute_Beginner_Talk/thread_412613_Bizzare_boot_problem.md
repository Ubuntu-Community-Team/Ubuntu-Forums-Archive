---
title: "Bizzare boot problem"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by mmikelst on 2007-04-18
I've been trying to figure out a way to get around a driver problem I've been having (my nvidia card and ubuntu aren't playing nicely) and so I've been booting up from the live CD multiple times (using ver. 6.10). Now, this was all fine and dandy until last night, when I tried to boot up from the live cd aaand


1) it goes to the regular menu (start/install, memtest, etc.)
2) I adjust the graphics settings to something that I know will let me get to the text interface once it crashes (sep. issue)
3) I say "start/install"
4) it starts to load the kernel
5)Computer restarts, goes back to initial boot page for the box (The one where you can access the boot, system setup (F2, F12)).

I booted from the utility partition at one point after this, in an attempt to diagnose the drive itself, the tests came up green, so I  restarted, and then it booted gentoo absolutely no problem (I'd forgotten to remove it after the data reading test). I restarted the computer again later, after playing w/ gentoo for a bit, and it returns to its previous behavior, refusing to allow me to boot up anything. This includes previous live CDs that would work just fine for me (knoppix, etc.), not just ubuntu/gentoo, with which I was having Xwindows errors. I'm additionally worried because if windows decides to up and die, if I can't boot from the CD drive, I'm potentially screwed in a way I don't even want to think about. 

If anyone had any suggestsions/ideas, they would be greatly appreciated!!!:confused:

---

### Post by Terl on 2007-04-18
I am confused a bit.  Can you boot with the cd drive at all?  Have you gone into windows and put a cd in to see if it reads it?  Maybe the cd drive went belly up.

---

### Post by mmikelst on 2007-04-18
That was actually my first thought, but I've checked the CDs while windows is running; it reads them just fine. It just refuses to boot anything from the CD drive...It'll start to boot up ubuntu, then just restart the computer after the kernel loads.:(

---

### Post by sailor2001 on 2007-04-18
how many times have you used that disk? A pressed disk has a limited life usage.....also try and clean the disk with alcohol.........

---

### Post by mmikelst on 2007-04-18
I'd used it about 10 times or so maybe...But the thing is the Gentoo disk, which was doing the same thing, I'd only used 2-3 times, same as the knoppix disk.

---

### Post by Terl on 2007-04-18
What kind of nVidia card do you have?  Better yet, what are the pc specs?

What setting are you trying to enter?  I assume you mean a boot parameter.

---

### Post by mmikelst on 2007-04-18
Specs:

Intel Pentium 4, 2.8ghz (dual)
1024 MB RAM
80GB HD
NVIDIA GeForce FX 5200 graphics card
That's about all I know off the top of my head.

And I just changed the boot parameter from VGA to 800X600 (16), which had been working for my purposes before.

---

### Post by Terl on 2007-04-18
This is odd.  Has this ever let you boot the live cd all the way to the desktop?  The specs seem to show that you should be able to do that.

Did you burn this cd yourself?  Have you always had a problem with it?  If so, redownload and reburn the cd at a slow speed (like 4x or so).

---

### Post by mmikelst on 2007-04-18
I've gotten the gentoo live CD all the way to the desktop once. I'm currently fighting w/ a common nvidia driver problem, so that kept me from getting any further (I mostly just was going to the text command, using sudo nano /etc/X11/xorg.conf and trying to edit that). And yes, I burned all these myself, but until last night, they all worked just fine. 


Unfortunately, I have to go to class now, so there'll be about an hour delay in my response. (thx for the help btw!)

---

### Post by Terl on 2007-04-18
So I can get the big picture:  1) Is ubuntu installed and are you just trying to boot it using the disk?  2)You said you were "playing with Gentoo".  Is it installed or are you just playing with the live cd?

I am confused because I do not understand the "common driver" problem.  Is your video card working as it should when you are in windows?

Have you tried other cd's in the drive from windows?  Try some games, audio, something just to make sure the drive is working.

Are there any other symptoms with the pc?  Anything happening when you are in windows?

---

### Post by mmikelst on 2007-04-18
1) I'm just booting from the live CD, nothing's installed but XP Pro on my computer
2)Just playing w/ the live CD

My video card is working properly when I'm in windows, but ubuntu is, for some unknown reason, trying to use the wrong drivers. I've seen a few other people on the forums having this issue (xwindows crashes immediately on boot), and so I've been going into the xorg.conf file and editing that by hand, which worked fine on gentoo, though I haven't gotten a chance to try it with ubuntu yet. 
I've tried other CDs in the drive and it reads them just fine. The only other symptom is that the CDs won't autoplay unless I actually go into the CD and run the autoplay file.

---

### Post by Terl on 2007-04-18
The autoplay is a windows setting.

Anyway, how are you saving the xorg.conf files if you are running live cd's?  

I believe the live cd's use a vesa driver anyway so your card should be just fine.  I am thinking you should try to burn a new disk and try from that.  If you did write back to the disk when you said your were trying to modify xorg.conf you may have corrupted something.

If you just want to play around (I mean get used to linux) without installing anything major you may want to try PuppyLinux.  It will boot for you like a live cd and will save your settings to your windows partition in a small space right on the windows drive.  It loads into ram and is fast.

---

### Post by mmikelst on 2007-04-18
I'm not actually saving the xorg.conf files at all; i'm just editing them and allowing it to use the new edit. I would think that I had corrupted something, except that the knoppix disk I didn't touch at all, because it always booted fine, which it doesn't do anymore. The reason I've been altering the config file is that I found several threads where people were getting the same xwindows error I was, and that seemed to fix their problem. Also, once I got into the file, it was definitely not using the right drivers (it was using the ones for my integrated graphics card that came w/ the computer, not my Nvidia).

---

### Post by mmikelst on 2007-04-18
Okay..Update time....

My computer apparently is now cool w/ booting from CDs...For no apparent reason. I didn't change anything. At all. At this point I don't care. I'm still having trouble getting into the text cmd prompt for ubuntu, but I'm going to try remaking the CD (I am suspicious of it now, since gentoo and knoppix booted up just fine)...I'll keep you guys apprised of the situation, thanks again!

---

### Post by mmikelst on 2007-04-18
As I type, I am in ubuntu. I don't know why, but my computer is currently allowing me to boot from CDs again, and I figured out how to get around the "Xwindows is incorrectly configured" error:)

Triumph! Thanks for all your help, hopefully i'll be installing it on a partition soon!

---

