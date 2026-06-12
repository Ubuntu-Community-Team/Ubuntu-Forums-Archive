---
title: "Live CD Hangs"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Smu on 2007-07-22
Hi!

I've tried to run the ubuntu feisty Live CD on a new Fujitsu Siemens desktop wich has vista. Everything goes smooth until just before the splash sceen, then it hangs. Theres only a beige background and I can move my mouse cursor, but that's it. Tried Ctrl+Alt F2 and Ctrl+Alt+Backspace but nothing had any effect. Does anybody know what might cause this? I've also tried the safe graphics mode and a different Live CD... but without success... 

It seems that this computer doesn't want ubuntu... :confused:

---

### Post by autocrosser on 2007-07-22
You might try reburning the LiveCD at a slower speed--at times this will help. I also F6 on the first screen & remove the "quiet" from "quiet splash"--this allows a dialog at the bottom centre that can help pinpoint your problem.

---

### Post by cobrn1 on 2007-07-22
What are the specs of your computer?

I have a slow pc (733Mhz, 128Mb ram) and the live Cd gets to the same place then freezes. If you don't have enough RAM then it won't like live CDs.

I thinks there are other things that cause live CD's to go wrong, but I'm not sure what they are.

Did you chack the MD5 sig to ensure that you'd downloaded the CD image properly? I doubt this is the cause, but you may as well check...

Also, If you can't use the live Cd you can use the alternate install Cd to install ubunty. This works just fine, but it will install it, so no trialling it out - be sure you want it... Also, it's a text based installer, but that should be OK.


Do you want to keep the vista installation. Id so then use vista's own partition resize facility to change the size of it's partition, otherwise things can go wrong. Then you can use the text based installer to add a new partition + swap partition, or you could download Gparted CD to partitions graphically.

Again, if you are keeping the vista partition, use vista's own tool to resize the ntfs partition, or you will run into a whole world of pain (MS changed the nts spec secretly, and the partition tools we have haven't caught up yet.)

---

### Post by Smu on 2007-07-22
Here's the specs:
AMD Sempron 3400+ 1,80 Ghz
1Gb RAM
ATI Radeon Xpress 1150


I've checked the Live CD and tried 2 different copies, one from last months Linux Format Magazine and the otherone is the official Ubuntu Live CD... I also tried running Mandriva Live and Simply Mepis Live, but without success.

I also tried removing the quiet splash, but everything seemed to be ok. I got no errors. The system hangs just after that, when X is started. I've installed ubuntu on several computers and tried the Live CD and never have I encounter this kind of problem... I wouldn't like to install ubuntu without trying. It's my mother-in-laws computer and I'd like to check first that everything is working correctly... :)

---

### Post by Smu on 2007-07-23
Anyone? :confused:

---

### Post by rillip on 2007-07-23
Mmm, only guess is to try a different resolution.  Maybe they're all fialing because X can't start correctly with your screen. Maybe try adding vga=791 to the boot option

---

### Post by BETOCORELLA on 2007-07-23
Same Problem I Had. Lol Restart It Then When U Get 2 The Menu. Press F4 N Go 2 The Resolution Of 1024 N Someting That Should Work.

---

### Post by Smu on 2007-07-23
Ok! Thanks for the replies. I'll try that!

---

