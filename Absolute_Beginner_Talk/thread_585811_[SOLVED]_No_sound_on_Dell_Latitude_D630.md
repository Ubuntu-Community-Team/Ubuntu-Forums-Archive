---
title: "[SOLVED] No sound on Dell Latitude D630"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jlambeth1 on 2007-10-21
I have tried the following steps to get my sound working that I found in another post.

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

After the last step I get these messages

 Installation of the alsa-source source failed.    
 Ignoring this package. Maybe you need to add something to     
 sources.list, maybe the contrib and non-free archives. 

Bad luck, the kernel headers for the target kernel version could     
not be found and you did not specify other valid kernel headers     
to use.

 However, you can install the header files for your kernel which     
 are provided by the linux-headers-2.6.22-14-generic package. For     
 most modules packages, these files are perfectly sufficient
 without having the original kernel source.   
 To install the package, run the PREPARE command from the main    
 menu, or on the command line:    
 module-assistant prepare

Any advice on what I am doing wrong?

---

### Post by jlambeth1 on 2007-10-21
bump

---

### Post by jlambeth1 on 2007-10-21
I guess I am out of luck for now.  Maybe future updates will fix this issue.

---

### Post by jlambeth1 on 2007-10-23
I started over with a fresh install of Gutsy Gibbon and the above steps worked great for me.  I assume that the various steps that I tried before this one messed up the whole process.

---

