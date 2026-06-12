---
title: "How to do a dual boot net install?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by bdmp on 2007-02-16
I have a little comp that has no cd drive and I would like to make it dual boot. One probem is that the windows install "cd" is a built in partion in the laptop. I am afraid that if I install ubuntu then make a seperate partition and then install windows from the "cd" partion that it will overwrite the whole disk. So, I need to start with the windows already installed and figure out how to install ubuntu in a seperate partition over the network.

I am not a beginner but I am in this area. Any suggestions would be appreciated. Thanks.

---

### Post by psithyrismos on 2007-02-17
I have the same problem.

I have a Computer with Win running and I'd like to install Ubuntu via network, since my SATA drives are not working with edgy :P How can I do that?

---

### Post by bdmp on 2007-02-24
bump for solution

---

### Post by old_geekster on 2007-02-24
> **bdmp said:**
> I have a little comp that has no cd drive and I would like to make it dual boot. One probem is that the windows install "cd" is a built in partion in the laptop. I am afraid that if I install ubuntu then make a seperate partition and then install windows from the "cd" partion that it will overwrite the whole disk. So, I need to start with the windows already installed and figure out how to install ubuntu in a seperate partition over the network.

I am not a beginner but I am in this area. Any suggestions would be appreciated. Thanks.
Starting with Windows already installed is the recommended way to do a dual-boot system.  Linux will recognize that Windows is installed and add it to GRUB (GRand Unified Bootloader).  This allows you to chose which OS you want to boot.

As for installing from the Internet, some distros have an ISO that is specifically for this purpose.  I know that SuSE is one of them.  I did an Internet install.  At the time, I didn't have a high-speed connection, so it was a bit slow.

I did a Google search and couldn't actually find any myself.  However, this is what is required for you to accomplish what you want to do.

---

