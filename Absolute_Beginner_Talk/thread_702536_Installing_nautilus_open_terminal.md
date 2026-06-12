---
title: "Installing nautilus open terminal"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Psicho on 2008-02-20
Hi,

I've been trying to install nautilus-open-terminal so that I can right-click on my desktop to start the terminal, but without much success. I'm executing:
```
sudo aptitude install nautilus-open-terminal
```

and I get the following back:

```
sudo aptitude install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "nautilus-open-terminal"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

```

Was it discontinued or something?

Thanks!

---

### Post by spiderbatdad on 2008-02-20
I have it in synaptic. Possibly you have some sources commented out.
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by y-lee on 2008-02-20
I haven't used it but [it is not discontinued]("http://packages.ubuntu.com/search?searchon=names&keywords=nautilus-open-terminal"). You have to enable the universe repositories, see [Adding the Universe and Multiverse Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096").

hopefully that solves your problem :)

---

### Post by stchman on 2008-02-20
> **Psicho said:**
> Hi,

I've been trying to install nautilus-open-terminal so that I can right-click on my desktop to start the terminal, but without much success. I'm executing:
```
sudo aptitude install nautilus-open-terminal
```

and I get the following back:

```
sudo aptitude install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "nautilus-open-terminal"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

```

Was it discontinued or something?

Thanks!

I use nautilus open terminal all the time.  Very handy package to have.  Allows you to open a terminal in whatever directory Nautilus is browsing.

Yes, just make sure the universe repository is enabled.

[http://packages.ubuntu.com/gutsy/nautilus-open-terminal](http://packages.ubuntu.com/gutsy/nautilus-open-terminal)

---

