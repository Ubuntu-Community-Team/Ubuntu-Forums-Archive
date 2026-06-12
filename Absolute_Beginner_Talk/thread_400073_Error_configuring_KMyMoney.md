---
title: "Error configuring KMyMoney"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-04-03
Hi

I'm trying to upgrade KMyMoney2-0.8.4 to KMyMoney2-0.8.6 which is the latest stable release. It doesn't come via the synaptic manager and therefore I'm trying to install it via the terminal.
I'm new to Ubuntu, a few weeks, and when I try to do this, at the ./configure part of the installation, I get an error as follows:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I'm not sure what X is and really what it is trying to tell me, apart from it can't find it.
Can anyone guide me as to what is required?

Many thanks in anticipation.

Gazza

---

### Post by Al_maverick on 2007-04-24
> **gazzadtfan said:**
> Hi

I'm trying to upgrade KMyMoney2-0.8.4 to KMyMoney2-0.8.6 which is the latest stable release. It doesn't come via the synaptic manager and therefore I'm trying to install it via the terminal.
I'm new to Ubuntu, a few weeks, and when I try to do this, at the ./configure part of the installation, I get an error as follows:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I'm not sure what X is and really what it is trying to tell me, apart from it can't find it.
Can anyone guide me as to what is required?

Many thanks in anticipation.

Gazza

To compile Kmymoney, you have to have the development packages of KDE and Qt.


Can you post the exact error message and what you typed in configure?

---

