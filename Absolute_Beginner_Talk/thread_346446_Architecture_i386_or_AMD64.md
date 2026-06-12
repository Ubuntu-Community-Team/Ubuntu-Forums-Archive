---
title: "Architecture i386 or AMD64???"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by mc.7winkie on 2007-01-25
I've been having trouble recently getting my wireless working but thankfully some one decided to help me out and I got what appears to be a very accurate and useful reply except one thing.  He told me to download network-manager-gnome.  What it tells me every time I try to install it is that it needs i386 architecture.  I know the difference between the different installs and I know that I do have the i386 install of Ubuntu (I checked my seeding torrents)  Does anyone know what might be wrong?

---

### Post by Shatrat on 2007-01-25
If you do "uname -r" in terminal does it return a kernel that ends in -386 or -generic?
If so I'm not sure what the problem is.
Where are you downloading network-manager-gnome from?
I believe there must be a repository you can install that from somewhere, if it isnt in the default ones.  Downloading single packages is kind of a last resort, since having them autoupdated through apt is so much nicer.

---

