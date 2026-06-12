---
title: "Unable to find a source package for openmovieeditor"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by one_iota on 2008-03-16
I'm a complete beginner, trying to install Open Movie Editor. I didn't want to have anything to do with 'compiling' but I need something to replace Windows Movie Maker, so I've had to jump in at the deep end and attempt it. :(

Following instructions from the Open Movie Editor website, I opened a terminal and typed: sudo apt-get install openmovieeditor. Things happened and it appeared to go well. I then typed: sudo apt-get build-dep openmovieeditor but I got an error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for openmovieeditor
```

I then downloaded the latest version of Movie Editor and extracted it on my Desktop, as prompted by the website.

I have also typed the following in a terminal, as I saw them mentioned when Googling:

sudo aptitude update
sudo aptitude install build-essential

They seemed to install ok but I am continuing to get the above "unable to find source package" error when I type: sudo apt-get build-dep openmovieeditor. :confused:

---

### Post by bsharp on 2008-03-16
if you did sudo apt-get install openmovieeditor, then it should already be installed on your system.

If that didn't work and you still want to go ahead and install the latest that you downloaded, then you need to extract that .tar and cd into the directory and then compile it from scratch.

---

