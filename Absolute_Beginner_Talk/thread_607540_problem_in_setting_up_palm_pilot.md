---
title: "problem in setting up palm pilot"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-09
it said i don't have write/read permission on /dev/pilot [see screenshot]

---

### Post by skyjacker on 2007-11-09
Don't know if this will help, but the only way I got my Palm to write was to enter this in the terminal: Code
> sudo modprobe visorr
Good Luck

---

### Post by afeasfaerw23231233 on 2007-11-22
thanks but don't work. Bump

---

### Post by afeasfaerw23231233 on 2007-12-11
BUMP! this is an unansweredd post!!!!

---

### Post by Orbital75 on 2007-12-11
Well, don't feel bad....... I could never get mine to work ( I have a Palm m505 )
Hopefully someone will get it working for you.....
:(

---

### Post by afeasfaerw23231233 on 2007-12-11
well, virtualbox doesn't work too because it doesn't show serial com port up. this question remained unsolved after a couple of week! [UNSOLVED]

---

### Post by afeasfaerw23231233 on 2007-12-11
should i bump it every 48hr? BUMPBUMPBbubjbubpM

---

### Post by Pinger05 on 2007-12-22
Having a similar problem in that I cannot get files from the SD card inserted in my Palm Zire 72s to my Ubuntu desktop.  I managed to get a backup to happen using gnome-pilot but what I really need is to have access to the files on the SD card.  I would rather figure this out than purchase a external SD card reader from best buy.

---

### Post by eldiabolosk on 2007-12-23
I have Ubuntu 7.10. Runing Gnome. Palm Pilot Zire m150 using USB conected straight to the palm. 

Here is what did and what did not work for me.
First I installed Kpilot. Did not connect to my Palm.

Than I got Jpilot (used Synaptic)

Run: 
1)sudo modprobe visor
2) Jpilot
2) click sync on my Pilot
3) click sync on Jpilot.
Worked.

Jpilot seems to be dumb but works

PS: At some point I run an application called multisync and synced my palm. I am not sure since I am not too advanced, but I was able to sync data back to my palm.

So what I did was run multysinc. 
wait till app is done.
click sync on palm
click sync on jpilot
done
As I said not sure it this is necessary but tried this and worked as well.

ed.

---

### Post by aww on 2007-12-27
Thanks eldiabolosk, 

sudo modprobe visor **worked** well for my **kpilot** connection.

Kubuntu 7.10

---

