---
title: "Linux from Scratch- where to begin??"
date: 2014-05-27
forum: Any Other OS
---

### Post by amier.naji7 on 2014-05-27
[COLOR=#000000][FONT=Arial]So I got the LiveCD environment up and running fine- but I'm having trouble getting started with it- do I still partition my hard drive, and if so, how do I access it?? I tried to cfdisk but it wasn't able to access any hard drives O_o Or am I supposed to build everything on the CD itself??[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I can follow the terminal commands, but I just need to figure out how to access the actual partition to do work on- or am I doing all the work on the CD itself...this is my real question-I already have a partition I set up in Linux Mint (what I was working on to do LFS before I realized that the LiveCD was a thing)[/FONT][/COLOR]

---

### Post by Elfy on 2014-05-27
*Thread moved to **Other OS/Distro Support**.*

---

### Post by Tadaen_Sylvermane on 2014-05-27
> **amier.naji7 said:**
> [COLOR=#000000][FONT=Arial]So I got the LiveCD environment up and running fine- but I'm having trouble getting started with it- do I still partition my hard drive, and if so, how do I access it?? I tried to cfdisk but it wasn't able to access any hard drives O_o Or am I supposed to build everything on the CD itself??[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I can follow the terminal commands, but I just need to figure out how to access the actual partition to do work on- or am I doing all the work on the CD itself...this is my real question-I already have a partition I set up in Linux Mint (what I was working on to do LFS before I realized that the LiveCD was a thing)[/FONT][/COLOR]


I haven't looked into LFS for almost 10 years now. As I recall it you need to mount the partitions somewhere then chroot into them. The book tells you what to do you just gotta read up on how to do it is what it sounds like. As far as cfdisk goes the command cfdisk won't do anything. You need to find out what letter your drive is at then cfdisk /dev/sdX. Then it will load and let you do your thing. You don't need a partition just for LFS though. You can build it right inside of Mint and then transfer it somewhere, or to it's own partition. At least from what I recall.

LFS is a big project though. If you are having trouble figuring out a cli partition tool then ... no offense and I mean no disrespect... you aren't ready for it. There will be errors and problems as you build, is just the way it is. The book doesn't tell you everything step by step, rather it doesn't always tell you the command to use. It assumes a certain level of ability.

---

### Post by hwindle83 on 2014-06-10
When I tried Linux From Scratch, I had spare space on my hard drive to use as the LFS partition. You can always read the help for commands using "man cfdisk", you have to build the tools on that partition because the CD is read only. I read the books that came with it thoroughly too. I'd try installing Gentoo before LFS, as it's a little easier, and uses similar processes except you don't have to compile the GCC compiler. That's where I got stuck.

---

