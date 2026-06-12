---
title: "Initramfs error"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Veggieb0i on 2007-02-21
Well, I'm having a problem with Ubuntu 6.10, installed from the live cd onto a fresh, reformatted drive, using the "Erase entire disk" option from the installation.
The problem is, the Ubuntu logo shows for about a second, then it switches to a console screen and lists an error; something like: "Initramfs unable to access jobs" and something to do with TTY, or an abbreviation like that.
I've heard this is a fairly common problem with live cd installations, so I'm kind of assuming someone might know what I'm talking about without me having to describe it completely.

EDIT: here's a thread about the same problem: [http://ubuntuforums.org/showthread.php?t=340398](http://ubuntuforums.org/showthread.php?t=340398)

But here is my situation:

I am an ignorant fool with no prior Linux experience, and 12 years of Windows experience. I am also sixteen.
I have two hard disk drives, one of which contains nothing but Ubuntu 6.10.
The other is running Windows XP normally.
The Windows drive is in the 'master' setting, and the Ubuntu one is in the 'slave' setting.
I built this computer wholly from parts off of Newegg with no prior computer engineering experience, but it has been running fine for over two years.
I reinstalled Ubuntu after this happened the first time (yesterday), but I got the above error after rebooting. Basically, I'd be more than happy to completely reformat the drive again if that would fix it.
I have made no changes to Ubuntu since its install, no new settings, no files whatsoever.
I can switch the 'master' and 'slave' settings on both drives with no stress.
I can remove the Windows XP drive if that would fix it.
I have as much time as it would take to download and install the non-live version.
I have no experience with the command prompt thingy.

So, can anyone help me from this? I can give more information if you'd like.


EDIT: Oh yeah... I forgot to say, I'm running the 64 bit edition of ubuntu: **ubuntu-6.10-desktop-amd64**

---

### Post by lhtown on 2007-02-22
I have never had that particular problem, but from reading about others problems, maybe you could try the alternate install CD and when it give the option to use LVM, use the other option whatever it is called. There are certain advantages that LVM has for power users, but you don't need to worry about it.

I don't know if that would help or not, but it wouldn't hurt to try. Also, the Live CD is really good, but the Alternate CD is said to work sometimes when the Live CD hiccups.

You could also try removing your Windows drive and installing Ubuntu with only one drive attached to see if it works.

---

