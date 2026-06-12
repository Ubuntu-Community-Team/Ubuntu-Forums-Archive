---
title: "Error installing applications designed for KDE"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by scweston on 2006-08-20
Hi,

From what I understand programs designed for the KDE environment can also run successfully in Gnome. Is this understanding 100% correct? And if so, why do they need to say it's designed for KDE when it works okay in Gnome, is there some disadvantage to using the applications in Gnome?

Anyways, I've tried to install amaroK and Kverbos (an educational package to help learn spanish verbs). But on both i get the same 'DCOP communications error' and 'Please check dcopserver is running'. when running them. The installation of both of these programs through Add/Remove was smooth.

What is DCOP? I've tried to make sure it installed by looking for the package in the Synaptic Package Manager, but on searching I can't find it listed.

AmaroK also comes up with some other errors on starting, but I think they're unrelated to this error and only want to focus on one error at a time.

Any help will be much appreciated.
Stephen

---

### Post by scweston on 2006-08-20
Okay, well thanks to ppl for reading this..

Although managed to fix the problem myself now. It ended up being a permissions problem with the /.kde folder which was set to root as being the owner. I changed it to my user name instead and fixed the DCOP error as well as the other error i was getting in amaroK (the ones i thought were unrelated).

Although, still interested in how compatible applications designed for KDE are with Gnome. So if someone is able to answer that i would be really interested.

Stephen

---

