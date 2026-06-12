---
title: "Eclipse and Java on powerpc"
date: 2011-03-07
forum: Apple Hardware Users
---

### Post by teachop on 2011-03-07
Anybody know how to get the Eclipse IDE to work on powerpc?  I have Ubuntu 10.10 installed on an eMac G4 1.25, and installed eclipse CDT from the repos, which pulled in a ton of stuff with it.

Starting eclipse results in nothing but the initial splash screen.  A process called Java takes the top spot in the task list and sits there burning up CPU to max it out at 100%.  It appears stuck there for good.

It is a pretty virgin system except for the automatic updates.  It was just installed yesterday.

---

### Post by linuxftw3 on 2011-03-09
> **teachop said:**
> Anybody know how to get the Eclipse IDE to work on powerpc?  I have Ubuntu 10.10 installed on an eMac G4 1.25, and installed eclipse CDT from the repos, which pulled in a ton of stuff with it.

Starting eclipse results in nothing but the initial splash screen.  A process called Java takes the top spot in the task list and sits there burning up CPU to max it out at 100%.  It appears stuck there for good.

It is a pretty virgin system except for the automatic updates.  It was just installed yesterday.


try reading this:    [http://tiny.cc/eclipseidepowerpc](http://tiny.cc/eclipseidepowerpc)      hope that helps:D


btw, i have an 1.25 GHZ eMac too  :D
also,  if you need some java support that albeit, is  a little slow,  try IcedTea.

---

### Post by teachop on 2011-03-09
I think that document is to help with targeting PPC for cross-development, rather than as the host OS CPU.  Interesting but a different endeavor.

For the time being, I have installed Code:Blocks IDE and am learning how to use it.  I have been able to bring in one existing project and build it from the IDE (it is an AVR cross-dev target) and so far so good.

Perhaps since Code::Blocks is "lighter" than Eclipse, this would be on this computer a better solution anyway.  Eclipse is so powerful though, would like to get it running and see...

---

### Post by teachop on 2011-03-14
Still no eclipse, bagging it for now.

After several days developing with Code::Blocks... it is a worthy IDE for c language development.  I can recommend it to anybody else not able to get eclipse working on powerpc.

So far I have used it on embedded development projects targeting AVR (Arduino) and ARM (Netduino) boards.

Not eclipse, but very nice in its way.

---

### Post by pauljwells on 2011-03-15
I found that the first run of Eclipse has to be as root (sudo eclipse from a terminal). After that it should open from the menus. If you want to install any add-ons (I use PyDev for example) then you have to run as root again.

---

### Post by teachop on 2011-03-16
I tried sudo eclipse from the command line, and it sticks at the splash screen the same.  Not even the progress bar...

---

