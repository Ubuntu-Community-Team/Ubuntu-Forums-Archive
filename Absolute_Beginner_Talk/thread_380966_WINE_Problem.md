---
title: "WINE Problem"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by andrewlinn957 on 2007-03-10
Attatched is the screenshot i get when i try to install DCOM98... please help, i dont see how i can clear the IE browser cache when i dont have IE on my Ubuntu partition.. does it mean my Windows IE partition?

[ATTACH]27070[/ATTACH]

---

### Post by Perfect Storm on 2007-03-10
Don't use winetools (it's buggy and outdated). clean it all up (also the stuff in ./wine in your home folder). Reinstall wine and type **winecfg**

---

### Post by andrewlinn957 on 2007-03-10
Thanks! do i have to remove any programs with synaptic or abything?

---

### Post by Perfect Storm on 2007-03-11
Well, if you installed wine and winetools through synaptic. Also in your home folder there is a .wine folder (for personal settings, application etc), it's hidden (when there's a . infront of a file or folder it's a hidden one).

---

### Post by macozz on 2007-03-12
Hi,
I tried to follows the suggestions in this thread, but no look.
The last wine version that works is 0.9.5. Versions 9.22 (original Edgy version) freeze my system and posterior version (both from backports ans winhq) produce just an error message, a debug list , and quit).
The only solution I find was stick to 0.9.5, but I'd like to update wine as new releases comes up, and, of course, why it is not working for me and apparently works fine for others...
I am running a laptop (ClevoM540V), with Celeron M 1.30 GHz, 256MbRAM, graphic card  VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter, with up 64Mb dynamically shared memory, 40GbHD and Ubuntu 6.10 updated (except for Wine, of course... ;-))
Thanks!

---

