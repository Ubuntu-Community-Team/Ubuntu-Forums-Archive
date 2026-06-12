---
title: "Can a Ubuntu user install an RPM"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-04-18
You can obviously see that I am new to this platform. BUT I have a question . . .

Can a Ubuntu user install a downloaded file ending with the extension of RPM?

:confused:

---

### Post by RedSquirrel on 2007-04-18
You have to use alien. See [this]("http://www.psychocats.net/ubuntu/installingsoftware"). There's section on "Manual installation of a .rpm".

---

### Post by BaffledMollusc on 2007-04-18
> **doctorj said:**
> You can obviously see that I am new to this platform. BUT I have a question . . .

Can a Ubuntu user install a downloaded file ending with the extension of RPM?

:confused:
Not directly. There are two main ways of packaging software in the Linux world. There is the Debian system (so package files end in .deb) and the Red Hat system (packages end in .rpm).

Ubuntu uses the Debian system. It is, however, possible to convert an .rpm to a .deb file using an application called alien. To do this download the .rpm file, (say it's test.rpm), and then convert it using the command

sudo alien test.rpm

You'll then have a .deb file which you can double click on to install. I'm not sure if alien is installed by default; you may need to use synaptic to install it first.

---

### Post by jjbean on 2007-04-18
You can use a program called alien to convert rpm to deb. You can use the synaptic package manager to install it. SYSTEM > Administration > Synaptic Package Manager. Search for alien. I do not know how well it works though. You might want to do a forum search for it.

Look up. He was faster, and a more complete answer. Guess I type to slow.:lolflag:

---

### Post by doctorj on 2007-04-18
Thanks for the reply. Have got the instructions.

:)

---

