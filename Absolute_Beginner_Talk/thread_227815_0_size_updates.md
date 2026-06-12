---
title: "0 size updates?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-02
Sorry in back so soon
                    upon switching unbunto on i was informed of 7 updates so proceeded to install but was presented with this.............

E: The package index files are corrupted. No Filename: field for package app-install-data-commercial.
E: Unable to lock the download directory

Then upon looking closer at these 7 updates i noticed that all of them are 0 "0 size"..

Please could somebody tell me what im doing wrong this time...:-k

---

### Post by apjone on 2006-08-02
open a terminal and type

apt-get update

then see what happens

---

### Post by xpod on 2006-08-02
I think imbecoming a bit of a pest on here.......cheers

Anyway....It sorta looks like the time has come when i need to learn all about these "permissions" dont it

dad@dad-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
dad@dad-desktop:~$

THERES WHAT THE TERMINAL SAID

---

### Post by confused57 on 2006-08-02
You need to use sudo, which gives you temporary root privileges:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by xpod on 2006-08-02
Thanks..I`ll get the hang of this yet.
Im not entirely sure but that seemed to do a lot more than just download the 7 updates that were listed.

Anyway,i know what to do in future so cheers again

---

### Post by pomegranate on 2006-08-02
I seem to have the same problem, but when doing sudo I get:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
tom@ubuntu:~$

---

### Post by pomegranate on 2006-08-03
Any clues why I'm still getting the lock list thing when I'm doing sudo?

---

### Post by carlosqueso on 2006-08-03
Do you have synaptic or the updater open?

---

### Post by pomegranate on 2006-08-03
No.
But - heh - I'm running apt-get update now and it seems to be working, if very slowly...

---

### Post by pomegranate on 2006-08-03
And quite a few of them failed, timing out I think. I'm still pretty clueless when it comes to any of this basic stuff, I'm really not sure what this operation actually does, I've just got the idea that it is the reason that Add Applications fails to install new applications... any ideas/basic clarification anyone can offer? Sorry if this is a bit o/t

---

