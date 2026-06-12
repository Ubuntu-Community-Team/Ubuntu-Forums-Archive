---
title: "rebooted kubuntu now all my 26gig's are gone! help please!"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-11-03
I dont quite know what happened. I dual boot with xp. 60gig harddrive. split 50/50 so on the kubuntu its 26gigs. I installed edgy the friday after its release. today all of a sudden it keeps crashing opera and amsn so 1st i start a new session. few mins go by same crash. so I reboot system. get to login screen enter password acts like it will login then sends me back to login screen does this about 4times which is each time i entered my password...so i boot into xp and i have that windows thing that lets me see linux drives. I hover over my linux partition and it says 0bytes free 26gig's used....my partition is 500mb swap, with home and root on one partition. i had 2gig's on my desktop so i moved those to windows. i go onto my trash and delete whats there. i right click on root, i have only used mb's, i right click on home and its 2.59 gig's used.

But when i try to login it wont let me. i run sudo apt-get clean after every update to remove debs and stuff, i empty my trash daily. I dont know what could have ate all my space.

i close windows and go to kubuntu and it says there is an error in root and restarts my system. i login but i have the blue wall paper of the login screen and a konsole on the top left. I called for firefox and that is how I am typing this message.

Can someone anyone tell me how i can see what part of my kubuntu is eating all my space? and how to fix it?

please, i dont understand why this is always happening to me and this problem is weird...

help anyone?

can someone tell me how to fix this? I dont have a gnome desktop just kubuntu.

---

### Post by pandu.rs on 2006-11-03
u can use this command, to find out what occupies most of ur space (they will be listed first)

sudo du / | sort -nr

---

### Post by maddbaron on 2006-11-03
I found what it was, somehow my firefox browserstate folder ate about 15gigs of space. i dont know how. but in xp i deleted them and thanks to somemore help i am using my ubuntu...but this was strange....

---

