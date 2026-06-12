---
title: "Some trouble with 8 Powerbook G4's"
date: 2011-07-29
forum: Apple Hardware Users
---

### Post by schooldude on 2011-07-29
Hello All,

I'm somewhat of a  novice and am trying to get some tips.  I work at an urban high school in Austin, Texas, and am trying to get eight 10 year old Powerbook G4's to a point where they are able to perform two functions; run Open Office and use firefox with a wireless connection.  These will be used for projects in our biology lab.  The computers were donated by a local university, and had their hard drives wiped before arriving.  I've attempted to install ubuntu on all 8.  

Of the 8;

3 work fine

2 have "triple vision". The screens are fuzzy and there are 3 of every image.  I imagine that could be a hardware issue, but really have no idea.

1 computer tells me, during the Detect Disk part of the 'install video=ofonly' install,  that no disk drive was detected, and asks me to select it from a list... the list is long

The other two computers have become my personal nemesis and I will deal with them as I please.

Any advice?

KR

---

### Post by linuxopjemac on 2011-07-29
You might want to try MintPPC.

---

### Post by rsavage on 2011-07-29
Maybe the 2 with the triple vision just need an xorg.conf file setting up? That is quite a common fix.

The hard drive one, erm has it got a hard drive?  Is one detected when you boot a live cd?  Annoyingly, some people have had to use an old version of ubuntu to get there hard drives detected.  I don't know if that is it.  I think that problem is something to do with if the drive had been formatted in hfs+.  I would check with a live cd first.

What version on ubuntu are you using?

---

