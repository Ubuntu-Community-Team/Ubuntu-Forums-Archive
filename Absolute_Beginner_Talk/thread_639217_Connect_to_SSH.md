---
title: "Connect to SSH"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by crimsonsky on 2007-12-12
what would be the best way to connect to a unix work station running SSH server. in windows i've used putty and winscp. is there any program for ubuntu that will let me do both. also which should i get emacs. [QUOTE][ * emacs21-nox
 * emacs22-gtk
 * emacs22
 * emacs-snapshot
 * e3
 * emacs-snapshot-nox
 * emacs21
 * emacs22-nox
 * jove
 * emacs-snapshot-gtk
/QUOTE]
 i'll use emacs just for doing some java programming.

---

### Post by t0p on 2007-12-12
In Ubuntu is the OpenSSH ssh client.  Of course you should check
```
man ssh
```
for full details.  But briefly, it's a command-line utility.  So you go into terminal and, for instance, type
```
ssh server.domain.org
```
and it connects you.  I use ssh to access my shell account on a remote FreeBSD server.

---

### Post by RealPSL on 2007-12-12
If you are addicted to putty it is also available

Use sudo **aptitude install putty** to get it. Or use **synaptic**.

---

