---
title: "Super user"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by Goffy on 2005-10-12
I have a problem that I don't quite understand.

I have installed several programs through the synaptic package manager with no problems. It asks for my password and works perfectly.

Now I have a software that I need to install manually over the terminal. Sp I open the window and type in SU for super user. Terminal asks for my password, but decline to log me in for some reason. Are there more than one root password or am I doing something completely wrong?

---

### Post by Pablo_Escobar on 2005-10-12
Ubuntu uses "sudo" insted of "su", so type "sudo make install" :)

---

### Post by kzutter on 2005-10-12
I hate typing sudo, so I usually open the "root terminal".

You can also *sudo su*

-Ken

---

### Post by Goffy on 2005-10-12
OK. Got it so far..

Now to another problem:

I am installing Yahoo messenger and have used the following command:  

 sudo dpkg -i ymessenger_1.0.4_1_i386.deb

Everything seems to start ok, but then the process terminates and I get this message:

Pakker ut ymessenger (fra ymessenger_1.0.4_1_i386.deb) ...
dpkg: Kravproblem hindrer oppsettet av ymessenger:
 ymessenger krever libssl0.9.6. Men:
  Pakken libssl0.9.6 er ikke installert.
dpkg: Feil ved behandling av ymessenger (--install):
 kravproblem - setter ikke opp pakken
Det oppsto feil ved behandling av:
 ymessenger

I am being told that I need to have libssl0.9.6 installed. I tried to look for it in synaptic, but its not there.
Where do I find that file, and how do I install it?

I really love ubuntu and the entire concept of Linux, but I must admit that the learning curve sometimes seems a little steep and software installations and starting some programs still give me a lot of headache. :???:

---

