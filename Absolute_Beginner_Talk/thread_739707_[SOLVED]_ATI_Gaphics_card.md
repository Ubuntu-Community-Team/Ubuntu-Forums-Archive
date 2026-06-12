---
title: "[SOLVED] ATI Gaphics card"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-30
Can someone walk me through updating my ATI Radeon Express 1100 graphics card so i can get full use including 3D out of it. I have read tutorials and searched threads but was confused on how to go through the upgrade.

---

### Post by c-ron on 2008-03-30
Use the Envy script:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

PS: Nice username!

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **c-ron said:**
> Use the Envy script:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

PS: Nice username!

Thanx and I love the avatar :)

---

### Post by chewit on 2008-03-30
I have recently just done a blog post on getting ATi Radeon cards with full 3d acceleration

[http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/]("http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/")

---

### Post by Saint Angeles on 2008-03-30
installing mesa is really not that helpful...

i'm sure the OP wants to get direct rendering rather than indirect...

go to the ati website, download the latest ati driver for your card...

goto a terminal and type: ```
sudo sh ati[tab]
```
tab will autocomplete the filename...

i will post a copy of my /etc/xorg.conf file just for your benefit.

also, search these forums for ati advice because theres all kind of helpful folks that have already encountered your problem and fixed it.

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **Saint Angeles said:**
> installing mesa is really not that helpful...

i'm sure the OP wants to get direct rendering rather than indirect...

go to the ati website, download the latest ati driver for your card...

goto a terminal and type: ```
sudo sh ati[tab]
```
tab will autocomplete the filename...

i will post a copy of my /etc/xorg.conf file just for your benefit.

also, search these forums for ati advice because theres all kind of helpful folks that have already encountered your problem and fixed it.

i will gladly give this a try - the info i have followed so far has REALLY screwed up my computer. pages load SLOW move extremely jerky, like on a computer running 64mb of ram - when i click on the tools link in firefox it turns to pure garbled garbage. lines flash across the screen and desktop will flash all crazy like when linux is loading up into low graphics mode. I will post when i have completed.

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **c-ron said:**
> Use the Envy script:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

PS: Nice username!

Envy  got rid of    all the messed up crap that had happened to my computer - no to try  the 3D out -     hopefully............

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **c-ron said:**
> Use the Envy script:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

PS: Nice username!

DUDE you ROCK!!! I finally have 3D, Envy is the sh*t!  now to work on Compiz.....

---

### Post by c-ron on 2008-03-30
> **N1N31NCHN41L5 said:**
> Thanx and I love the avatar :)

Created in The GIMP. Good stuff.

---

### Post by huntwell on 2008-03-30
I also found Envy to solved all my problems. I didn't have to go through all the bs of long and complicated terminal commands found in wikis and other posts. 

Not that the people posting solutions to getting ATI cards running 3D effects are doing a bad job and aren't very helpful, but Envy was by far the easiest process.

Ciao

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **huntwell said:**
> I also found Envy to solved all my problems. I didn't have to go through all the bs of long and complicated terminal commands found in wikis and other posts. 

Not that the people posting solutions to getting ATI cards running 3D effects are doing a bad job and aren't very helpful, but Envy was by far the easiest process.

Ciao

After the envy install I installed Copmiz-Fusion and have ALL the cool 3D effects now from drawing fire to the rotating and spinning cube. A few Windows Vista users have alraedy commented on the new look and are almost ready to try Ubuntu out now. The goal for today: 1 more Linux convert and ubuntu install for dual boot.

---

