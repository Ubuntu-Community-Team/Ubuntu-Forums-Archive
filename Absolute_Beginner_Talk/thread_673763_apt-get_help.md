---
title: "apt-get help"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Rhift on 2008-01-21
Ok so here is the deal, 
I just installed Ubuntu on to my fz180e laptop, everything seemed to be fine un till i went to go install wine and it gave me this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

it's not just wine, any time i try to download anything that way it gives me the same message.

Any help at all would be great, Thanks

---

### Post by CupofDice on 2008-01-21
You need to enable your repositories. Type "  gksudo gedit /etc/apt/sources.list  " in the terminal and uncomment (removing the # signs) all of the lines that start with a deb and http link after the # sign. Do not uncomment the instructions to you.

---

### Post by wolfen69 on 2008-01-21
a safer method would be system>admin>software sources and make sure everything is checked off.

---

### Post by rosegarden78 on 2008-01-21
I use aptitude and Synaptic package manager, yes you need all repositories enabled, I seldom use apt-get.  You can get Synaptic installed by typing "sudo aptitude install synaptic" or use Add/Remove Programs.

---

### Post by Majorix on 2008-01-21
> **wolfen69 said:**
> a safer method would be system>admin>software sources and make sure everything is checked off.
+1
You can also do it in Synaptic, through Settings > Repositories. I believe it launches the same program as Software Sources does.

---

### Post by Rhift on 2008-01-21
Hey thanks for the help i got it working.

---

