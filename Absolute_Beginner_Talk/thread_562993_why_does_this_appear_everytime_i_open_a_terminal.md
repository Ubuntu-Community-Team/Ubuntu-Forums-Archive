---
title: "why does this appear everytime i open a terminal?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by RaviJ on 2007-09-29
Hi
  I was trying to install a opensource CFD software which required me to do something with bash. Though after the whole installation process i'm not able to run the software, i got an additional problem. everytime i open a terminal the following appears:

bash: /home/ravi/OpenFOAM/OpenFOAM-1.4/.OpenFOAM-1.4/bashrc: No such file or directory
bash: /home/ravi/OpenFOAM/OpenFOAM-1.4/.OpenFOAM-1.4/bashrc: No such file or directory
ravi@ravi-desktop:~$ 

These two lines have become an eyesore. how to get rid of them?
thanks a lot in advance

---

### Post by Kingsley on 2007-09-29
Just remove whatever you added to ~/.bashrc

---

### Post by dwhitney67 on 2007-09-29
Or ensure that the path leading to the file is correct.

[FONT="Courier New"]bash: /home/ravi/OpenFOAM/OpenFOAM-1.4/.OpenFOAM-1.4/bashrc[/FONT]

probably should be

[FONT="Courier New"]bash: /home/ravi/OpenFOAM/OpenFOAM-1.4/.bashrc[/FONT]

---

### Post by southernman on 2007-09-29
It's always best to fix a problem, rather than put a band-aid on it.

---

### Post by RaviJ on 2007-10-01
Hi thanks removing those lines helped me, now as suggested by others i'll try to see into the problem and try to run my software successfully

---

