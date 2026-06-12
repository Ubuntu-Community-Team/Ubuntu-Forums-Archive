---
title: "gift error"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-24
dave@mypc:~$ gift
GIFT:Starting Server
Random number generator has been seeded with 20396
CAlgorithmCollection.cc:204:throwing AnVENotFound occured: /home/otacon/gift-config.mrml

terminate called after throwing an instance of 'VENotFound'
Aborted (core dumped)

help me.
i just want to use gIFT... its a peer 2 peer client...
i tried using the one on the package site for fiesty and i get that error.i also tried installing in terminal using sudo apt-get install gift then apt-get install gnuift....
and the above error is all that i get:S
please help me.
cheers.

---

### Post by ikonia on 2007-06-24
where did you get this package, when you say one of the fesity sites ??


When you say this is the error you get, its obvious that this is a run time error - not an install error so I assume everything installed ok.

The two key bits are 

> 
CAlgorithmCollection.cc:204:throwing AnVENotFound occured: /home/otacon/gift-config.mrml


and
> 
terminate called after throwing an instance of 'VENotFound'


check that the file gift-config.mrml is readable/execuatable if required by the appropriate users.

If that looks good view the file and look for references to the phrease VEN

---

### Post by keef247 on 2007-06-24
cheers i will check this out in the morning.just checking before bed.as for the package it was from the offical ubuntu packages site and i also tried installing through apt but again the .deb file matched the one installed when using ubuntu repo's so both same installation files/setup each time just one through gui and one in terminal.even when i tried reinstalling the deb install from the repo's it gave the same error.i also installed gnuift which it asked for.sorry if that was comfusing.
in short i tried to methods of obtaining the files through apt-get install in terminal with sudo and the ubuntu package repo's site for fiesty and both where the same files when installing same version etc etc just at first it was obviously a text based install in terminal and the second a gui one with a package manager with a .deb being installed...
hope this help.and as i say i will checkout the above advice in the morning and post back.
cheers

---

