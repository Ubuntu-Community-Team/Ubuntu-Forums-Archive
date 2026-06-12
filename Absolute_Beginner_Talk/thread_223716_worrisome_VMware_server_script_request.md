---
title: "worrisome VMware server script request"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by wog on 2006-07-26
The Long Story:
Okay, so wine isn't good at being a replacement for Windows for running games. Since VMware is now free, I thought I'd try installing it, putting win98 into it, and installing/playing games through that.

I got the software and it installs through what I have finally come to understand is a perl script. I ran it with this:
```
sudo ./vmware-install.pl
```

Okay, so it runs. It asks questions, and in typical windows fashion (I know this isn't windows, but these are the habits I have to work with right now) I press ENTER and type in 'yes' for everything until I get to the point where it asks for the location of the directory of C header files that match my running kernal. Its default is /usr/src/linux/include. However, when I press ENTER it tells me /usr/src/linux/include is not an existing directory.

Okay, I have no idea what it wants to find in that location it says doesn't exist, and so I have no idea what to install. 

Can anyone lend me a clue?

---

### Post by simonn on 2006-07-26
Install linux-headers for your kernel version. Use synaptic or apt-get etc.

---

### Post by Anduu on 2006-07-26
Just to let you know you probably won't have much luck running games under vmware either...

---

### Post by wog on 2006-07-26
> **Anduu said:**
> Just to let you know you probably won't have much luck running games under vmware either...

No? Why not?

I figured that with a full version of the software games expect to find, things would work much better. Slower, but much better. :)

---

### Post by wog on 2006-07-26
> **simonn said:**
> Install linux-headers for your kernel version. Use synaptic or apt-get etc.

How do I figure out which headers I need? I mean, I don't even know that much.

---

