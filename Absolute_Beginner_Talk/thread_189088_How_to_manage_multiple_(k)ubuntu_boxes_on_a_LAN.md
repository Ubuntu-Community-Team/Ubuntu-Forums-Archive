---
title: "How to manage multiple (k)ubuntu boxes on a LAN?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Master One on 2006-06-04
Let's say, you have bunch of computers in your LAN, all running (k)ubuntu, how would you handle the package management?

I mean, it wouldn't make sense, to have each box act individually, so that when you install a new package on all machines, that package wouldn't have to be downloaded from a mirror multiple times, but only once.

I am new to (k)ubuntu, and I only know how to handle such a situation for Gentoo Linux:

- local-rsync-server for keeping the package managment (portage) up-to-date (so all local machines sync against the local server, instead of one of the public rsync-servers)
- http-replicator for centralized downloading and distributing all requested source-packages (since in the Gentoo world about everything is compiled from source) to local machines (pretty sophisticated, even if two machines request the same file at the same time, it only gets downloaded once)
- distcc for distributed compiling (of course not needed for a binary-based distribution)

---

### Post by Master One on 2006-06-05
Hm, does nobody here have more than one (k)ubuntu maschine is use? I read something about setting up a local deb-repository, but nothing in detail. The other idea would be to use a NFS share as centralized deb-package-folder.

I really thought, there should be quite some extended information available how to handle a bunch of maschines on a LAN, especially if you think about use in companies / schools / universities, where it even makes more sense, to keep the network-load down, and to relieve the official mirrors.

---

### Post by guerillero on 2008-02-11
Hey,
I am working in a company and we are using Kubuntu workstations for development. At least I can tell that setting distcc is a straight forward operation and does not take more than 5 mn per machine. 
About the rest, I can't say a lot except if you need something specific.

---

