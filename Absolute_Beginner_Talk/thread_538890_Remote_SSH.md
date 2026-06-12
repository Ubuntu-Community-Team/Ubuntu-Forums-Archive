---
title: "Remote SSH"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-30
Hi there,

I need my girlfriend to be able to SSH into my PC from her res....

She is using a 3G mobile connection and I am connected to a Netgear ADSL router? There is plenty to read on the web about setting up routers and stuff, but I just need someone to take me by the hand for the first baby steps... where to start!?

How would you about setting up a remote ssh system?


Thanks very much!

Rudolf

EDIT: I have been using ssh for a while now, but not outside of my home network.
         She is running XP, can she do this using puTTY?

---

### Post by llamakc on 2007-08-30
sudo apt-get install openssh-server

Open a port on your router so that port 22 points to your box.

Give her your IP.

Yes. Putty works fine.

---

### Post by beercz on 2007-08-30
> **llamakc said:**
> sudo apt-get install openssh-server

Open a port on your router so that port 22 points to your box.

Give her your IP.

Yes. Putty works fine.
Once you have set this up you could use winSCP (on the windows pc) to copy files to and from your linux box.

[http://www.winscp.com/](http://www.winscp.com/)

---

### Post by dwhitney67 on 2007-08-30
> **beercz said:**
> Once you have set this up you could use winSCP (on the windows pc) to copy files to and from your linux box.

[http://www.winscp.com/](http://www.winscp.com/)
But not if it is a dual-boot system.  I think you meant any workstation, including one running Windows, can run a secure-copy app or secure-shell app to connect to the Linux machine (when the Linux machine is currently running).

---

### Post by banditti on 2007-08-30
probably worth looking into dynamic dns for ease of use.

---

### Post by RudolfMDLT on 2007-08-31
Thanks guys! I'll give it a shot this weekend!

---

### Post by Dr Small on 2007-08-31
> **llamakc said:**
> sudo apt-get install openssh-server

Open a port on your router so that port 22 points to your box.

Give her your IP.

Yes. Putty works fine.
Having said that, make sure you open port 22 on your box too, otherwise you still won't be able to connect to the ssh server.

Dr Small

---

