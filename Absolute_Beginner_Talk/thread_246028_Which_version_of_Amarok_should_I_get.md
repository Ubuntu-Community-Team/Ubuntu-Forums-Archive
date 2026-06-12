---
title: "Which version of Amarok should I get?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by nushawn on 2006-08-28
There is no Ubuntu option, I'm such a noob.

---

### Post by orb9220 on 2006-08-28
synaptic has version 1.3.9 if you enable additional reposorties.
But to get the latest. Open a terminal and copy and paste each line into terminal.

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s
apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

