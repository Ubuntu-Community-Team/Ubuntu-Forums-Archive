---
title: "Opera installation problem (Feisty Fawn)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by keithrennie on 2007-07-24
I'm new to Ubuntu (like it lots).  Opera is my mailer and browser of choice, but I cant get it to install.  I downloaded from the web the 9.22 .deb installation file version 20070716.6 and the error message I get when I try to install is "Dependency not satisfied - Libqt3-mt".  

I cant see this filename anywhere.   I'm using Feisty Fawn.   I looked through previous posts and couldnt find anything directly relevant. 

What should I do? Any advice gratefully appreciated.

---

### Post by Mornedhel on 2007-07-24
Opera is available through the Medibuntu repositories. The Medibuntu website ([http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)) has the instructions to enable their repository, from there you can just sudo apt-get install opera . It (Medibuntu) has some other interesting stuff (codecs and the like).

---

### Post by deadgobby on 2007-07-24
Please install Opera in Synaptic. It should be in there and solve your depends issue. You all so can install it in the terminal as well. 
sudo aptitude install opera

Gobby

---

