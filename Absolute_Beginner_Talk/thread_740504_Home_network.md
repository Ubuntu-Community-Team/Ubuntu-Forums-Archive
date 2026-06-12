---
title: "Home network"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2008-03-30
Ok, so I'm not sure exactly what a network is, but is it something where I could have one of my computers turned on and I could access files in it?  I really would like to do something like this because I have an EeePC (read: only 4GB drive) so i would like to be able to get music from another computer mayhaps.  Is that possible?  How would I do this?
Both computers use Ubuntu (took me a while to get Ubuntu on the Eee since it has no CD drive...)

---

### Post by freebeer on 2008-03-30
Yes, it's quite possible to do what you want.  You need a means to allow the two computers to talk to each other.  Usually accomplished through a router but there are other means.

---

### Post by Helgiks on 2008-03-30
Yes you can with NFS, read about it.

Edit your /etc/exports file, listing what you want to share, and than mount it on the eeepc.

Add something like ($ sudo nano /etc/exports)

/folder/to/share eee.pc.ip.address(rw,no_root_squash,async)

To your exports file.
Than type $ exportfs -a (so it will read your changes)

And finally mount it with something like this:

$ sudo mount ipadress:/folder/to/share /place/to/mount

Assuming of course the computers are connected in some way.

There are allot of tutorials on NFS on the internet, google it and read.
Hope that helps.

---

