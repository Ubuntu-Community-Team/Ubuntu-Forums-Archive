---
title: "Problems installing Open Office"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-08-13
Hi,
First off, I had Open Office installed here in kubuntu 7.04, but I had major problems, and a rep at OpenOffice.org recommended an uninstall and a clean reinstall from the ORG site.

So, I've downloaded open Office and  I've searched AND followed 2 'How To' guides in this forum,

Here's what's happening:

```
brightbelt@brightbelt-desktop:~$ cd Desktop/OOF680_m18_native_packed-1_en-US.9161
brightbelt@brightbelt-desktop:~/Desktop/OOF680_m18_native_packed-1_en-US.9161$ sudo alien -d *.rpm
Password:
sudo: alien: command not found
brightbelt@brightbelt-desktop:~/Desktop/OOF680_m18_native_packed-1_en-US.9161$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
brightbelt@brightbelt-desktop:~/Desktop/OOF680_m18_native_packed-1_en-US.9161$
```

As you can see, when I got sudo:alien: command not found, I went ahead and tried the install anyways, but to no avail.

I appreciate any help on this. Getting Open Office to work correctly is going to be really helpful if I can get it going.

Many Thanks, Frank B.

---

### Post by ThrobbingBrain66 on 2007-08-13
It would be easier to install OpenOffice from the repos.  It won't be the latest version, but you won't have to go through the hassle of converting everything with alien.
```
sudo apt-get install openoffice.org
```
If you insist on using alien, it must be installed before you can use it
```
sudo apt-get install alien
```

---

### Post by Brightbelt on 2007-08-13
Thanks ThrobbingBrian,
I did get it installed, and the interface is a lot better. But I still can't seem to save a file to a folder in my Documents folder.

It tells me the path "home/brightbelt/Documents/Open Office Drawing/filename" does not exist. And then it tells me it is a "general error" and an "input/output error".

Any idea on those?

Many Thanks, Frank B.

---

### Post by ThrobbingBrain66 on 2007-08-13
If that's the exact error there's two possibilities: there should be a forward-slash (/) before home OR Open Office doesn't like the spaces in the folder name.

---

