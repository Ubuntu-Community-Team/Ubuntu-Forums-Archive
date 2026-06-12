---
title: "ob archive"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-08-10
trying to install XnView and it tells me to bring in ob of archives. What is this and where?

---

### Post by sailor2001 on 2006-08-10
bump

---

### Post by sailor2001 on 2006-08-10
sailor@sailor-desktop:~$ sudo aptitude install XnView
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "XnView"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
sailor@sailor-desktop:~$

---

### Post by sailor2001 on 2006-08-11
bump

---

### Post by msak007 on 2006-08-11
First of all, I think you're reading that wrong - it's 0B (the number 0), not OB (the letter O) - it simply means it's not going to download or install anything. When you posted the complete output later on, you can see why:

```
Couldn't find any package whose name or description matched "XnView"
```

The package doesn't exist, so a.) it's not going to download it, b.) it's not going to install it - thus using "0B" of space. I searched for it and the app doesn't seem to exist in the repos - you may have to compile it form source or find an alternative image viewing program as the only [package downloads]("http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html") they offer on their site are RPMs.

---

### Post by sailor2001 on 2006-08-12
> **msak007 said:**
> First of all, I think you're reading that wrong - it's 0B (the number 0), not OB (the letter O) - it simply means it's not going to download or install anything. When you posted the complete output later on, you can see why:

```
Couldn't find any package whose name or description matched "XnView"
```

The package doesn't exist, so a.) it's not going to download it, b.) it's not going to install it - thus using "0B" of space. I searched for it and the app doesn't seem to exist in the repos - you may have to compile it form source or find an alternative image viewing program as the only [package downloads]("http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html") they offer on their site are RPMs.

no. I have it downloaded and sitting on my desktop.(linux version) and tried to use Arnie's instruction for installing in terminal, but that just sits there and doesn't do anything.

---

### Post by orb9220 on 2006-08-12
The linux version is no where near as good as the windows which I have used under wine.

---

### Post by msak007 on 2006-08-12
If you downloaded it and you have it on your Desktop, then you're going about the wrong way of installing it - when you install a local package, you would use "dpkg". The way you're trying to install it using aptitude is only used when you're installing packages from the repositories. Hence you when tried to install the application using aptitude
```
sailor@sailor-desktop:~$ sudo aptitude install XnView
```
it didn't install because it's not in the repositories as I said before.  What Arnie instructions are you talking about?

---

