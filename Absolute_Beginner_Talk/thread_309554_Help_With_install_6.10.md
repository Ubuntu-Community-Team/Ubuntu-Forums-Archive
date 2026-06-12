---
title: "Help With install 6.10"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-11-29
Hi, I downloaded the 6.10 iso (ubuntu-6.10-desktop-i386.iso) to load onto an AMD based PC.  I booted using the CD I created and ran the CD and Mem check from the menu.  Everything checked out.

I then chose the Boot/Install Ubuntu selection.  The splash screen appeared for a while, and then when the screen switched (apparently to load X) the screen filled with garbage.

The good news is the speakers worked and played the music intro.

I tried ctrl-alt-backspace to kill X and got nothing.

If anybody could help out, I'd be greatly appreciative, I'm about to go for the world record distance throw on the cd I burned.

---

### Post by komaroveli on 2006-11-29
can you tell me what videocard do you have?...i had old video card that couldn't load 6.10, but previous versions worked fine. try burning dapper (6.04) and boot it, see what's comes up

---

### Post by taurus on 2006-11-29
Does <Ctrl><Alt>F2 bring you to a console?  If it does, then reconfigure X again with

```
sudo dpkg-reconfigure xsever-xorg
```
Otherwise, download the alternate CD to install Edgy on your machine since it seems that the desktop CD/LiveCD is having a problem with your graphic card.

What's the spec of your machine anyway?

---

### Post by the gnome on 2006-11-29
> **taurus said:**
> Does <Ctrl><Alt>F2 bring you to a console?  If it does, then reconfigure X again with

```
sudo dpkg-reconfigure xsever-xorg
```
Otherwise, download the alternate CD to install Edgy on your machine since it seems that the desktop CD/LiveCD is having a problem with your graphic card.

What's the spec of your machine anyway?

Hi, I never got to the point of installing anything, so it seemed like X was loading from the CD.

My machine is as follows:
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+,  MMX,  3DNow (2 CPUs), ~2.0GHz
Memory: 1022MB RAM
Card name: NVIDIA GeForce 6600 GT
Description: Sound Blaster Live! 24-bit


My machine had a drive with 5.10 up and running, but it got ruined when upgrading to 6.06.  I haven't had time to play with getting that fixed, so I figured I'd start fresh from 6.10.

Unfortunately I cant even get to the point from the CD to get prompted to reformat the disk or do the install.

Thanks for the help!

---

### Post by syrleb on 2006-11-29
hmmmm, hit your computer about three times, kick it twice then swear at it for 15 minutes, usually fixes all my problems

---

### Post by the gnome on 2006-11-29
LOL I'll do that if I don't chuck the monitor out the window in the next 5 minutes.  I'm downloading 6.06 now.... hopefully that fixes things.

The real bummer is I think the mainboard is an nvidia chipset too.

---

### Post by the gnome on 2006-11-29
> **the gnome said:**
> LOL I'll do that if I don't chuck the monitor out the window in the next 5 minutes.  I'm downloading 6.06 now.... hopefully that fixes things.

The real bummer is I think the mainboard is an nvidia chipset too.

Nope, 6.06 didn't work.  The nvidia drivers are not installed, I dont know why the install doesnt see I have an nvidia vard and just go to a non-graphical install sequence like 5.10 did.

Oh well, looks like Vista is in my future.

---

### Post by taurus on 2006-11-29
Why not try the alternate CD?  

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by the gnome on 2006-12-01
Hi, and thanks for the tip Taurus.  I had to walk away from this for a couple of days and come back.  The alternate image installs using a non-graphical routine, which is exactly what I needed.

I then could boot up in terminal mode, install the Nvidia drivers, and things started working.

The only problems I'm having now are getting all my mouse buttons/wheel to work, and get sound.


Safety Tip:  For those new to Linux who are trying an Ubuntu install, doing so with the flu and on cold medication should probably wait until they're well lol.

---

