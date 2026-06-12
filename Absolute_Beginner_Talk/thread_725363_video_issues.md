---
title: "video issues"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by windows hater on 2008-03-15
hi 

im having issues playing videos off of firefox youtube and myspace videos they dont work 
and i installed the flash using add/remove and it still doesnt work


can someone help me!!!!!

---

### Post by freebios on 2008-03-15
did you install restricted extras as well?  if you didn't install that package this should solve your problem

---

### Post by ghost_ryder35 on 2008-03-15
> **windows hater said:**
> hi 

im having issues playing videos off of firefox youtube and myspace videos they dont work 
and i installed the flash using add/remove and it still doesnt work


can someone help me!!!!!
did you do a restart of the comp after the install of the flash?  If that doesnt work, try installing the alternative flash that firefox gives, I belive it is Gnash

---

### Post by windows hater on 2008-03-15
umm how might i find that out if its restricted

---

### Post by ghost_ryder35 on 2008-03-15
add/remove under accessories

---

### Post by jan quark on 2008-03-15
try this in terminal
```

sudo apt-get install ubuntu-restricted-extras
```
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by windows hater on 2008-03-15
now i gett a picture but its really all distorted and the play bar is moved around flashing add when i try to unstall flash i get "dpkg --configure -a to correct"

---

### Post by billgoldberg on 2008-03-15
Try downloading the .tar.gz from the adobe website.

Right click the .tar.gz and choose "extract here".

In the folder that it creates there should be a installer.sh file (or some other .sh file) double click that and run it in terminal if it asks so. 

(you might have to right-click the .sh file, go to properties, permissions and tag the "allow execution ..." box.)

---

### Post by robertchahine on 2008-03-15
go to the adobe website and download the package of the flash player (.tar.gz) 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)


then right click on the pacakge->extract here.
open the folder and click alt+F2 browse the file in the folder of the flash player and mark "run in terminal"
so you install properly the falsh player for firefox.
then restart firefox.

---

### Post by windows hater on 2008-03-15
thnx a million 

it works finally i can enjoy youtube !!!!

---

### Post by natirips on 2008-03-15
If your're using a 64-bit computer, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

It tells how to properly install flash on a 64-bit machine. If your're using a 32-bit computer, some of those posts above were supposed to work, so in that case I'll be of no use to you (unfortunately).

Edit: Lolz, you solved your problem just the second before I posted this meaningless post.... :)

---

### Post by robertchahine on 2008-03-15
> **windows hater said:**
> thnx a million 

it works finally i can enjoy youtube !!!!

i'm glad that it works

remember to mark this thread as solved:popcorn:

---

### Post by windows hater on 2008-03-15
im sry but i have another question unrelated i cant update and when i do

SOFTWARE INDEX IS BROKEN

it is impossible to install or remove any software please use the package manager "synaptic" or run"sudo apt-get install -f in terminal to fix this issue 

well when i do it it doesn't work

---

### Post by robertchahine on 2008-03-15
did you change the permission?
and does the "sudo" works normal?

---

### Post by windows hater on 2008-03-15
yea sudo works

---

### Post by robertchahine on 2008-03-15
did you upgraded the operating system from dapper to feisty or edy to feisty?
and can you open the synaptic?

---

### Post by robertchahine on 2008-03-15
i thnik it's a bug

---

### Post by robertchahine on 2008-03-15
try that : launch Synaptic Package Manager, select "Broken" from left column, and then and then click the checkbox next to "linux-restricted-modules-generic" in upper window and click on "Apply" to update package.

---

