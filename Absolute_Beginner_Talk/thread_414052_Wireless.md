---
title: "Wireless"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-04-19
How much does Feisty's wireless support exceed Edgy's? I'm having trouble figuring out if I could use my Linksys G card with it (and I would like to know before the upgrade!)

---

### Post by rich.bradshaw on 2007-04-20
My wireless cards both work fine with Feisty.

If they don't work then ndiswrapper has a nice gui you can use by installing

sudo apt-get install ndiswrapper-utils ndisgtk

which gives you a option on the System/Admin menu to install Windows Wireless Drivers. This is what I did and it all works fine... That's in Feisty - not sure if that package is in Edgy, you'll have to try it!

The main difference in Feisty is that the Network Manager has been rewritten so it is a lot easier to use.

---

