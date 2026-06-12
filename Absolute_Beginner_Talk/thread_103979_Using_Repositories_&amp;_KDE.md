---
title: "Using Repositories &amp; KDE"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by oldguy on 2005-12-15
Very new. Have Ubuntu Breezy Badger up and running (with much help). Can access internet, but am vulnerable.

1. How to determine what version of a program to download from a depository? I want Firecracker as a firewall, but there are so many choices. If it matters, my PC is AMD and not Intel.

2. Once I know which to choose, how do I download? The reason I ask is that downloading Ubuntu in the first place, I got a file that wouldn't work. It was not an ISO image. 

3. Will downloads automatically install?

4. Can I now add KDE? I've read that Gnome is very limiting and I would like all available options.

As you can see, I'm totally confused about what I'm doing beyond using what is in Ubuntu "out of the box".

Any help would be appreciated.

---

### Post by manicka on 2005-12-15
To install what you want you could choose to install the 'Firstarter' and 'kubuntu-desktop' packages in Synaptic or just run this command from a terminal.

sudo apt-get firestarter kubuntu-desktop

All the dependencies will be handled for you by synaptic/apt.

Once installed log out and click on the 'Session' button and choose to start a kde session.

enjoy!

---

### Post by oldguy on 2005-12-15
Thanx...

Told you I'm new. I assume "sudo apt-get" is "synaptic/apt"?

---

### Post by Gossie on 2005-12-15
No, Synaptic is the graphical program you can use, but you can also install manually by typing commands in the terminal (>Applications >System Tools >Terminal).

- 'sudo' means 'superuser do', then you can work as root user
- some commands you can only work with, if you give the root password
- these commands you have to use together with the command 'sudo'
- apt-get is a command that uses the sources.list. In the sources.list are the servers where your ubuntu finds packages. You can edit the sources list. 
- here's a nice site for newbies: [https://wiki.ubuntu.com//UbuntuHowCome](https://wiki.ubuntu.com//UbuntuHowCome)

good day, Gossie (Amsterdam)

---

### Post by oldguy on 2005-12-15
Thanx much. Will be back I'm sure.

---

### Post by Gossie on 2005-12-15
Me too!

---

