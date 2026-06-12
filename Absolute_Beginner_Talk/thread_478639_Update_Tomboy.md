---
title: "Update Tomboy?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by megadeus on 2007-06-19
I'm not sure how to update my Tomboy. I'm using 6.06 Dapper and added Tomboy when I heard of its inclusion in Edgy.

My version is 0.3.5, and the current version is something like 0.6.*, so I'm wondering why it hasn't been updating along with the rest of my programs.

I'm a little heasitant to download the tarballs and try to upgrade that way, and the .deb files I found listed all the versions higher than 0.3.5 as "Edgy" and "Feisty."

Will using a .deb or unpacking a new tarball bork my old installation, or is there a simple way to get the latest Tomboy?

Thanks in advance!

---

### Post by angryfirelord on 2007-06-19
If you installed tomboy from an edgy deb, then it won't update because you're using dapper repos. You could potentially get another deb and use it, but watch out for the dependencies. dpkg won't install or remove anything unless all dependencies are satisfied.

---

### Post by megadeus on 2007-06-19
Yes, dpkg says the dependancies are not satisfiable: mono-runtime.

Anything I can do about this besides upgrade distros?

---

