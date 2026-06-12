---
title: "DMA activation left system unbootable"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by nsa_767 on 2005-09-04
Hi there,

I've made a big mess of my system.... I followed the unofficial Ubuntu guide's instruction on speeding up my CD-ROM and now the system won't boot.

I am able to boot into recovery mode, but I'm unfamiliar with console commands. I'm unable to start the X-windows system with the command startx.... Guess I need to fix things from within the console-only.

I need to edit and undo the changes I made to the hdparm.conf file. Clearly, I can't use gedit, since I can't run X. What do I use?

I know there is something called vi or vim? But I also understand that it is quite difficult to use....

Any help whatsoever will be appreciated.

---

### Post by bam on 2005-09-04
yes learn to use vim, its not that difficult to use. Just remember there a few things 
1. esc key=command mode, 
2. pressing the letter i after say the escape key puts you in text insertion mode.
3. when done with edit press "esc" key(command mode) then ":" , "w", "q" that way the work gets saved.
4. to save without changes ":", "q", "!"


any more then I will have to look it up, and arrow keys work well.

---

### Post by nsa_767 on 2005-09-04
Thanx bam.... Got the system back up and running... 

BTW, there really should be a howto aimed at this sort of thing.... You know, a howto describing the basic console tools users need to know in order to "fix" things when they go wrong....

Anyway, thanks again for all your help.

---

### Post by rafakl on 2005-09-04
for that problems, download emacs, its a powerful text editor and is more easy to learn than vi.

sudo apt-get install emacs

 :razz:

---

