---
title: "Dual Cpu Support On A G4 Powermac"
date: 2008-02-09
forum: Apple PPC Users
---

### Post by cobberdig on 2008-02-09
would someone step me through the process get ubuntu gutsy to recognise my dual processor my machine is a G4 power mac gigabit ethonet with dual 500 mhz cpu. thanx in advance.

---

### Post by stream303 on 2008-02-09
Gutsy should use smp by default.  Let's check the kernel, what is the output of 

uname -a

For a quick check, I like to download HTOP as an alternative to the regular top to keep an eye on my processors.  It works great on dual-processors.

---

### Post by frog_pilot on 2008-02-09
If not, install the following meta packages manually (e.g. via synaptics)

```
linux-image-powerpc-smp
linux-headers-powerpc-smp
linux-restricted-modules-powerpc-smp
linux-powerpc-smp
```

reboot. Now the system monitor will show you your 2 processors

---

### Post by cobberdig on 2008-02-10
thanks for your reply frog pilot. i discovered synaptics not long after i posted the question, and followed the directions from another thread you posted on about dual cpu's and sound, it worked i installed the smp kernals in synaptics got rid of the old ones now i have 2 working processors!!! thanx i have a similar set of things to iron out as the person in that  other thread. now i need to sort out the sound. I had the busy box problem on boot but thats been sorted now since i got a friend to show me around terminal and nautilus etc.  i need to also get some sort of flash plugin so i can watch youtube etc. I installed mozilla firefox mplayer from synaptics thought that would do the trick but not yet.

---

