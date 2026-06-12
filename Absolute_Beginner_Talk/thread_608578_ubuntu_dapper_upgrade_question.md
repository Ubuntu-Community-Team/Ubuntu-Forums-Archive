---
title: "ubuntu dapper upgrade question"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-11-10
hello 
(again)

Im seting up an old computer for a friend in need. 
NOw for dsome reason the newest ubuntu version text installer didnt work, i t was complaining about the cd rom being too obscure . But fter trying all the newest ubuntus finally 6.06  worked. (text)

but since i only have about 90 something megs of ram i removed ubuntu desktop and put xubuntu desktop.....(using psychocats guide)

 and i installed ndiswrapper from source for my cheap zonet pci card.

so far those are the only changes ive made, well i removed gaim too...

  how should I upgrade to edgy? 
 using the xubuntu method or the ubuntu method?
xubuntu: [http://ubuntuforums.org/showthread.php?t=285951](http://ubuntuforums.org/showthread.php?t=285951)
ubuntu:    gksu update-manager -c

 By the way, i ran the update manager and is showing me 6.10 as an upgrade option....

  Is not a big deal if it gets all  messed up but itll be just time consuming 

so I decided to ask...

any thoughts????

---

### Post by overdrank on 2007-11-10
> **gigaferz said:**
> hello 
(again)

Im seting up an old computer for a friend in need. 
NOw for dsome reason the newest ubuntu version text installer didnt work, i t was complaining about the cd rom being too obscure . But fter trying all the newest ubuntus finally 6.06  worked. (text)

but since i only have about 90 something megs of ram i removed ubuntu desktop and put xubuntu desktop.....(using psychocats guide)

 and i installed ndiswrapper from source for my cheap zonet pci card.

so far those are the only changes ive made, well i removed gaim too...

  how should I upgrade to edgy? 
 using the xubuntu method or the ubuntu method?
xubuntu: [http://ubuntuforums.org/showthread.php?t=285951](http://ubuntuforums.org/showthread.php?t=285951)
ubuntu:    gksu update-manager -c

 By the way, i ran the update manager and is showing me 6.10 as an upgrade option....

  Is not a big deal if it gets all  messed up but itll be just time consuming 

so I decided to ask...

any thoughts????

HI and yes use the update manager, but with 90mb of memory you may take a look a DSL or puppy. [http://distrowatch.com/](http://distrowatch.com/)    Good luck!

---

### Post by gigaferz on 2007-11-10
i do know about them and got them cd burned already, but i m just not too familiar with  those versions...

right now this installation runs good, and i hope ill find a tweak  to use the swap in a better way (or something)

I m barely learning icewm, and tried before dsl, but i just cant gitterdone!!!, now can you imagine a poor soul that  its been captive under a windows world??

Also I remember setting up file sharing on an edgy it was a pain!!!
now in feisty it was (almost) ready to go,,,,so im aiming at that too.... 
for my own good i wont install gutsy...ill wait till the next one....LTS.....

Thanks!!!

well it didnt work, it couldnt guess the metapackage.....

i also tried  apt-get dist upgrade, but it only shows me upgrade packages not a full upgrade....or im supposed to get them pckages first then the version upgrade will show up???

---

### Post by louieb on 2007-11-10
> **overdrank said:**
> 
HI and yes use the update manager, but with 90mb of memory you may take a look a DSL or puppy. [http://distrowatch.com/](http://distrowatch.com/)    Good luck!

I've been playing with xUbuntu 7.10, DSL 4.0, Puppy 3.01 and XP on a P2 400mhz, 384 MB ram.  xUbuntu comes in 1st when it comes to functionality and only in front of XP  when it come to speed.  

DSL and Puppy are about the same speed wise. DSL can be turned into a sorta Debian  with apt and access to the Debian repositories.   The latest version of Puppy is Slackware compatible.   

With Firefox running:  xUbuntu uses 134MB ram.  DSL uses 25MB,  Puppy  around 100 MB and XP checks in at 175 MB. 

I would say Puppy would work but their wiki and forum have problems and getting additional software is a pain right now.

---

