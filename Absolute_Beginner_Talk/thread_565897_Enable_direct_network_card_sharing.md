---
title: "Enable direct network card sharing?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-10-02
Hi all.  I've bought a new PC and dual installed Ubuntu with windows XP.  I bought a crossover cable, so I could connect my old PC to my new one, to transfer all my old media.

I enabled sharing in the old PC and the XP installation on the new one.

Works fine, I can see my old PC's drives.

Is it possible to see the old PC's drives in Ubuntu?  I need to transfer the files to my Ubuntu install, the XP is too small (and I'm trying to make the switch completely to Ubuntu)

Thanks to any all who respond!

---

### Post by Pumalite on 2007-10-02
sudo apt-get install openssh-server, or
sudo apt-get install openssh-client

---

### Post by waste301 on 2007-10-02
Thanks!  I'll try that now, and post how it goes.

---

### Post by Pumalite on 2007-10-02
Let us know.

---

### Post by waste301 on 2007-10-02
OK, I ran the command and it seemed to install fine.  It asked for the ubuntu CD and got what it needed.

However when I unplug my internet connection and plug in the patch cable to the old PC  the network icon changes to read:

 Please contact your system administrator to resolve the following problem:

Could not find information on interface 'eth0:avahi' in /proc/net/dev

I only have one netwok card in each machine, which is why I'm switching back and forth. I tried rebooting with the patch cable plugged in. Should I be seeing new drives available to be mounted, or do I need to buy a new network card to do this?

---

### Post by waste301 on 2007-10-02
Bumpity

---

### Post by Pumalite on 2007-10-02
The best thing is to have a small home LAN with a router providing DHCP to both computers. And you need two cards.

---

### Post by waste301 on 2007-10-02
I'm a single guy living in an apartment, I really don't need a network.  I just want to get my old music off the old PC and onto the new one.  What I need to know is:

If you've got 2 pc's hooked together with a network cable, how do you  look at the other pc's drives?  There is no network icon I can click in ubuntu.  How do I access the other file system?  Is there a utility I'm supposed to use?

---

### Post by waste301 on 2007-10-03
Good Morning. Bump.

---

