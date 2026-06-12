---
title: "How to properly partition disk manually."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-05-05
ubuntu is picking the wrong disk to partition during setup so I have to partition using the manual method.  Can someone walk me through this or point me to a how to.  set up is telling me I need to partition for a swap file and the root file system.  I need 2 partitions for ubuntu and how do I designate one  for the file system and one as  a swap partition?

Thanks for your help.

---

### Post by cptjaben on 2007-05-05
Well, you can boot up an Ubuntu Live CD and jsut Gnome partition editor or just install it if you have an installed version. What you'll want to do is make you primary partition ( the one that will have ubuntu installed) either ext2 or ext3, as far as I know ext3 is the way to go. You'll then need to make a swap partition, these are usually 2 to 3 gb's. After that, follow the installation and hopefully everything will work smoothly. Goodluck.

---

### Post by crimesaucer on 2007-05-05
When I installed back in October, I liked this guide, here is the updated version for Feisty:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

You can search all of the pages in that site to see different ways to install. Click on the home page here to see the list: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

