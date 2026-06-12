---
title: "[SOLVED] Feisty restart issue"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-07-09
I am running Feisty on a Dell 410, duo core, 2 gig ram, nvidia graphics (the Dell ubuntu offering) when I try to do a restart, it goes down as normal, but when the orange bar in the Ubuntu shutdown screen is gone, it just sits there and never reboots. If I do a shutdown, it goes to that point and the computer turns off as I would expect. I guess two questions:
1) any idea why or where I should look?
2) When it is in this state, is there any command that might get it out of it without pushing and holding the power button until it goes off?

So far, thanks to answers that I have gotten and searches, I pretty much have it working the way that I want. The mouse buttons work like I want (mx Revolution), I have most of the keys working on the MS 4000 kbd, and Beryl seems to be working fine. I have gotten fairly good at getting it working again after I crash the x server ;-)

The restart issue is not a killer, but it is rather anoying.

Thanks for the assistance.

Partially solved, see below

---

### Post by bren on 2007-07-09
see the instructions halfway down post #1

[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

good luck

bren

---

### Post by loserboy on 2007-07-09
That's got Ubuntu preinstalled right? don't forget to report that to the Dell forums or wherever

---

### Post by bren on 2007-07-09
if i read it right this is a problem installing beryl brings....not really dell's fault
the fix i posted above may well work....

bren

---

### Post by dondad on 2007-07-20
I found a thread that suggested adding reboot=b to the grub file and that seems to have fixed the restart issue. It works with both the default window manager and also with Beryl. The "only" issue I know of now is that the screensaver works fine, but the monitor will not shut down after the timeout if Beryl is running. It works with metacity.

Also, FWIW, this is a Dell ubuntu machine, but I reinstalled Feisty from the CD because I repartitioned it to put the home directory on a separate partition and I was not sure how the built-in install script would handle that.

---

