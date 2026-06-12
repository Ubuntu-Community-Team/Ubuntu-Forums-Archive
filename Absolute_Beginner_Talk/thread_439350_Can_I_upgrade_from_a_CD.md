---
title: "Can I upgrade from a CD?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jefuchs on 2007-05-10
I tried the recommended way of upgrading, but I keep getting a message saying the files have been permanently moved.

So how about taking a new CD and starting the install process?  Will it give me the option to upgrade, or will it just wipe out my old install?

Alternately, if I make a backup copy of my home folder (called "Jeff") onto a CD, then do a fresh install of Feisty, then replace the new Feisty "Jeff" folder with my old Dapper one from the CD, would that screw things up, or would it be like an upgrade?

TIA,

Jeff

---

### Post by Ramses de Norre on 2007-05-10
> **jefuchs said:**
> I tried the recommended way of upgrading, but I keep getting a message saying the files have been permanently moved.

So how about taking a new CD and starting the install process?  Will it give me the option to upgrade, or will it just wipe out my old install?

Alternately, if I make a backup copy of my home folder (called "Jeff") onto a CD, then do a fresh install of Feisty, then replace the new Feisty "Jeff" folder with my old Dapper one from the CD, would that screw things up, or would it be like an upgrade?

TIA,

Jeff

Keeping the home dir would work pretty well, you can also try to add the new cd with **apt-cdrom add** and update that way. I never tried it myself but I think it's possible.

---

### Post by zvacet on 2007-05-10
You can not upgrade directly from Dapper to Feisty.It´s look like Dapper>Edgy>Feisty.You can make separate home partition before you do the upgrade,and that way all your data wil be safe.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

