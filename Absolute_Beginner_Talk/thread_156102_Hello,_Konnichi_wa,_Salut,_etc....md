---
title: "Hello, Konnichi wa, Salut, etc..."
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Kyuketsuki on 2006-04-06
Hello! I'm obviously new to the forums here, and admittedly to linux itself, so I thought I'd introduce myself. Where to start... I've attempted to use other distro's, DSL ( [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org) ), gentoo (x64 ed), and knoppix (from cd only). Gentoo didn't work out too well since a friend started the install for me, got me to the point of compiling the kernel, then had to go back to college (I've tried to compile the kernel, it's just I can't seem to get command line down correctly to make it work after that point). So I gave up on that as it gets me nowhere. DSL was nice, only 50MB, but didn't feel like it was a full-blown OS, so I'm reserving it for portable use such as on USB pen drives. And knoppix, well, it works, I'll leave it at that.

So here I have a gentoo installation (dual-booting with WinXP Pro, Windows works, gentoo doesn't) that I can't use sitting on a 20GB partition, and another 40GB in FAT32 for sharing. I Figured since I can't get gentoo to work I have 2 options: A) Find a linux distro to replace it that's easy to install (seems like this one). Or B) Wipe the partition, fixmbr, get all my space back for windows, and wait till I buy a case for these spare parts I have laying around ('C' would be install in dual-boot with winxp home, but I'll touch on that soon).

Now here's where the fun begins. I hang out for a day, read the forums, see the complaints/fixes/praise/guides/whatnot on the site and forums. I download the CD's (x64 and x32), burn'em, and boot. Detects just fine, get a nice welcome screen... well, "welcome" as in the Ubuntu logo and a scrolling load screen below it. I don't see any errors anywhere, but when it's done I'm left with:

[IMG]http://skittle.vullcan.net/images/MsgBoardStuff/PICT0783.JPG[/IMG]

At first I thought "Okay, it's just taking time because it's loading from a CD" so I go do something else for 30 minutes (lunch time!). I come back, CD's not spinning, no system activity.... same screen. So I try the x32 disk, same thing. I took the x32 disk down to my other computer (800Mhz Asus C3 Terminator) and it boots fine, albeit a little slower than my main system was going, and the only thing that didn't work was the Microsoft wireless network adapter.

All in all, not too bad of an experience. It seems like a pretty nice distro and I'll definitely (at the very least) install it on the next machine I build. I threw out the problem I had in case someone has already run across this and knows an easy fix, but I'm really in no rush to get it working on this machine (After my experience with DSL I didn't expect linux distro's to run very well on my main system). However, I would like to confirm a couple things: First, Ubuntu automatically configures the dual-booting itself during install? Or am I mis-interpreting? Second (the stupid one), I have partitions C through M on windows, K (sdb7) is the linux partition, breaking that up into a linux partition and a swap partition would just make a drive 'p' and not mess up windows, correct? (N and O are dvd drives). Those are just questions in case I fiddle around and figure out how to get the liveCD to work on this system.

Anyway, guess my intro was a tad long! Hope to learn much about linux here! :-D 

~Kyuketsuki~

---

### Post by sailor2001 on 2006-04-06
I dual-boot on 2 boxes...When installing ubuntu, I manualy partition (after defraging windows ..important) swap file should be 2 1/2 size of your ram..no need for any more. everything worked perfect..........remember to sudo apt-get update when finished.

---

### Post by Kyuketsuki on 2006-04-06
Hmm.. Whatever seems to be keeping Breezy from working on my machine doesn't seem to be in dapper (I'm writing this from the dapper liveCD), though it seemingly can't do anything with most of my partitions... Oh well, I'll have plenty of time to check that out later. So I guess I just wait until the next release! :mrgreen: 

~Kyuketsuki~

---

### Post by Mustard on 2006-04-06
Welcome to the world of Ubuntu. :)

On the subject of your screenshot above.  I would suspect that the live CD attempted to use drivers for your graphics card and failed.  **If you could get to a command line (using the ctrl + alt + f1 keys) at the point that it is at in the screenshot**, you could probably configure the live CD to use the 'vesa' drivers, which are a generic driver, rather than a card specific driver.  To reconfigure your xorg.conf file you would do this...

First lets make sure that the gnome desktop manager is shutdown..

```
sudo /etc/init.d/gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
#instructs the system to reconfigure the xserver-xorg packages
#configurations settings
```

A dialog will be started in which the best answer is usually the default answer that is already selected.  Since you only want to change the graphics drivers you wait till it comes to the driver dialog and choose the 'vesa' option.  Then continue with the dialog until it finishes.

After the dialog is finished, to start the 'xserver' (the graphical display), you could try either of these commands.

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

---

### Post by Mustard on 2006-04-06
Heh..someone else with a similar problem, but slightly different look in this thread. :)

[http://www.ubuntuforums.org/showthread.php?t=156297](http://www.ubuntuforums.org/showthread.php?t=156297)

---

### Post by Kyuketsuki on 2006-04-06
Thanks for the help! I tried Mustard's solution, it didn't go so well. Seems all I can do when I get to that screen is amuse myself by playing with the mouse (which moves a lot faster than it does in windows, if that's any consolation :mrgreen:  ), and hit the reset button on the case. It doesn't bother me since I know (for the moment anyway) that the next release will work nicely, and it's only 2 months away (not long for a college student :p  ).

In the meantime I suppose I'll be playing with the dapper liveCD! :cool: 

~Kyuketsuki~

---

