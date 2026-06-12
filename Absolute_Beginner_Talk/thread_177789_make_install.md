---
title: "make install"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Artist22405 on 2006-05-16
I am new to linux so bear with me plz 
I am wondering if anyone can piont me to a web page for installing things from the command line 
I downloaded super tuxcart and would really  like to install it but when I unzip it I get all the iles like install-sh  the config files
but then I am stuck I know what the termanil and root termanil but I just dont know what the commands I am supose to use when installing a new program

---

### Post by aysiu on 2006-05-16
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

---

### Post by johnc4510 on 2006-05-16
This might help:
[http://ubuntuforums.org/showthread.php?p=990636#post990636](http://ubuntuforums.org/showthread.php?p=990636#post990636)
My only question is, why did you not use synaptic to install this game.
It looks like it is the lastest version
good luck

---

### Post by Artist22405 on 2006-05-16
I havent used synaptic because its not in there I try to use that whenever I can

---

### Post by johnc4510 on 2006-05-16
Um, it's in mine, either breezy doesn't have it or you don't have universe multiuniverse enabled. You are breezy right?

---

### Post by Artist22405 on 2006-05-16
umm no I am using dapper I liked the artwork to much I used breezy for like a week love ubuntu aint going back to windoze just gonna learn all I need to like the command line

---

### Post by dmizer on 2006-05-16
[QUOTE=johnc4510]My only question is, why did you not use synaptic to install this game.[/QUOTE]
i made this mistake alot too at first.  remember, with windows ... if you want to install a program, you have to go find it, download it, and run the executable and walk through a wizard.

so out of habit, when looking for new software in linux, you go to the web, and sure enough, the program is out there, so you use windows logic and go from there.

but in debian based linux distros, most all of the software is available right from your package manager.  looking at it from a windows point of view, it's a little like going to start > controll panel > add/remove programs ... then searching for your program you want to install, and installing it.  skipping the whole 'find it on the web and download it' step.

---

### Post by johnc4510 on 2006-05-16
Correct, and like I said before, it is in synaptic on my dapper

---

### Post by flaak_monkey on 2006-05-16
what about for KDE? How do you install in  Kbuntu?

---

### Post by dmizer on 2006-05-16
[QUOTE=Artist22405]I downloaded super tuxcart ... [snip][/QUOTE]
i think i see your problem.  when you searched in synaptec, did you search for tuxcart or tuxkart?  the actual program name is tuxkart.

edit ...

so to install with command line, just type: sudo apt-get install tuxkart

---

### Post by aysiu on 2006-05-16
Are you talking about SuperTux or TuxKart?

Or is there really a game called SuperTuxCart?

Well, both SuperTux and TuxKart are in the Dapper repositories (see attached screenshot).

---

### Post by Artist22405 on 2006-05-16
ok 1 verson is in the repostories and yes I install it thruogh th epackage manager umm thats right I cant spell 
there ver I downloaded is super tuxkart newer graphics I found it through linux game tome 
root@paulsputer:/home/paul# /home/paul/Desktop/supertuxkart-0.0.0-1/install-sh
/home/paul/Desktop/supertuxkart-0.0.0-1/install-sh: no input file specified
this is the first error I get I know there are more to come but one thing a time

---

### Post by aysiu on 2006-05-16
```
cd /home/paul/Desktop/supertuxkart-0.0.0-1/
chmod +x install-sh
sudo ./install-sh
```

---

### Post by Artist22405 on 2006-05-16
root@paulsputer:/home/paul# cd /home/paul/Desktop/supertuxkart-0.0.0-1/
root@paulsputer:/home/paul/Desktop/supertuxkart-0.0.0-1# chmod +x install-sh
root@paulsputer:/home/paul/Desktop/supertuxkart-0.0.0-1# sudo ./install-sh
./install-sh: no input file specified
not yet I think I need a good terminal command dictionary 
I used to know tons and tons of dos commands then I got lazy with windows

---

### Post by dmizer on 2006-05-17
wow ... talk about bleeding edge.  the home page for super tuxkart says it's not really meant to be playable yet.  there's not even a 1/2 version for it yet ... current version is 0.0.0-1.

i don't mean to discourage you or anything, but you sure you really want to install this?  i understand if you want to help with development of the game, but you're risking alot of crashes and bugs that will give you alot of headaches.

---

### Post by ShAdEd_PaSt on 2006-07-30
> **dmizer said:**
> i think i see your problem.  when you searched in synaptec, did you search for tuxcart or tuxkart?  the actual program name is tuxkart.

edit ...

so to install with command line, just type: sudo apt-get install tuxkart

That tho... that installs tuxkart he wants super tuxkart which is truly not in synaptic or apt-get

---

### Post by ShAdEd_PaSt on 2006-07-30
It's not currently being worked on the project was ditched you should give up
"i won't lose you al i can't give till make everything right again" -FMA Edward Elric Ep:?

---

