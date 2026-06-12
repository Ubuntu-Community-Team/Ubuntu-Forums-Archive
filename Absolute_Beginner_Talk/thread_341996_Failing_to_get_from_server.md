---
title: "Failing to get from server"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2007-01-19
Hey dudez.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/cln/libcln4_1.1.11-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/cln/libcln4_1.1.11-1_i386.deb)
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]

thats what I get while I am trying to install a package from synaptic.

I'm running edgy is there another repo I should add while this gets worked on?

---

### Post by riven0 on 2007-01-19
The only fix I've found for this is to take out the **.us** from the repository line. For example, changing this:
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

To this:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe


Someone mentioned that too many doing this will cause the main servers to slow down, but thankfully, no slowdowns yet. :)

---

### Post by Linux&amp;Lizards on 2007-01-19
you typed the same thing twice.

so what do I do again?

---

### Post by riven0 on 2007-01-19
Oops! Sorry, the second one should have been:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

EDIT: Do the same for all the entires in your sources.list

---

### Post by Linux&amp;Lizards on 2007-01-21
kk thanks :guitar:

---

