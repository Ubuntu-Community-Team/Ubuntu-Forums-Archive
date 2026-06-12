---
title: "Is Linux really that secure?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Dr. E on 2005-12-14
I am preparing to make the switch to Ubuntu for a number of reasons.  The security of Linux is one of them.  However, when I told my system administrator my plans he grew very concerned because I have a public line to my computer while most of the rest of the computers on the local network do not. (I use remote desktop.) He said that the Windows Firewall is currently taking care of keeping hackers away, but that with Linux I would have to do that sort of thing manually (by checking the log, etc.).

The other disturbing thing is that my workmate next door, who has a PhD in computer science, runs UNIX and had his machine hacked.  The hackers were had commandeered it in order to hack into government installations.

Any comments before I take the plunge?

---

### Post by 23meg on 2005-12-14
As is often said, there's no such thing as absolute security, there are only varying levels of insecurity, and no matter how secure your OS is by its nature, you can ruin all the security with misconfiguration, and/or others can find ways in with their own efforts.

That said, Linux in general and Ubuntu in special *are* very secure as they are. In Ubuntu there are no open ports by default, so as long as you don't install anything that listens on a particular port, you don't need to block anything, which means you don't need a firewall in the Windows sense of the word. You can still use iptables or a frontend to it such as Firestarter to block and certain services/ports, and that's very very easy to set up. Your admin needs an update on the current state of things in Linux.

---

### Post by earobinson on 2005-12-14
[http://www.ubuntuforums.org/showthread.php?t=98912](http://www.ubuntuforums.org/showthread.php?t=98912)

That is all the reading you will need lol

Off Topic: 32megs I just may punk your sig I assume its under the gpl

---

### Post by ltmon on 2005-12-14
The rule I go by is that if anyone _really_ wants to hack your machine and is sufficiently skilled, then they will.  The only way to protect against this is to lock your machine down to the point of being near useless for day to day tasks.

This is irrespective of whether you are running Windows Firewall, Firestarter on Linux or not.

The advantage Linux has is that it is not a target for automated worms/trojans etc., and Ubuntu in particular has less vectors for any of these nasties to use.  As the above poster stated, there are no services running by default.

L.

---

### Post by Dr. E on 2005-12-14
OK, I'm completely blown away.  I make my first posting ever and get several USEFUL responses in under four minutes.  This makes me seriously question whether any of you have a real life.

---

### Post by matthew on 2005-12-14
[quote=Dr. E]OK, I'm completely blown away. I make my first posting ever and get several USEFUL responses in under four minutes. This makes me seriously question whether any of you have a real life.[/quote]People were helpful to us when we started and we want to do the same for others...

...and maybe we don't have a life. :)

---

### Post by aysiu on 2005-12-15
[QUOTE=Dr. E]This makes me seriously question whether any of you have a real life.[/QUOTE] That's gratitude for you. We live to help Dr. E. We've been waiting for you!

---

### Post by 23meg on 2005-12-15
> This makes me seriously question whether any of you have a real life.Linux *is* part of real life, as far as I'm concerned. I don't separate computing from the rest of my activities in "real life".

---

