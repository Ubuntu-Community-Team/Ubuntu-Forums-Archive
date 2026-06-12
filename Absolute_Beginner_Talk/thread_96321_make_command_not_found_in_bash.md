---
title: "make command not found in bash"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by ellwoodloc on 2005-11-28
been awhile since i've dabbled in linux, but i found ubuntu, and installed it jsut fine. i was trying to build some packages from the terminal but when the INSTALL readme says 

"all you gotta do is 
make
su
make install"

trying the first step and just typing make in the package directory, bash tells me that make isnt even a command. is there something i need to setup in a conf somewhere? 

thanks in advance,
brittj(learning to ride the bike again)

---

### Post by Kyral on 2005-11-28
You need the tools

```
sudo apt-get install build-essiential
```

NOTE: If you get an error, then I misspelled "essiential"

---

### Post by ellwoodloc on 2005-11-28
thanks bro. upacking as we speak. one other quick question. i have ubuntu dual booting on my office comp with XP. i partioned/installed ubuntu on hdb. for some reason though, on my gnome desktop, hda(my windows installation) is showing up as the default hard drive. is there anyway to change this so that i can just have hdb my default drive?

thanks in advance again.
brittj

---

### Post by Kyral on 2005-11-29
Default HD? Eh? (Example? This is the first I have heard of this term lol)

---

