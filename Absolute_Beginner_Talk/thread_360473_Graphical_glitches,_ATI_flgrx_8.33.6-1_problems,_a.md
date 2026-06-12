---
title: "Graphical glitches, ATI flgrx 8.33.6-1 problems, and general install problems"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by haec on 2007-02-13
Hello there. 

I'm trying to install Wine and I have been getting this error message:

E: graphviz-cairo: subprocess post-installation script returned error exit status 127

This occurred on multiple tries, whether I use a Package Manager or not. And I am also getting this error when I try to install Bittorrent files and the GUI through Synaptic, however, I have been able to install other programs without the problem.

Furthermore, I am having problems of a graphical nature too. I thought installing 8.33.5-1 would help the fact that when I scroll in browsers e.g. Firefox etc that I get jerkiness, but I couldn't install it I kept getting this terminal output:

Unpacking replacement fglrx-driver ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /media/sda2/LINUX DRV/fglrx-driver_8.33.6-1_i386.deb ( - - install):
 subprocess dpkg-deb  - -fsys - tarfile returned error exit status 2
Starting stieventsd: done

So I downloaded an earlier version 8.28.8-4 which seems to install fine but doesnt get rid of the glitchiness when browsing. My system also boots into the Ubuntu screen with nasty graphical glitches too.

please help i'm having a hell of a time 

thanks.

---

### Post by Jussi01 on 2007-02-13
Hmm, Try Envy it may just fix those graphical probs with the correct driver. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Hope this helps.

---

### Post by haec on 2007-02-13
Thanks for the suggestion. Tried Envy, but it hasn't helped even when I sorted the repositories and pressed ALT+F1; it just made the machine hang.  :(

---

