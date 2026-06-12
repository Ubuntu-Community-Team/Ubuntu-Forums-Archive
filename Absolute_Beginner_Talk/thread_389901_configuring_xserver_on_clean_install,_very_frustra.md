---
title: "configuring xserver on clean install, very frustrating experience"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-21
what is up with scrambled screens on fresh install of ubuntu?  when i first tried out linux/ubuntu a few months back, one of the most frustrating experiences for me was on a fresh install ending up with a scrambled screen.

i almost gave up on linux trying to solve this problem.  yes, i was a complete noob who had no idea how to edit text files from the command line, but what is all this talk about my grandma being able to use linux if i can't even get a gui out of a fresh install on a widely used nvidia graphics card.

i forgot how frustrating this was until i decided to do a fresh install last night, with a much greater understanding of how linux operates, ran in to this same problem, and ended up jacking with it for hours.

i solve the problem by booting to recovery mode and editing xorg.conf to use "vesa" instead of "nv" driver, so i could get to gui and . . .

> sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

then editing xorg.conf to "nvidia".  all is well until i update kernel from -386 to -generic and it breaks again.  so i remembered to . . .

> sudo apt-get install linux-generic

is there a way to do a fresh install without having to go through all this?

---

### Post by Bachstelze on 2007-03-21
Just remember to always have the restricted modules matching your current running kernel. Is it *that* hard ? Another option would be to get the installer from nvidia's website. When you install a new kernel and it breaks your X, jusr run the installer again and voilà.

---

### Post by larrybrazos on 2007-03-21
> **HymnToLife said:**
> Just remember to always have the restricted modules matching your current running kernel. Is it *that* hard ? Another option would be to get the installer from nvidia's website. When you install a new kernel and it breaks your X, jusr run the installer again and voilà.

yes it is *that* hard.  imagine for a second that you are talking to someone who knows nothing of linux and kernels.  "remember to always have the restricted modules matching your current running kernel".  you might as well be speaking another language.  i am not saying i am that user, but that simple statement takes a considerable amount of research for a noob to follow up on.

and what about the having to configure xorg.conf from the command line just to get a gui on a fresh install?

---

### Post by Bachstelze on 2007-03-21
Having to configure X from the CLI on a fresh install is far less common... Did you install from a Desktop or an Alternate CD ? Also, for questions like the "restricted modules" part, instead of doing hours of searching, just ask and someone will explain it in two minutes :)

---

### Post by larrybrazos on 2007-03-21
let me get back on track . . .

is there an easier way to configure xerver on clean install then having to back out to terminal and manually configure xorg.conf?

---

### Post by larrybrazos on 2007-03-21
well, we must have been posting at the same time, give me a bit, i want to figure out why this has been so difficult for me and write out the steps.

---

### Post by larrybrazos on 2007-03-21
while i am working . . .

how bout you give me that explaination of restricted modules?

---

### Post by Bachstelze on 2007-03-21
The nvidia driver is composed of three parts : a Xorg module, a kernel module and some graphic libraries. They're free as in "no cost" but not Free as in "freedom" so they cannot be shipped with Ubuntu. Instead, Ubuntu has a "restricted-modules" package, which provides an easy way to install such non-free modules. 

But of course, a module built for one version of the kernel will not work on another so you always need to have the restricted-module package that matches your current kernel. Once you've installed linux-generic, though, you shouldn't need to worry about it since it will be updated automagically with the kernel.

---

### Post by larrybrazos on 2007-03-21
sorry for being snappy, just in a bad mood, and the  "is it *that* hard" comment got me all riled up.  you must have the patience of a saint, but thanks for the explanation.

---

