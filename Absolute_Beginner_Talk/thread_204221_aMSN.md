---
title: "aMSN"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-26
i have recently updated the aMSN skins and plugins, and now aMSN will not start... when i try and start it, i get the waiting/loading mouse icon, then nothing....

i wouldnt even know where to start looking for error codes or anything, please help....

i have tried to apt-get remove and re-install it, but doesnt work either

---

### Post by th3james on 2006-06-26
Try running it from a terminal (just type amsn), this should give you errors

---

### Post by shoot2kill on 2006-06-26
ok... i would like you to know im using KDE desktop also, but still use terminal instead of konsole.. but error is:

```
gav@gav-linux:~$ amsn
Segmentation fault
gav@gav-linux:~$

```

---

### Post by th3james on 2006-06-26
Have you tried deleting the skins from ~/.amsn/skins

Also, have you tried a complete remove in synaptic?

---

### Post by catlett on 2006-06-26
try ```
kdesu amsn
``` see if it runs then. This will launch it as root. (I hope kdesu is corect. In gnome it is gksudo amsn.) I say this because a a segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (e.g., attempts to write to a read-only location, or to overwrite part of the operating system). So I'm curious if maybe you installed the new upgrades as root and now as user you can't access them?? Just a hunch. I don't see why you are getting a segmentation fault by running an application that has been run before. Obviously the updates changed something but what?

---

### Post by richbarna on 2006-06-26
More info :- [http://en.wikipedia.org/wiki/Segmentation_fault]("http://en.wikipedia.org/wiki/Segmentation_fault")

And yes it is kdesu

---

### Post by shoot2kill on 2006-06-26
when i try kdesu amsn

i get 
```
gav@gav-linux:~$ kdesu amsn
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144   
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
gav@gav-linux:~$

```

i did install the skins into the root area because in my personal area, it didn't work, but i have removed these now and still doesnt work...

:(

just tried a complete removal in synaptec (sorry for typos) and re-installing  it, still no luck... :(

---

### Post by catlett on 2006-06-26
[http://www.ubuntuforums.org/showthread.php?t=176851](http://www.ubuntuforums.org/showthread.php?t=176851) I wish that guy was more desrciptive. There are a few more posted with your error and they all happen after updates and deleting stuff to try and get it working.
He mentions>  fixed by deleted the /root/config directory but I don't know if he means that applications root/config or what. When I get a chance I'm going to huint around my setup and try to see what directory he meant but I thought I'd throw it back at you for now.

---

### Post by shoot2kill on 2006-06-26
ok. thx.. 

i will leave it for now and settle for gaim untill it sorted, 

i dont want to start deleting stuff to have to re-install ubuntu.. lol

---

### Post by shoot2kill on 2006-06-27
*bump*

any hep...?

---

