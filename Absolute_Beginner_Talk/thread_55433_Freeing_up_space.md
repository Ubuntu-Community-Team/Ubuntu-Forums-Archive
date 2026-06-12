---
title: "Freeing up space"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by anwarlorenzo on 2005-08-08
Hi! I've got winetools installed from source and I want to uninstall it.
I feel that my computer is so cluttered with so many useless files lying around and I'm wondering how do I free up some space and remove files that I don't use? Is there a program that automates this?

---

### Post by fng on 2005-08-10
Linux, compared to wndows,  doesn't slow down when there are a lot of programs/files installed.

But if you still want to free some space :
- remove programs you don't use anmymore by 'apt-get remove program'
- clear all the downloaded files by apt by 'apt-get clean'
- clear firefox's or any other browsers cache (look for it in the options)
...

I'm sure there are more people with other tips for freeing up some space (e.x. /var/cache and /var/tmp)

Edit : typo :)

---

### Post by KingBahamut on 2005-08-10
[QUOTE=fng]Linux, compared to wndows,  doesn't slow down when there are a lot of programs/files installed.

But if you still want to free some space :
- remove programs you don't use anmymore by 'apt-get remove program'
- clear all the downloaded files by apt by 'apt-get clear'
- clear firefox's or any other browsers cache (look for it in the options)
...

I'm sure there are more people with other tips for freeing up some space (e.x. /var/cache and /var/tmp)[/QUOTE]
 actually thats apt-get clean and apt-get autoclean

---

### Post by TristanMike on 2005-08-10
[QUOTE=KingBahamut]actually thats apt-get clean and apt-get autoclean[/QUOTE]
Hi, thanx for those two commands, but what is it that they do, clean obviously, but what are they doing.
Sorry for a garbled question.
Thanx

---

### Post by KingBahamut on 2005-08-10
clean and autoclean take care of the unessecary storage of deb files in your apt cache. Sometimes , specially if you install large files say like VegaStrike (150meg I think), they can take up some space.

---

