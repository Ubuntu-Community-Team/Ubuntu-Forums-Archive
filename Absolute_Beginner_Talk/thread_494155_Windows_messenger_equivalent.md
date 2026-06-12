---
title: "Windows messenger equivalent"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-07-06
Suddenly, a colleague is having real troubles connect with his Skype software and is no longer able to chat on line. Until he is able to resolve this matter,  I'm wondered can he use Windows messenger or similar and at the same time, me use a linux equivalent program?  If this is possible, what might i use on my Ubuntu machine when he is on an XP computer?

---

### Post by r4ik on 2007-07-06
aMSN and Gaim are options they should be in synaptic.

Good luck.

---

### Post by twiceasworn on 2007-07-06
I would suggest Gaim, but only because it is the only one I have used.  Good solid IM program that you can use for multiple IM accounts (AIM, ICQ, MSN etc).

---

### Post by jamesey on 2007-07-06
i like Kopete

---

### Post by insane_alien on 2007-07-06
kopete or gaim. both are good. if your on a gnome desktop go with gaim, a kde desktop then kopete as they are installed by default. you can use either one on either enviroment though, if you do you will need to download a bunch of libraries as well. synaptic handles that though.

---

### Post by lbelloq on 2007-07-06
aMSN if you need webcam support, Pidgin or Kopete for everything else.

---

### Post by njknight on 2007-07-06
My favorite is kopete, but the only thing I can't get to work (yet) is the built-in webcam on my Acer, and that's not the fault of the kopete program.

---

### Post by a.v.l on 2007-07-06
> **lbelloq said:**
> aMSN if you need webcam support, Pidgin or Kopete for everything else.

Having installed aMSN already I find that when I try to sign in I get a message telling me I don't have TLS installed on the computer and then recommends a website to download it from. When I go to that website, ( [http://tls.net](http://tls.net)) I cannot find it there to download. 

Before I resort to the other software suggested by members, perhaps some ideas about where else I can find TLS would help, I've looked in synaptic, but no joy?

---

### Post by a.v.l on 2007-07-06
> **insane_alien said:**
> kopete or gaim. both are good. if your on a gnome desktop go with gaim, a kde desktop then kopete as they are installed by default. you can use either one on either enviroment though, if you do you will need to download a bunch of libraries as well. synaptic handles that though.

Gaim is installed according to Synaptic, but I can't locate it.  How do I find it please?

---

### Post by hardyn on 2007-07-06
does pidgin allow for point to point file xfer yet?

---

### Post by quinnten83 on 2007-07-06
> **a.v.l said:**
> Having installed aMSN already I find that when I try to sign in I get a message telling me I don't have TLS installed on the computer and then recommends a website to download it from. When I go to that website, ( [http://tls.net](http://tls.net)) I cannot find it there to download. 

Before I resort to the other software suggested by members, perhaps some ideas about where else I can find TLS would help, I've looked in synaptic, but no joy?

The TLS package needs to be renamed, here is a howto which worked for me.
[http://www.amsn-project.net/wiki/TLS]("http://www.amsn-project.net/wiki/TLS")

---

### Post by kukibird1 on 2007-07-14
> **a.v.l said:**
> Having installed aMSN already I find that when I try to sign in I get a message telling me I don't have TLS installed on the computer and then recommends a website to download it from. When I go to that website, ( [http://tls.net](http://tls.net)) I cannot find it there to download. 

Before I resort to the other software suggested by members, perhaps some ideas about where else I can find TLS would help, I've looked in synaptic, but no joy?


Open a terminal  and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50

Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 

Restart Amsn

All l versions of Amsn have TLS  installation issues  from within the program . The Sourceforge mirror it uses is faulty.

---

